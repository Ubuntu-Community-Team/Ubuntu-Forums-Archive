---
title: "How can I reset display settings back to defaults (XFCE)"
date: 2015-07-22
forum: Desktop Environments
---

### Post by dealy663 on 2015-07-22
Hi, 

I'm running XUbuntu 15.04. After spending far too many hours trying to get my settings to work properly with HiDPI on my notebook (Lenovo Y50-70) and a regular 1080p external monitor I've given up on the effort. After setting the notebook display back to 1920x1080 my system continues to misbehave after I thought I had undone all changes I made in the HiDPI effort.

I'd like to just get all of my display settings back to their originals defaults that were defined after the first install. And then run both the notebook and external displays at 1920x1080 (the only stable setting I've seen so far).

Any suggestions (short of re-installing XUbuntu).

Thanks, Derek

---

### Post by Bashing-om on 2015-07-22
dealy663; Hello;;

Keep in mind that 15.04 is systemd :
In 14.04 one can revert to defaults as :
Xfce stores the display information, as defined from the Display configuration applet, in $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml. Deleting that file should restore it to its defaults.

Check that these files exist in 15.04, and maybe the same procedure will be effective ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by dealy663 on 2015-07-22
I had already tried deleting the displays.xml file. It didn't solve the problem.

---

### Post by Bashing-om on 2015-07-22
dealy663; Well, then !

Again check and make sure these files exist in 15.04 as this procedure is ubuntu release 14.04 and xfce4 version 4.10 .

1. Shut down the panel first, xfce4-panel --quit
2. Kill the xfce4 configuration daemon, pkill xfconfd
3. First delete settings for the panel, rm -rf ~/.config/xfce4/panel
4. Clear out the settings for xfconfd, rm -rf ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
5. Restart the panel, run xfce4-panel. This will respawn xfconfd automatically. Note if you need or want to restart xfconfd manually know that on my installation it was in /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd which was outside of $PATH.
This clears it for the running session, regenerates the files, and sets up the default for future sessions.

Mind you once more, I do not know as I am not on 15.04 and not tested.

[INDENT][INDENT]but it could happen
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-07-22
Try logging out, then at login screen use Ctrl+Alt+F1 to go to  TTY command line at which you can login with your username and password, (the password will not show on screen; just type and hit Enter).

At the command line when logged in rename the ~/.config/xfce4 with command ```
mv .config/xfce4 .config/xfce4backup
``` then start a GUI session with command ```
startx
```
Hopefully you will now have a default desktop layout.

---

