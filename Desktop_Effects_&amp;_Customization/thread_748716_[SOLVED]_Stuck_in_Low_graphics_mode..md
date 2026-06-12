---
title: "[SOLVED] Stuck in Low graphics mode."
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by j3rownjjvjjagik on 2008-04-07
Hey guys, I'm super new at this whole linux/ubuntu thing...and I've come across my first problem that has me completely stumped.

I'm running an asus motherboard, pentium 3 (3.2 ghz), ati aiw 9550, 1 gb ram.

I installed ubuntu two days ago, and it was working fine until last night.  At that point, I tried installing XGL/compiz.  After using this [tutorial]("http://www.tectonic.co.za/wordpress/?p=1153"), I rebooted my computer.

Now my computer is stuck in this stupid loop.  First, it boots up with its resolution at 600x800.  Then, it proceeds to tell me im running in low-graphics mode.  At that point, I used the "change manually" option and entered the correct graphics card and monitor (ATI AIW 9550, and some generic 17" flatpanel that i got at costco).  Then I login to my account...and after from anywhere between 2 and 10 seconds, the screen flashes black and then goes back to the login screen with the same error message.

I tried doing some xconfigure or something (i read it in some forum), and it looked for a second like it was going to work...and then it didnt.  I tried opening in failsafe...same stuff happened.

Can someone help me get back to things the way they were please?

---

### Post by overdrank on 2008-04-07
> **j3rownjjvjjagik said:**
> Hey guys, I'm super new at this whole linux/ubuntu thing...and I've come across my first problem that has me completely stumped.

I'm running an asus motherboard, pentium 3 (3.2 ghz), ati aiw 9550, 1 gb ram.

I installed ubuntu two days ago, and it was working fine until last night.  At that point, I tried installing XGL/compiz.  After using this [tutorial]("http://www.tectonic.co.za/wordpress/?p=1153"), I rebooted my computer.

Now my computer is stuck in this stupid loop.  First, it boots up with its resolution at 600x800.  Then, it proceeds to tell me im running in low-graphics mode.  At that point, I used the "change manually" option and entered the correct graphics card and monitor (ATI AIW 9550, and some generic 17" flatpanel that i got at costco).  Then I login to my account...and after from anywhere between 2 and 10 seconds, the screen flashes black and then goes back to the login screen with the same error message.

I tried doing some xconfigure or something (i read it in some forum), and it looked for a second like it was going to work...and then it didnt.  I tried opening in failsafe...same stuff happened.

Can someone help me get back to things the way they were please?

Hi and welcome, do you realize that "how to" was for dapper 6.06. and you are using Gusty 7.10. Did you edit your sources list like the "how to " directed. If  you reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it still reboots?

---

### Post by j3rownjjvjjagik on 2008-04-07
yeah, the resolution went back to normal for about 3 seconds, and then the error messages ensued once more.

i know the file i edited, it was etc/gdm/gdmconf-custom...i just added the lines at the end it told me to add.  would changing it back to the way it used to be (i still have the ubuntu cd) bring things back to normalcy? if so, how would I do that?

---

### Post by overdrank on 2008-04-07
> **j3rownjjvjjagik said:**
> yeah, the resolution went back to normal for about 3 seconds, and then the error messages ensued once more.

i know the file i edited, it was etc/gdm/gdmconf-custom...i just added the lines at the end it told me to add.  would changing it back to the way it used to be (i still have the ubuntu cd) bring things back to normalcy? if so, how would I do that?

Hi and the "how to" states to backup 
The following files should be backed up before continuing any further:
- /etc/gdm/gdm.conf-custom (if present)
- /etc/kde3/kdm/kdmrc (if present)
- /etc/apt/sources.list
Then if you did back up yours then you can restore them.

---

### Post by j3rownjjvjjagik on 2008-04-08
I didn't back up my files (stupid me)...is my only solution at this point reinstalling?

---

### Post by Pap3r on 2008-04-08
7.10 comes with Compiz Fusion installed already, it's only necessary for a person to install CCSM (Compiz config settings manager).

---

### Post by warp99 on 2008-04-08
> **j3rownjjvjjagik said:**
> I didn't back up my files (stupid me)...is my only solution at this point reinstalling?

No, you can fix this without a problem. The only time you need to reinstall is for a catastrophic failure, this isn't Windows you know. Linux is a module operating system and at the most you just need to reinstall certain components.

First what tutorial did you use to install to xgl/compiz? The reason I ask is that most of the guides are deprecated. Second what files did you change in /etc/gdm directory? We may need to reverse some damage. Very easy, no big deal.

---

### Post by Pap3r on 2008-04-08
He used [This tutorial](http://www.tectonic.co.za/wordpress/?p=1153)

---

### Post by warp99 on 2008-04-08
> **Pap3r said:**
> He used [This tutorial](http://www.tectonic.co.za/wordpress/?p=1153)

Well that guide is definitely deprecated since his card will run Compiz with the open drivers no modifications at all. If he can post back here with what files he changed we can just remove those files and do a reinstall of the packages, No problem.

---

### Post by j3rownjjvjjagik on 2008-04-08
the file i changed was called gdmconf-custom and it was in etc/gdm.

---

### Post by warp99 on 2008-04-08
Go ahead and boot to a login screen, but don't login, then press alt-crtl-F2 to get a console. Login to the console and remove this item from your sources.list:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

so enter the following:
```
sudo nano /etc/apt/sources.list
```
if nano is not installed then
```
sudo apt-get install nano
```
edit the file, save (ctrl-o), exit (crtl-x), then:
```
sudo apt-get update
```
make sure the update runs to remove the previous repositories then:
```
sudo apt-get -d install --reinstall gdm
```
this will only download gdm to our archive, make sure the operation completes correctly before moving to the next step
```
sudo apt-get remove --purge gdm
```
when the package is being removed go ahead and stop xserver as the prompts says, then:
```
sudo apt-get install gdm
```
Now we have the new gdm installed with a new configuration, next we need to get rid of xgl and the associated files:
```
sudo apt-get remove --purge xserver-xgl compiz compiz-plugins compiz-core compiz-manager csm cgwd cgwd-themes
```
then install the following:
```
 sudo apt-get install --reinstall compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig0
```
and finally enter:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
choose the driver 'ati' and when you get to monitor resolution choose the resolution you want to run and any resolution **ABOVE** that resolution should be removed. Once that is done issue the following:
```
sudo reboot
```

Now Compiz graphics should run with the open driver and your card, however if Compiz is not working we can install the proprietary drivers if needed.

Edit:
If you did not install any packages from [http://xgl.compiz.info](http://xgl.compiz.info) you can skip that step of removing the packages.

---

### Post by j3rownjjvjjagik on 2008-04-08
Ah, thanks so much, that worked!

---

