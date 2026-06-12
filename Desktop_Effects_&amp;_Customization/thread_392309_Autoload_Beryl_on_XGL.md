---
title: "Autoload Beryl on XGL"
date: 2007-03-24
forum: Desktop Effects &amp; Customization
---

### Post by aashay on 2007-03-24
I just got Beryl 0.20 installed and simply love the performance.. Just one thing though; Is there any way to autorun the "beryl-manager" everytime i select a XGL session during login. From what i understand startup programs in System>>Preferences>>Sessions are independent of session. I want to prevent beryl from running in the non-xgl session

---

### Post by Waappu on 2007-03-24
Hi

I found this guide

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Adding_Beryl_to_Session_Startup](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Adding_Beryl_to_Session_Startup)


> To start beryl-manager only when the session "xgl" is started, I modified a script from Gentoo Wiki scripts.so: 


Create the script: Use your favourite text editor to create a script start_beryl.sh. I placed and created it in /usr/local/bin/ so: 

$ sudo gedit /usr/local/bin/start_beryl.sh
In the file paste this: 

#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi
and save the file. 

Making the script executable: Now make sure the script has the right permissions settings set so that it can be invoked by session login entry - this can be done in Nautilus or Konqueror or simply by typing the following into a terminal: 

$ sudo chmod a+x /usr/local/bin/start_beryl.sh
Add the script to gnome session startup: 

Go to System ? Preferences ? Sessions 
Go to the 'Startup Programs' tab 
Click the 'Add' button and type /usr/local/bin/start_beryl.sh into the dialog box 
Click 'Close' 
Now, you can logout and start a session. When you start a gnome session, the script looks if XGL is started, and so, if you are in a xgl-session, it launches beryl-manager. 

---

