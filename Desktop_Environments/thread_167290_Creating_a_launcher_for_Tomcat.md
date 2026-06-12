---
title: "Creating a launcher for Tomcat?"
date: 2006-04-28
forum: Desktop Environments
---

### Post by underthing on 2006-04-28
What I would like to have is a panel launcher for starting up Tomcat. I have Tomcat installed in /home/a_user/tomcat

I can start it by opening a terminal and manually entering:

```
sh /home/a_user/tomcat/bin/startup.sh
```

This works fine. But when I create a launcher with the same command, it doesn't work. What am I missing?

Thanks...

---

### Post by louis_nichols on 2006-04-28
What error are you getting when you execute your launcher?

---

### Post by underthing on 2006-04-28
No error, the terminal window flashes up but then disappears immediately. Tomcat does not start. 

I have "Run in terminal" checked in the launcher properties, but unchecking it doesn't seem to make any difference. When unchecked, the terminal window doesn't appear at all, but still no Tomcat.

---

### Post by louis_nichols on 2006-04-28
Try creating it with the command ```
/home/a_user/tomcat/bin/startup.sh
``` (without **sh**) as the app launcher. It might work.

---

### Post by underthing on 2006-04-28
Thanks for the idea, but no luck. Still unresolved. I've tried all sorts of different combinations of settings in the launcher, but nothing seems to do the job. ](*,) 

Is this even possible? It's not terribly complicated is it: get Ubuntu to run a shell script. Maybe it can't be done?!? 

There must be a way..... :-k

---

### Post by louis_nichols on 2006-04-28
well, then.... sorry, but I'm out of ideas.

to my knowledge, an app launcher should execute any command that can be executed from the command line, be it a binary or a shell script or perl script or whatever. I may be wrong, though.

Try creating the command to direct the output to a file. Perhaps it will spit out some error or smth. Like:

```
/home/a_user/tomcat/bin/startup.sh > ~/error.txt
```

Then see if error.txt says smth.

---

### Post by underthing on 2006-04-28
Thanks for trying, I appreciate your suggestions.

---

### Post by Sef on 2006-05-01
I set it up to launch when I boot up.  

System > Preferences > Sessions > Start up programs  

Then I browse for where it is.  It was under /usr/bin/.

---

### Post by Another Monkey on 2008-03-27
Did anyone figure out how to create a launcher for Tomcat?  It's doing my head in as well.

Any instructions will have to be explicit I am afraid as I am still new at this.

Cheers.

---

### Post by Another Monkey on 2008-03-28
Done it.

I created 2 scripts "gnome_tomcat_start.sh" and "gnome_tomcat_shutdown.sh" in /bin and then pointed launchers at them.  Is this the correct way to do it, or is there a better way?  It seems that Gnome is unaware of any environment variables defined in "~/.bashrc" for some reason.

[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/startup.sh[/FONT]

and
[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/shutdown.sh[/FONT]

---

