---
title: "Text Login to GNOME &amp; KDE"
date: 2009-12-21
forum: Desktop Environments
---

### Post by CodeTBone on 2009-12-21
Hey guys,

Im running Karmic and I have GNOME and I just finished installing KDE.

First, when I installed KDE my bootup/shutdown progress bar and logo are all Kubuntu now, not the issue at hand but in all curiosity, why? (But if you do have a fix to get me back to the regular Ubuntu one im all ears.)

Once I select Ubuntu in GRUB on bootup I'd like to see a text login as opposed to the Ubuntu/Kubuntu GUI login.  Why you may ask?  For some reason geeky looking command lines attract me.

I read that in order to disable X from starting automatically I needed to run this command:
```

sudo update-rc.d -f gdm remove
```So I did and rebooted but still came to Kubuntu login, so I ran again replacing gdm with kdm, and again still seeing Kubuntu login screen.

Ultimately I want to bootup, select Ubuntu, enter my user/pass, enter startx, and either see the GUI login or even better if I could run startx with an option like "startx kmd".

Whatever anyone's got will be met with a million thanks!

---

### Post by lewisforlife on 2009-12-21
To get a text login, add the word "text" (without quotes) to the end of your Kernel in your boot loader.  You can also get rid of the word "splash" and this will show you what is happening when Ubuntu is loading instead of the splash screen with the progress bar.

Here is how you do this with grub, I am not sure how to accomplish this if you are running grub2 as I don't have it yet.

```

sudo gedit /boot/grub/menu.lst   # add text, remove splash
sudo update-grub

```

---

### Post by CodeTBone on 2009-12-21
Thanks man, that sounds like it would work, now I just got find out to do it in grub2.

---

### Post by CodeTBone on 2009-12-22
Bump.

---

### Post by lewisforlife on 2009-12-22
From doing some research on Grub2, it looks like you are going to want to update /boot/grub/grub.cfg, and then run the sudo update-grub command, check out these links for detailed information:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

---

### Post by CodeTBone on 2009-12-22
I just got done, works just like I planned.
Now is there a way to set an MOTD once I get to the CLI?

---

### Post by CodeTBone on 2009-12-31
New question, how can I get my GNOME login back, instead of the KDE one?

---

### Post by benerivo on 2009-12-31
What's 'MOTD'?

To switch between kdm and gdm, you can install any other display manager, eg...```
sudo apt-get install xdm
```and the installation process should offer you an option for what you want to have as default. You could also try```
sudo dpkg-reconfigure gdm
```.

---

### Post by CodeTBone on 2010-01-01
'Message of the Day'...as a like if your reading this walk away now.
 
Thanks man

---

