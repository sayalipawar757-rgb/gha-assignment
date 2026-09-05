q1 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q1-release-notes.yml

q2 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q2-matrix-build.yml

q3 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q3-fix.yml

explaination :
The workflow wasn't starting because the file was in the wrong .github folder. 
I also used an invalid runner name. The checkout step was after the hello script, so the script didn't exist when GitHub tried to run it. 
Finally, the checkout action needed a version such as @v4. After fixing these four things,
the workflow should appear in Actions and the hello script can run correctly.

q4 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q4-fix-me.yml

explaination : 
The first bug is that the environment input is free text, so it should be changed to a dropdown with only staging and production. 
The second bug is that the job condition allows the job to run only for production, which causes staging to be skipped, so that condition should be removed. 
The third bug is that the production deployment message should only be displayed when production is selected, so the check should be placed inside the step. 
The fourth bug is that $APP_NAME == "demo-app" uses shell syntax inside a GitHub Actions if, so it should use ${{ env.APP_NAME == 'demo-app' }}.
Finally, the notification condition can skip when a previous step is skipped, so ${{ !cancelled() }} should be used instead.

q5 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q5-fix-me.yml

explaination : 
There are three bugs here. First, the consume job does not have needs: generate, so both jobs can start at the same time;
adding needs: generate makes sure the output is created before it is used. Second, the Make version step does not have an id, 
but the job output refers to steps.make.outputs.version; adding id: make allows GitHub Actions to access that step’s output. Third, 
::set-output is deprecated, so the version should be written to $GITHUB_OUTPUT instead, such as echo "version=1.0.${GITHUB_RUN_NUMBER}" >> "$GITHUB_OUTPUT".


q6 : https://github.com/sayalipawar757-rgb/gha-assignment/blob/main/.github/workflows/q6-reusable.yml
   

