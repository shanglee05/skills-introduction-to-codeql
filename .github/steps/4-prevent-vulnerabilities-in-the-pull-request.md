## Step 4: Prevent Vulnerabilities in the Pull Request

The last step is to try pull request integration with CodeQL. In this step, we will add a vulnerability back into the `routes.py` file to trigger an alert for a SQL injection vulnerability. This is going to be the same issue we initially saw.

Our goal is to understand what developers experience when they find a new vulnerability.

In this step, we will:

- edit the `routes.py` file.
- change the SQL statement to make it insecure.
- commit those changes and merge the insecure code into the main branch.
- experience the alert inside the pull request.

**What is pull request**: Pull requests are proposed changes to a repository submitted by a user and accepted or rejected by a repository's collaborators. This allows multiple people to work on the same code at the same time. For more information, check out the GitHub Skills exercise "[Introduction to GitHub](https://github.com/skills/introduction-to-github)" or "[About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)" from the GitHub docs.

**What is branch**: A branch is a parallel version of your repository. By default, your repository has one branch named main and it is considered to be the definitive branch. Creating additional branches allows you to copy the main branch of your repository and safely make any changes without disrupting the main project. For more information, see "[About branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#)" in the GitHub docs.

### ⌨️ Activity: Edit `routes.py` and create a new pull request

In this first activity, we'll introduce the same insecure SQL statement from before to the `routes.py` file. Once we update the file, we'll commit it to a new branch, then create a pull request.

1. Click the **Code** tab in your repository.

1. Select the `server` folder.

1. Select the `routes.py` file.

1. Click the **Edit** button to the right.

   <img width="400" alt="edit button" src="https://github.com/user-attachments/assets/19462cc5-a360-4dae-a97b-ecfd571aa403"/>

1. Edit line 16 by highlighting the SQL statement and replace it with this text.

   ```py
   "SELECT * FROM books WHERE name LIKE '%" + name + "%'"
   ```

1. Click **Commit changes...** from the top right. The "Propose changes" window will pop up.

1. This time, select the radio button next to **Create a new branch**. You can create a new name for this branch or leave it as the default suggestion.

1. Click **Propose changes**. This opens a new pull request.

1. In the "Open a pull request" window, click **Create pull request**.

### ⌨️ Activity: Review pull request

At this point, we've edited the file `routes.py` to add our vulnerable code, committed those changes to our new branch, and created a pull request to merge the new branch into our `main` branch. These are the same steps a developer would take to introduce new, vulnerable code into a repository.

Now, let's take a look at the pull request to see what the experience is like.

1. In the previous activity, we created the pull request. After creating the pull request, you were brought directly to the pull request page. At the bottom of the pull request, you will see a check called "Code scanning/CodeQL". This is the CodeQL analysis job scanning the code introduced in the pull request.

   <img width="400" alt="pr panel" src="https://github.com/user-attachments/assets/1c29ee0f-cc1d-4568-9e71-338d45ad1d54"/>

1. Once the check is complete, you will see a new comment in the pull request from CodeQL indicating a new security vulnerability; a SQL query built from user-controlled data. This is our SQL injection vulnerability.

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/677cc104-9116-44a9-8061-091e8126442a">

1. Review the data flow paths by clicking **Show paths**.

1. If you would like, add a comment and tag one of your friends by using their GitHub handle (example: `@username`). This will notify them that you made a comment on the issue and need their help solving the problem. 😄

   If this were a real-world situation, the developer would fix the SQL statement in their branch. Once fixed, the vulnerability will automatically close out.

   If you would like to learn more about pull request integrations for code scanning, see "[Triage code scanning alerts in pull requests](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/triaging-code-scanning-alerts-in-pull-requests)."

1. With the pull request started, Mona will check your progress and share a final review. Nice work! You are done! 🥳
