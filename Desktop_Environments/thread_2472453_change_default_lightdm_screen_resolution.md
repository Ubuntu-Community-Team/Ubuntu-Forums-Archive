---
title: "change default lightdm screen resolution"
date: 2022-02-27
forum: Desktop Environments
---

### Post by ccrs8 on 2022-02-27
I have an 8th gen thinkpad carbon x1 with a max screen resolution of 3,840 x 2,160 that I just installed Xubuntu 20.04 LTS on.  I have regular human eyes so I changed the resolution to 1920 x 1080 in my main xfce session, but I can not for the life of me figure out how to change the default lightdm screen to the same resolution.  If I'm already logged in and lock my session, the lightdm screen is exactly as I want it, but if I'm logged out or just booting up, the resolution is 3,840 x 2,160.  It's not a big deal since there's only one user on the machine and the screen just needs to accept a password and then I'm done with it, but it is curious that there is no setting for it in the lightdm settings gui in xfce.  I've googled the issue and there seem to be several .conf edits I could make in various etc or var folders, but when I attempted one heavily upvoted solution I found that I didn't even have the file/folder the solution suggested.  Any suggestions for getting the default resolution changed?  Increasing the font size makes things a bit more tolerable, but not as great as if the resolution was changed.

---

### Post by him610 on 2022-02-27
Don't know about changing the resolution of lightdm, but my distribution is Xubuntu 20.04.4.
When using Xfce, from the whisker menu, Settings->Display, Resolution (choose your resolution), Apply, Close.

Added:
This may, or may not work for you...
Find the line in /etc/default/grub that reads "#GRUB_GFXMODE=640x480"
Change it to read "GRUB_GFXMODE=1920x1080"
Save the file
Run 'update-grub' to update /boot/grub/grub.cfg
Reboot your machine.
Assess the results.

---

### Post by ccrs8 on 2022-02-28
> **him610 said:**
> Don't know about changing the resolution of lightdm, but my distribution is Xubuntu 20.04.4.
When using Xfce, from the whisker menu, Settings->Display, Resolution (choose your resolution), Apply, Close.

I did that for my general xfce session once I'm logged in, but unless I'm already logged in and just unlocking my existing session, the lightdm login screen defaults to 3,840 x 2,160 regardless of what I have set in that settings screen.

---

### Post by &amp;KyT$0P# on 2022-02-28
First you will need to find a [FONT=Courier New]xrandr[/FONT] command that sets the resolution you want (I've used xrandr for this exact purpose before, but not often enough nor recently enough to know any further details at the moment, sorry).  Put the command as a script file -
```
#!/bin/bash
[COLOR="#FF0000"]insert your xrandr command here[/COLOR]
```
Save it wherever you want, make sure root has execute permission on this file.

Then create a .conf file in [FONT=Courier New]/etc/lightdm/lightdm.conf.d/[/FONT] (create this directory if it does not exist) and fill it with this -
```
[Seat:*]
display-setup-script=[COLOR="#FF0000"]/full/path/to/your/script[/COLOR]
```
Replace [COLOR="#FF0000"]/full/path/to/your/script[/COLOR] with the actual absolute path to your script.

---

### Post by ccrs8 on 2022-03-04
> **halogen2 said:**
> First you will need to find a [FONT=Courier New]xrandr[/FONT] command that sets the resolution you want (I've used xrandr for this exact purpose before, but not often enough nor recently enough to know any further details at the moment, sorry).  Put the command as a script file -
```
#!/bin/bash
[COLOR="#FF0000"]insert your xrandr command here[/COLOR]
```
Save it wherever you want, make sure root has execute permission on this file.

Then create a .conf file in [FONT=Courier New]/etc/lightdm/lightdm.conf.d/[/FONT] (create this directory if it does not exist) and fill it with this -
```
[Seat:*]
display-setup-script=[COLOR="#FF0000"]/full/path/to/your/script[/COLOR]
```
Replace [COLOR="#FF0000"]/full/path/to/your/script[/COLOR] with the actual absolute path to your script.

Perfect, thank you so much!  This site gave me everything I needed to know about xrandr:
[https://linuxconfig.org/how-to-configure-your-monitors-with-xrandr-in-linux](https://linuxconfig.org/how-to-configure-your-monitors-with-xrandr-in-linux)
and then your instructions worked like a charm.

---

### Post by jakemaverick911 on 2022-10-11
> **him610 said:**
> Don't know about changing the resolution of lightdm, but my distribution is Xubuntu 20.04.4.
When using Xfce, from the whisker menu, Settings->Display, Resolution (choose your resolution), Apply, Close.

Added:
This may, or may not work for you...
Find the line in /etc/default/grub that reads "#GRUB_GFXMODE=640x480"
Change it to read "GRUB_GFXMODE=1920x1080"
Save the file
Run 'update-grub' to update /boot/grub/grub.cfg
Reboot your machine.
Assess the results.

I'm having a similar problem here, need to increase my resolution to 1920x1080...and i thought your suggestion might work! New installation here. Trouble is, I can't save the file? It opened in mousepad....

---

### Post by ajgreeny on 2022-10-11
> **jakemaverick911 said:**
> I'm having a similar problem here, need to increase my resolution to 1920x1080...and i thought your suggestion might work! New installation here. Trouble is, I can't save the file? It opened in mousepad....
You have to use root permissions to save that file, possibly easiest done using ```
sudo -H mousepad
``` to open the application with root permissions, write it as shown, and then save the completed file to the **/etc/lightdm/lightdm.conf.d/** folder as shown in halogen2's post above.

---

### Post by jakemaverick911 on 2022-10-11
Thank you! that let me do it, but i still can't switch resolution, not sure what I'm doing wrong :-( I'll look again with less tired eyes is probably best I think. Found out it does let me change it under 'Settings Editor' as well, but no way to save it....

---

