---
title: "Cannot launch application from menu"
date: 2006-07-27
forum: Desktop Environments
---

### Post by readingboy on 2006-07-27
Hi All,

This one's going to turn out to be silly, I just know it. :)

I'm trying to run IntelliJ IDEA from a menu. Since IDEA doesn't add a gnome menu item, I did so myself manually. I copied the eclipse.desktop item from /usr/share/applications and modified it to suit IDEA. It appeared in the menu hierarchy fine. However, launching it from the menu only causes an item to show up for IDEA in the gnome window list for about 15 seconds. The IDEA splashscreen never appears and the application never launches (nor does it appear in 'ps -A | grep idea' or 'ps -A | grep java'). Weirder, when I type the exact same command I entered into the exec line in the .desktop file, the IDEA splashscreen comes right up and I soon see the IDEA IDE appear. 

I checked permissions on the .desktop file (which are 644, just like every other .desktop file in that directory). I checked to see if there was a .desktop file in ~/.local/share/applications that would take precedence over the .desktop file in /usr/share/applications, but I didn't find one. 

Here's the contents of the .desktop file I created:
[Desktop Entry]
Name=IntelliJ IDEA 5.1.1
Comment=Java Integrated Development Environment
Exec=/usr/local/idea/bin/idea.sh
Icon=/usr/local/idea/bin/idea32.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;Development;
Encoding=UTF-8
StartupNotify=true

IntelliJ IDEA is a java application, so it requires knowing where JDK_HOME is. I've put that information in my .bashrc file. Thinking this might be part of the problem, I created a script that exports JDK_HOME and calls idea.sh. After pointing the desktop file to that script, nothing changed --  the Gnome window list shows IDEA for about 15 seconds, but no new process gets listed in ps -A. 

Running /usr/local/idea/bin/idea.sh from the Gnome deskbar applet does nothing either. Here, I don't even get the entry in the Gnome window list. Yes, I've triple-checked that running /usr/local/idea/bin/idea.sh from gnome-terminal launches the app just fine. 

At this point, I'm at a loss as to how to continue to debug this issue. I don't see a place where any errors from nautilus might get logged. /var/log/messages has nothing to say to me about this. Anyone have any suggestions? I can launch the app by opening gnome-terminal, but this seems really strange and I'd like to figure out what's happening. 

Thanks in advance for any ideas (no pun intended). 

-- Craig

---

### Post by greenstar on 2006-07-27
> **readingboy said:**
> Hi All,
Here's the contents of the .desktop file I created:
[Desktop Entry]
Name=IntelliJ IDEA 5.1.1
Comment=Java Integrated Development Environment
Exec=/usr/local/idea/bin/idea.sh
Icon=/usr/local/idea/bin/idea32.png
[COLOR=Red] Terminal=false[/COLOR]
X-MultipleArgs=false
Type=Application
Categories=Application;Development;
Encoding=UTF-8
StartupNotify=true



Change the line highlighted red to:

Terminal=true

I think this will help. I had the same issue when adding icons to my menu for packages I manually installed.

Greenstar

---

### Post by ardchoille on 2006-07-27
> **readingboy said:**
> 

Here's the contents of the .desktop file I created:
[Desktop Entry]
Name=IntelliJ IDEA 5.1.1
Comment=Java Integrated Development Environment
Exec=[COLOR="Red"]/usr/local/idea/bin/idea.sh[/COLOR]
Icon=/usr/local/idea/bin/idea32.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;Development;
Encoding=UTF-8
StartupNotify=true



Is the highlighted file executable? If not, you'll need to do:

```

sudo chmod u+x /usr/local/idea/bin/idea.sh

```

---

### Post by fouadk on 2006-07-30
i am intrested in running intellij idea on ubuntu but i dunno how to set the JDK_HOME for it since im a newbie, can you help me???

---

### Post by greenstar on 2006-08-01
> **fouadk said:**
> i am intrested in running intellij idea on ubuntu but i dunno how to set the JDK_HOME for it since im a newbie, can you help me???

For starters, start a new thread. Your question is completely unrelated to the subject of this thread. Then I might help.

Greenstar

---

### Post by mikeh123 on 2008-05-06
(in hardy) I'm having exactly the same issue as the original poster, triple checked everything and cannot get IntelliJ to run from a launcher icon, absolutely fine from a command line.  any other ideas ? is there a way to get debug information about what is actually happening when you click on a launcher icon ?

---

### Post by mikeh123 on 2008-05-06
answered my own question, and for those interested, you can get debugging information from a launcher icon if you enter the command:

```
/bin/bash -s "~/apps/idea-7757/bin/idea.sh >> ~/c.out"
```

noticed that i was receiving the error:

```
ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
```

the IDEA_JDK environment variable was not setup, so it could not run.  When running from a terminal, my .bashrc is executed which exports this variable, and thats why it was running correctly.  So, to get the launcher icon to run:

```
/bin/bash -c "export IDEA_JDK=/usr/lib/jvm/java-6-sun && ~/apps/idea-7757/bin/idea.sh"
```

trying to find out how i can set up such environment variables at a 'higher level' if you like, so that other icons launch correctly, without having to specifiy all of my env vars again for each and every application.  seems silly that .bashrc is not run automatically for all commands.

Mike.

---

### Post by GeneralCody on 2008-06-10
Well, putting:

```
export JDK_HOME="/usr/lib/jvm/java-6-sun"
export IDEA_JDK="/usr/lib/jvm/java-6-sun"
```at the end of your ~/.bashrc file, will export the needed variables everytime you log on, or type . .bashrc in a terminal.

This is Bash variables, and not "system wide" variables, that X pick up, so it will not affect the launcher.

Put the two variables in /etc/environment instead, and you should be fine... like this:

JDK_HOME="/usr/lib/jvm/java-6-sun"
IDEA_JDK="/usr/lib/jvm/java-6-sun"

---

