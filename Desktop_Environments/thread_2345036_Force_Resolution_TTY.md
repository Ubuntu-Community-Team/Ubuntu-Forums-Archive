---
title: "Force Resolution TTY"
date: 2016-11-30
forum: Desktop Environments
---

### Post by giobaxx on 2016-11-30
ood morning guys


I need your help because of my lack of experience. We have a laptop with 4K monitor on which we have just installed in dual boot ubuntu 14.04 and Windows. The problem is that the resolution at which UBUNTU start is too high(3480x2160) and Basically is impossible to work with the TTY.

I've configured the Desktop Environment at lower resolution, basically 1920x1080 and also the terminal is goo enough. I fixed the resolution for the GRUB menu adding this line:
**GRUB_GFXMODE=1024x768 **in this file  **/etc/default/grub**

But the splash screen and the TTY1-6 are even in 4K Resolution, For the Spash screen is a relative problem you have only to write you password, even if i would like to fix to lower resolution, but the problem is the is impossibile to work with TTY for their high Resolution..so the character are so small....


Looking on google there is a possible solution by adding also **GRUB_GFXPAYLOD_LINUX=1980X1080 **or **GRUB_GFXPAYLOAD_LINUX=keep** in the same file, i tried also many value but apparently nothing has changed.

Do you have any idea how to solve?

---

### Post by sudodus on 2016-11-30
[url=http://ubuntuforums.org/showthread.php?t=2319718&p=13466678#post13466678]
How to change default font size in console mode[/url]


1. There is a set of custom fonts for your console.
You must first download them with this command:

```
sudo apt-get install fonts-ubuntu-font-family-console
```

2. Next, you will use a text editor to create a script. I simply used gedit.
You must create the file as root / administrator - so enter the command:

```
sudo gedit /usr/local/bin/fontset
```

Once the new empty file is open in gedit, you need to specify the font that
you want to use as your console default. Now you can see a list of all the
available fonts by visiting the directory

```
/usr/share/consolefonts/
```

. There are in total 302 available fonts, so you may want to test a few
until you find one that you like. You should adjust the code below to reflect
the font that you want to use. This is the larger font that I selected.
Enter this code into the new empty file /usr/local/bin/fontset using gedit:

```
#!/bin/sh
setfont /usr/share/consolefonts/Uni3-TerminusBold32x16.psf.gz
```

To clarify once more, Uni3-TerminusBold32x16.psf.gz is the font that I choose
to use. There are 301 others in the font directory that you downloaded &
installed earlier! So you set the path to the exact name of the font you want
to use. Once done, save the file with the changes and exit gedit.

3. You must next edit your

```
.profile
```

which is a hidden file located in your home directory. I simply used gedit
again to do this. As .profile is your file, you have permissions to change
it and there is no need to type sudo first. So enter:

```
gedit .profile
```

This will open up your .profile file. There will be lines of entries in this
file that you should not change. Just scroll down to the bottom and add these
lines to your .profile:

```
if [ "$TERM" == "linux" ]; then
/usr/local/bin/fontset
fi
```

Save the file with the changes and exit gedit.

4. Next, you need to change the permissions of the script that you created
earlier. Because it was created as root using sudo, you should enter the
following command:

```
sudo chmod 777 /usr/local/bin/fontset

```
Finally, reboot your system.

Once you restart, you can log onto anyone of the 6 consoles pressing the keys:

[B][I]ctrl-alt-F1
[/I][/B]
or ***... F2-F6***

At first the console text at the prompt is the tiny default. Enter your
username and password at the prompt and your new customised font will be
displayed.

---

### Post by giobaxx on 2016-11-30
Tanks A lot.....at list we can work with a new font, now after i login in the system is possible to read what i write in the TTY.

 even if i'm just curious if is possible to configure TTY and splash screen resolution without tricks......

..I can configure at system level? or i have to configure for each user?  

is it Possible to change the default bash with an other Software more enhanced and configurable?

---

### Post by sudodus on 2016-11-30
Well, not without tricks, but there might be other and better tricks ;-)

---

### Post by giobaxx on 2016-11-30
Tanks a lot!!!! .....can you tell me if it possible to add this configuration to all user?

---

### Post by yetimon_64 on 2016-11-30
> **sudodus said:**
> Well, not without tricks, but there might be other and better tricks ;-)

> We have a laptop with 4K monitor on which we have just installed in dual boot ubuntu **14.04** and Windows. 

@ sudodus, I just read the link in your first post that states from 15.10 on "sudo dpkg-reconfigure console-setup" no longer works, but if the OP is using 14.04 it stiil should work fine for increasing the font size.

Through a very complex (non-standard) "tty only" boot set up on 16.04 on either upstart or systemd, I actually have still got the use of the older "dpkg-reconfigure console-setup" method working. I had to alter 6 /etc/init files for upstart and add 6 override files in /etc/systemd/system for the ttys to work (I use autologin with the mingetty package). Then had to point the default.target to the multi.user.target and NOT the graphical.target etc. Once it is all set up I boot straight to a tty in either systemd or upstart boot options and can start the GUI in either. 

After reading your link stating the dpkg-reconfigure command no longer works I tested it here and it worked fine and even held after a reboot (in the standard "systemd" boot option); most probably as a result of the heavy system modifications I have done to get a tty only boot with manual startup of lightdm.

@OP, have you tried the "sudo dpkg-reconfigure console-setup" command yet ? That may work ok to increase the tty console font size if you are on 14.04.

---

### Post by sudodus on 2016-11-30
Thanks, *yetimon_64*, for the heads up regarding the release - that the original poster is using 14.04, where it might work with an easier method :-)

---

