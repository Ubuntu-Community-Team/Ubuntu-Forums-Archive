---
title: "ssh problem"
date: 2007-06-07
forum: Education &amp; Science
---

### Post by elfstone214 on 2007-06-07
This problem is driving me insane. I have been breaking my head for a couple of hours and can't figure it out.

I am trying to run a script on a server remotely with ssh using the below command with no success 

ssh [email]user@server.edu[/email] sh foldername/myscript.sh

and the script is:
>>>>>>>>>>>>>>>>
unset DISPLAY
matlab > matlab.out 2>&1 << EOF
matlabfile
print file
exit
EOF
>>>>>>>>>>>>>>>>
here I am making matlab run a matlab script called "matlabfile"
But the script somehow does not run. 

I know for a fact that the way I am calling the script through ssh is right and I am pointing in the right location of the script. However the fact that is in a folder which is not my main user directory causes it to not be able to run through ssh. I can run it fine through ssh if the script is in the main user directory but not if it is in a folder within the main directory. 

I can also confirm that if I connect to the server and cd into the folder and run it from there (sh myscript.sh), it also runs just fine.

This is driving me crazy.

Can anyone help?
Thanks!

---

### Post by Mr. C. on 2007-06-07
You'll get better results to your questions if you post in forums more appropriate to your questions (eg. networking instead of Education and Science).

First, what exactly is the error message / error code ?

When you run you script over ssh, the shell's working directory will be "user"'s home directory.  I presume foldername is the same as /home/user/foldername (or equivalent).  So you are telling the remote shell to run the command myscript.sh by a relative pathname (foldername/myscript.sh).  However, your script is assuming that the file matlabfile is either in user's home directory, or that matlab knows where to find it by name.

What directory is your matlabfile located in?

Add the code to the beginning of your script:

```
echo $PATH
pwd
ls -l matlabfile

```

This should make things a little more clear.

Finally, save yourself a little typing.  Add

```
#!/bin/sh
```

as the first line of your script and then:

```

chmod a+x foldername/myscript.sh
```

Then you can just type foldername/myscript without "sh" preceeding, as well as:

```
ssh user@server.edu foldername/myscript.sh
```

MrC

---

### Post by meatpan on 2007-06-07
I'm a bit confused about which dir's you have access to.  In your example, do you have write permission to $HOME/foldername on [email]user@server.edu[/email]?  If not, is it possible to copy the script to a directory that will allow you to write the matlab.out file?

---

### Post by elfstone214 on 2007-06-07
> **Mr. C. said:**
> 
First, what exactly is the error message / error code ?


It doesn't actually return any errors it just doesn't seem to run because there are output files that I am expecting and they do not turn up.

> **Mr. C. said:**
> 
What directory is your matlabfile located in?


my matlabfile is in the same directory as the myscript.sh in user/foldername


P.S. Sorry I posted it here because I thought Networking was more about support for Ubuntu itself.

---

### Post by elfstone214 on 2007-06-07
> **meatpan said:**
> I'm a bit confused about which dir's you have access to.  In your example, do you have write permission to $HOME/foldername on [email]user@server.edu[/email]?  If not, is it possible to copy the script to a directory that will allow you to write the matlab.out file?

I have access to:
/home/user
(and any folders within obviously)

the script I need to run (myscript.sh) is under:
/home/user/foldername

I have an ssh public key under:
/home/user/.ssh


Sorry about the confusion.

---

### Post by Mr. C. on 2007-06-07
Ok, then, there's your problem.

Your script is started with its working directory as your home directory.  Your script's does not indicate where matlab should find the "matlabfile" file.  Matlab is started up with its working directory as your home directory also.  How can it possibly know to look inside foldername to find matlabfile ?

Replace matlabfile with $HOME/foldername/matlabfile

Always use absolute paths, or know how to control your relative paths, when creating scripts.

MrC

---

### Post by elfstone214 on 2007-06-07
```
echo $PATH
pwd
ls -l matlabfile

```

I tried adding this but it didn't work

I appears for some reason it tries to run the script from:
/home/user

when I added that snip of code it pwd returns
/home/user

when it should be
/home/user/foldername

and ls -l matlabfile returned an error because the matlabfile is also not under
/home/user

---

### Post by elfstone214 on 2007-06-07
> **Mr. C. said:**
> Ok, then, there's your problem.

Your script is started with its working directory as your home directory.  Your script's does not indicate where matlab should find the "matlabfile" file.  Matlab is started up with its working directory as your home directory also.  How can it possibly know to look inside foldername to find matlabfile ?

Replace matlabfile with $HOME/foldername/matlabfile

Always use absolute paths, or know how to control your relative paths, when creating scripts.

MrC


Alright, I'm going to give that a try.

---

### Post by Mr. C. on 2007-06-07
Of course it doesn't work.  The ls command should not return /home/user/foldername.  You are misunderstanding working directories and process invocation.

Invoking a program as either:

```
  program
```

or 
```

   directory/program
```

does not change the working directory.  When the program starts, its working directory is exactly the same as the working directory of the process that exec'd it.  In this case, its a shell, started by the ssh server.  And when you run foldername/myscript.sh, the working directory is not changed; rather, the shell just attempts to exec some file named foldername/myscript.sh

Use full pathnames if you don't understand the working directory concept.  If you want to learn more about this, read the section of PATH in Lecture 5 under Coursework at [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/) .

MrC

---

### Post by elfstone214 on 2007-06-07
Got it!

many thanks guys! really appreciate your help.

I dunno what I would do without these forums :D

---

### Post by elfstone214 on 2007-06-07
> **Mr. C. said:**
> Of course it doesn't work.  The ls command should not return /home/user/foldername.  You are misunderstanding working directories and process invocation.


Yeah I understood, I posted that before I saw your later post
Thanks

---

