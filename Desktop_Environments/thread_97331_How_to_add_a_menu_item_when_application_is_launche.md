---
title: "How to add a menu item when application is launched from a script"
date: 2005-11-30
forum: Desktop Environments
---

### Post by jonathanjo on 2005-11-30
I have a (java) application that is launched from a script, actual example which launches IntelliJ IDE is:

[INDENT][FONT="Lucida Console"]/opt/idea/bin/idea.sh[/FONT][/INDENT]

My Question is, how can I add this to the applications menu. I've tried using the application menu editor and i can get the icon to click, but when i do click nothing happens. 

In the "Command:" entry i've tried "/opt/idea/bin/idea.sh", i've tried "exec ...." etc. I've tried checking "Run in terminal" 

No joy. Any help is greatly appreciated.

Apologies if this is already answered, i've tried a few searches and so far failed to answer my question.

---

### Post by art on 2005-11-30
Well, first of all you need to know how to run that applocation. When you run it from command line, do you type /opt/idea/bin/idea.sh and it runs? what is the output of 

ls -l /opt/idea/bin/idea.sh
.

---

### Post by jonathanjo on 2005-12-01
yes, to launch i type
[INDENT]
/opt/idea/bin/idea.sh[/INDENT]
and the application runs no problem (the script sets environment variables and then launches a java program)
out put of ls -l /opt/idea/idea.sh is
[INDENT]-rwxr-xr-x  1 jonathan jonathan 1851 2005-11-03 02:05 /opt/idea/bin/idea.sh[/INDENT]

It would be useful to know how to make this work, also as a way to easily launch other scripts. For example scripts to run and stop the tomcat jsp server.

---

### Post by RAOF on 2005-12-01
Does the first line of idea.sh look like this?
```
#!/bin/sh
```
If not, try adding that line to the top.

---

### Post by jonathanjo on 2005-12-01
Yes it does.

Has anyone actually created a Gnome menu item that launches an application from a shell script? 

I've tried other scripts for other applications with no luck. 
(The were all probably java applications)

Have attached the script for this example in case that hepls

---

### Post by FLeiXiuS on 2005-12-02
Aboslutely this is relatively easy if you think about it.

Simply create an executable for this script.

```

$ sudo gedit /usr/bin/ideascript

```
Inside gedit you can enter the following.
```

#!/bin/sh
/opt/idea/bin/idea.sh

```
Then SAVE and EXIT.  Basically your creating an executable file to run this script for you.  Quite easy eh?

Whats left now is make sure the file is executable.
```

$ sudo chmod +x /usr/bin/ideascript

```

Inside the Application Launcher you may set the command to execute the program to be "ideascript".  Give that a shot.

---

### Post by aysiu on 2005-12-02
[QUOTE=jonathanjo]
Has anyone actually created a Gnome menu item that launches an application from a shell script?[/QUOTE] Yes. A kind soul on these forums helped me write a script for emptying the trash. I put it in /usr/bin, and I added an item that launches emptying the trash with the command ```
emptytrash.sh
``` **Edit**: Actually, I use it as custom keyboard shortcut, but I just tested it as an application menu entry, and it works just fine.

---

### Post by Cruxic on 2006-12-10
I got very frustrated with a similar problem.  It turns out that there was an error in the script so that when it was launched it would almost immediately terminate (thus giving zero feedback about the problem).

Given my experiences here is the procedure I would recommend to add a menu launcher for a script:
**Overview steps**:
[LIST=1]
[*]Mark the script as executable
[*]Make sure the script works when executed from any directory
[*]Add a menu entry using the full path to the script file
[/LIST]
**Detailed steps**
[LIST=1]
[*]Mark the script as executable
[*]Open a terminal.
[*]cd into a directory other than the one your script resides in (~/Desktop for instance).
[*]Type in the fully qualified path to the script (eg /home/cruxic/programs/pyNeighborhood-0.3/pyNeighborhood.sh)
[*] Hit enter.  Did the script execute successfully?  If so we have established that it works no matter where it is executed from.
[*]Now try add a menu entry with Alacarte (System->Preferences->Menu Layout)
[*] In the *Command* field for the entry put in the fully qualified path to the script.
[/LIST]
**Notes:**
[LIST]
[*]It is not necessary to put the script on your PATH from my experience.
[*]This should work for scripts that start with #!/bin/sh as well as #!/bin/bash
[*]It is not necessary to to check the "*Run command in terminal*" option.  It should work either way.
[*]If you "*Browse*" to the script file I noticed that it will escape certain characters in the file path.  This did not cause any problems for me.
[/LIST]

Hope this helps.

---

