---
title: "Gnome-Tweak-Tool will not launch"
date: 2014-04-06
forum: Desktop Environments
---

### Post by zongosaiba on 2014-04-06
Greetings to all, 

I finally got stumped with an issue I cannot seem to solve after using Linux for 1 month. 

gnome-tweak-tool will not launch anymore. 
Errors message:
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
CRITICAL: Could not find schema /usr/local/share/glib-2.0/schemas/org.gnome.shell.gschema.xml
WARNING : Shell not installed or running

I have installed/reinstalled every dependencies that could have cause the issue but to no avail.
I have downgraded Gnome from 3.11.4 to 3.9.90 and was left with a vanilla Ubuntu Gnome but that did not help.
I have recompiled all the schemas: /usr/bin/glib-compile-schemas /usr/share/glib-2.0/schemas &> /dev/null but no go.
I checked that 'org.gnome.shell.gschema.xml' was in '/usr/local/share/glib-2.0/schemas/' and it is.  Don' know why it is complaining then. 

The issue occured right after I installed this new theme: [http://www.noobslab.com/2014/03/trevilla-new-themes-and-icons-in.html](http://www.noobslab.com/2014/03/trevilla-new-themes-and-icons-in.html). Now, I am not saying that this new theme caused the issue but my problem came right after the install of the theme. 

Guys, I am stumped. I have strolled the internet for the better part of the day and could not find a solution to my problem. I found a lot of people with issue similar to mine, but no solution given.  

Any help is of course much appreciated.  Just to make sure that all is clear, I have no issue other than the fact that I cannot open gnome-tweak-tool and change theme, icons etc...

Kind Regards, 

zongo

---

### Post by zongosaiba on 2014-04-06
Small update:
I am posting the solution to this error message:
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
You have to recompile dconf, since the error stems for it. 
1. Download dconf for your distro [http://ftp.acc.umu.se/pub/gnome/sources/dconf/](http://ftp.acc.umu.se/pub/gnome/sources/dconf/)
2. Extract:  "tar -xJvf"
3. Compile: ./configure && make ; sudo make install prefix=/usr
That got rid of the error above. I am down to one

---

### Post by zongosaiba on 2014-04-06
Another update:
I can now change my theme and icons to my content with gsettings command line. I still cannot open up gnome-tweak-tool as the error: "Could not find schema /usr/local/share/glib-2.0/schemas/org.gnome.shell.gschema.xml" persist. I have looked inside 'org.gnome.shell.gschema.xml' and it is empty. That explains the fact that 'gnome-tweak-tool'  is not capable to read it. So the question is how can I recreate it ?

---

