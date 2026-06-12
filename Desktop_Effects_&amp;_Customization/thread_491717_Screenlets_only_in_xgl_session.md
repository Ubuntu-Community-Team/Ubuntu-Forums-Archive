---
title: "Screenlets only in xgl session?"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-07-03
screenlets look good with xgl running, horrible without it. I want to set it to start on startup, but only for my xgl session. I thought i'd try to modify my startxgl.sh, and added "screenlets-tray" to the end, but that didn't work. 

I'm not to keen on shell scripts - how do i modify startxgl.sh so it launches the command "screenlets-tray", or is there another way to have it start only in my xgl session?

---

### Post by AdamG51172 on 2007-07-04
Thanks for asking the question, cause I just taught myself all of this.  I originally was just going to point you to something and suggest you change it, but I wanted to know what I was telling you.
I use a script for Beryl with an ATI card and xgl that doesn't start Beryl unless you are in an xgl session.  This is separate from the startup script itself!!  
Note that I use this for Beryl, so be sure to change Beryl to what _you_ are using this for.
This entailed creating a new script: 
> sudo kate /usr/local/bin/start_beryl.sh Remember to replace 'kate' with 'gedit' if using Ubuntu.
Then adding a fairly simple if-then-else command telling the system not to load beryl unless xgl is running:

> #!/bin/bash
#
# Start beryl-manager within kde-session
#
if [ `ps -A -o comm | grep -c '^Xgl$'` == "1" ]; then 
       DISPLAY=:1 beryl-manager
      DISPLAY=:$1 dbus-launch emerald &
      DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?" fi
the if statement says : ps -A -o comm (using the common name of all processes running ) | grep -c '^Xgl$'` (count the ones with Xgl in the name).  If that count is "1" then run the following: beryl-manager, dbus-launch emerald &, beryl-xgl 
> else echo "${0}: Error: beryl-manager not launched. Xgl not running?" fiOtherwise (else) display (echo) this message: "${0}: Error: beryl-manager not launched. Xgl not running?" 
fi (closes the if-then-else command)

remember to make it executable:
> sudo chmod a+x /usr/local/bin/******.shwhere ****** is the name of your new script

I you can modify this to suit your needs, but it might be a start.  you pretty much would just have to change all of the "beryl" apps with all the apps that you need to run.

---

### Post by superyounan1 on 2007-08-08
awesome, thanks!

---

