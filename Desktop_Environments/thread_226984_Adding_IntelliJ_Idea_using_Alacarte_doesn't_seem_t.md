---
title: "Adding IntelliJ Idea using Alacarte doesn't seem to work"
date: 2006-08-01
forum: Desktop Environments
---

### Post by sillygit on 2006-08-01
Hi All, 
I'm trying to add a custom entry for IntelliJ Idea using the Alacarte Menu Editor.  After I successfully add the menu idea (Name: IntelliJ Idea, Comment: IntelliJ Idea, Command: /opt/idea/idea-4267/bin/idea.sh) it shows up under applications menu as expected but when I click it nothing happens...

It's not critical as I can run /opt/idea/idea-4267/bin/idea.sh from a terminal but it is a little frustrating (and some what concerning).  Does anyone have any ideas on how I can diagnose whats going on?

Cheers,
Dan

---

### Post by sillygit on 2006-08-03
Actually, I don't seem to be able to get any java programs to launch from the applications menu.

Note: the java programs are wrapped by bash shell scripts...

---

### Post by sillygit on 2006-08-03
Narrowing it down even further.  I can't get any shell scripts to work from the applications menu...

e.g. 
------------------------
#!/bin/sh

touch /tmp/hello
------------------------

Calling the script from the applications menu doesn't create the /tmp/hello file but calling it from a terminal does...

---

### Post by sillygit on 2006-08-03
Also, double-clicking the shell script asks me if I want to run or run in terminal.  Neither of the options actually executes the script...

---

### Post by sillygit on 2006-08-03
The 'Run in terminal' option makes, what looks like, a terminal window open but it closes almost instantly...

---

### Post by keyvez on 2007-02-14
Same here.
Other programs like Eclipse IDE and Netbeans run just fine from the app launcher menu. :confused: 

Is there a program to execute .desktop files, which I can call from terminal, to see what's crashing?

---

### Post by araz_233 on 2008-04-27
you should add variable JDK_HOME in idea.sh

[INDENT]gedit [/path/to/idea]/bin/idea.sh[/INDENT]
[INDENT]add 'export JDK_HOME=[/path/to/jdk]' in first line[/INDENT]
[INDENT]save and exit[/INDENT]

---

