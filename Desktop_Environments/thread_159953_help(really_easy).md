---
title: "help(really easy)"
date: 2006-04-13
forum: Desktop Environments
---

### Post by SledgeHammer_999 on 2006-04-13
I am newbie and I haven't linux  for about a year and I have forgotten the few things I've learned but I know that the solution to my problem is really easy.

I've downloaded the new ati drivers that support my X1800XL graphic card and burned the file on a cd-rw(all this was done in Windows)

Just a while ago I installed ubuntu 5.10 and of course the x-server couldn't start and I am facing the console.

The problem is that I can't remember how to access the cd-rw in order to run the ati installer.

Also I don't how to connect as a superuser nor do I know the password that ubuntu uses in order to do a sudo.

One more do you know if the ati installer needs a graphical interface in order to run?(i ask this because in ATI's installation notes there are screenshots where someone can see that the installer is a graphical wizard)

thanks in advance.

---

### Post by joselin on 2006-04-13
[quote=SledgeHammer_999]
The problem is that I can't remember how to access the cd-rw in order to run the ati installer.[/quote]

The cd will be automounted once you inserted it. You can see the files on /mnt/cdrom.

[quote=SledgeHammer_999] Also I don't how to connect as a superuser nor do I know the password that ubuntu uses in order to do a sudo.[/quote]

To connect as a superuser you must type 'sudo command' with the same password as your user.

[quote=SledgeHammer_999] One more do you know if the ati installer needs a graphical interface in order to run?(i ask this because in ATI's installation notes there are screenshots where someone can see that the installer is a graphical wizard)[/quote]

I can't help on this.

Hope that helps.

Regards.

---

### Post by Sutekh on 2006-04-13
Was the ATI installation wizard on a Windows machine?

You don't need a GUI to install the ATI drivers, try this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

Also if you want something more friendly try

[Easy Ubuntu](http://www.ubuntuforums.org/showthread.php?t=64629)

---

### Post by SledgeHammer_999 on 2006-04-13
@joselin

there seems to be a problem(maybe the cd isn't automounted -REMEMBER that I am facing the console nothing else-). I do a "cd /mnt" and it responds. after that I do a "cd /cdrom" but it says there is no such directory. I'll give some more information(i don't know if this matters) when i login this is what it says before the cursor "sledgehammer@ubuntu~$>". If you give me anymore help plz remember that I am a newbie.

@Sutekh
your respond was semi-relevalt. If you read my post you'll see that I've downloaded the ATI's official LINUX drivers.
> Was the ATI installation wizard on a Windows machine?

I don't think so I read the installation notes for the LINUX version.

---

### Post by Sutekh on 2006-04-13
[QUOTE=SledgeHammer_999]
@Sutekh
your respond was semi-relevalt. If you read my post you'll see that I've downloaded the ATI's official LINUX drivers.[/QUOTE]
I didn't see that in your post.  It wasn't clear that they were for Linux.

Anyway, I see the graphical installer they have.  OK so you need to get X working in some shape or form so you can use the installer.

Backup and edit the X configuration file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
Look for the section entitled
```
Section "Device"
```
Change the line that contains
```
Driver "ati"
```or whatever it may be to```
Driver "vesa"
```
Save the file (Ctrl+O) and exit (Ctrl+X).  Try starting the X server again with
```
sudo /etc/init.d/gdm restart
```

Then if X starts and you get to the default Ubuntu desktop, you can try the ATI installer from a Terminal Window (Applications - > Accessories Menu)
```
sh ./ati-driver-installer-8.24.8-i386.run
```

---

### Post by joselin on 2006-04-14
[quote=SledgeHammer_999]@joselin

there seems to be a problem(maybe the cd isn't automounted -REMEMBER that I am facing the console nothing else-). I do a "cd /mnt" and it responds. after that I do a "cd /cdrom" but it says there is no such directory. I'll give some more information(i don't know if this matters) when i login this is what it says before the cursor "sledgehammer@ubuntu~$>". If you give me anymore help plz remember that I am a newbie.[/quote]

Ok. Let's go... For mount your cd you must know in which device the cd is located. 

```
dmesg | more
```

You must looking for a line like this:
```
[4294675.265000] **hdc**: MATSHITADVD-RAM UJ-820S, ATAPI CD/DVD-ROM drive
```

In bold the device file.

Then you must type the following into a console:

```
sudo mount -t iso9660 /dev/hdc /mnt/cdrom
```

For more info you can type:

```
man mount
```

Regards.

---

### Post by SledgeHammer_999 on 2006-04-14
ok i fixed it thanks.

---

