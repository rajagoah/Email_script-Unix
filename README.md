# Email_script-Unix
UNIX korn shell to send email upon execution
The steps of execution are as follows:

1. Accept command line arguments. The arguments that should be passed are the File being searched for, the path where the success files resides and finally the path where the error file resides. 
2. Since Informatica tirggers this shell upon completion of workflow, the paths are session level parameters. 
  Success file dir -- $PMTargetFileDir
  Error file dir.  -- $PMBadFileDir 
4. Next, there is a word count check to establish if the file exists in the said path or not.
5. if it does, then using the mailx command, an email is fired to the desired audience.

#CONSTRUCTING THE COMMAND LINE ARGUMENT FOR THIS SCRIPT
#sh /global/informatica/102/server/infa_shared/ScriptFiles/Email_script.ksh *BILLING__c*.csv $PMTargetFileDir $PMBadFileDir
#example,
#sh /global/informatica/102/server/infa_shared/ScriptFiles/Email_script.ksh *BILLING__c*.csv /global/informatica/102/server/infa_shared/ScriptFiles/TgtFiles /global/informatica/102/server/infa_shared/ScriptFiles/BadFiles

NOTES on the what the commands used do:
echo $(pwd) --> having a command enclosed in the bracket and preceeding it with $ makes it an executable inside of the echo command.
1) $(echo $FILE_NAME) --> this command will output parametrized file name to the console. 
2) $(ls -t "$LOCATION_SUC"/$(echo $FILE_NAME) | head -n1) --> This command will produce the latest file which matches the file       type being passed through the ls command.
starting from the left:
        a) ls -t "$LOCATION_SUC"/$(echo $FILE_NAME) command will print out the list of files created with the latest file on  top. This is then piped to the head command
        b) head -n1 command will extract the 1st file from the top.


