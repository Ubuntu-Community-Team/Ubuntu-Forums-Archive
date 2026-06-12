---
title: "Auto change Wallpaper"
date: 2009-09-21
forum: Desktop Environments
---

### Post by El Rengo on 2009-09-21
Hello,
I know how to do to change the wallpaper in XFCE but it's work when XFCE start ever I restart o start the machine.

I wont  to configure XFCE to change my Wallpaper of one list, but in one hour, 30 minutes or 10 minutes. It is this possible?

Thanks!!!

---

### Post by rippin on 2009-10-03
Can't take credit for the following as I had to search the Web a **[COLOR=black]while[/COLOR]** to locate and test this method. It works!

1) make an executable file (chmod +x <filename>) with the following lines and save it to your user's /home (I saved it as ~/bin/bg_changer.sh as I keep all my personal special files in my user's bin/)

#!/bin/sh
export DISPLAY=":0.0"
MONITOR=${1:-0}
PROPERTY="/backdrop/screen0/monitor${MONITOR}/image-path"
IMAGE_PATH=`xfconf-query -c xfce4-desktop -p ${PROPERTY}`
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s ""
xfconf-query -c xfce4-desktop -p ${PROPERTY} -s "${IMAGE_PATH}"

2) edit your crontab in a terminal

crontab -e (below is mine with <user> replacing your username)

*/30 * * * *  /home/<user>/bin/bg_changer.sh  > /dev/null 2>&1

HTH,
rippin

---

### Post by tnanek on 2012-03-30
Thanks, this script helps me now, in accomplishing the same thing.

---

### Post by aubreybourke on 2012-05-01
How can I accomplish in with LXDE? I'm running "lubuntu".

I tried installing xfconf, and when I "xfconf-query -l" I dont get the "xfce4-desktop" channel! just a bunch of other stuff like xsettings, displays, xfce4-keyboard-shortcuts, and finally xfce4-power-manager

so then I tried installing the "xfdesktop4" package. And rand "xfdesktop" command. It started up and got a SESSION_MANAGER environment varialbe not defined error. Furthermore, still no xfce4-desktop channel in sight!

am I using the wrong tool completely? 

I had a look at gconf-tool, but that has no entry for the desktop wallpaper either.
I'm guessing, but do I need to add a key in gconf-editor?
Or 
Perhaps there is some way of creating a channel with xfconf? 

Would appreciate some insight pls.

-Aubrey.

---

