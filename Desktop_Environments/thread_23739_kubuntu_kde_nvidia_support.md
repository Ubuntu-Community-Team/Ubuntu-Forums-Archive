---
title: "kubuntu kde nvidia support"
date: 2005-04-03
forum: Desktop Environments
---

### Post by kristi on 2005-04-03
EDIT : solved.  close thread.

One post said that Nvidia 7167 driver was installed.  How do I get to use it?  Or do I have to go through the kern source install.make,make,etc stuff in a x console.
tia
Kristi

---

### Post by digby on 2005-04-03
It's actually as easy as possible now.  From your console just type each of these two lines:

     $ sudo apt-get install nvidia-glx nvidia-settings
     $ sudo nvidia-glx-config enable

As an optional step. you can disable the nVidia splash screen that shows up when you start X by following the steps [here]("http://ubuntuguide.org/temp/#disablenvidialogo").

edit:  I guess that I should mention that after you run the enabler command, you have to restart X (ctrl+alt+backspace).

---

### Post by kristi on 2005-04-03
Thanks.
I did this and it seemed to work:
 ```
$ sudo apt-get install nvidia-glx nvidia-settings
$ sudo nvidia-glx-config enable
```

I did ctrl+alt+backspace and it seemed to restart X and flashed the Nvidia splash screen at me and then seemed to put me into KDE.

I went ahead and tried the thread to remove the splash and discovered that gedit is apparently not installed.  Fortunately I knew vi so did
cd /etc/X11
sudo vi xorg.conf
i                                  for insert
added the appropriate line (I am used to modifying xorg.conf)
<esc> :wq                 to save it and exit.

I reboot and I am left at a prompt. I log in and type kde but nogo.
Fortunately I know about /etc/inittab so I find it is set to :2:

I set it to 5 and reboot.
It does init 5 but leaves me at a prompt.   I login and this time try kde or kubuntu or &^%$&^%$((

How do I get kubuntu to boot into KDE?
What is the normal setting for inittab?
Does modprobe.preload have to have nvidia added?
tia
Kristi

---

### Post by digby on 2005-04-03
Did you make a backup of xorg.conf?  If so did you try restoring it?  What happens when you run 'startx' at the command prompt?  What about 'kdm'?

You are correct that init:5 is the graphical startup.  I have no idea what would have changed that to 2.

---

### Post by kristi on 2005-04-04
Thanks.
I coppied xorg.conf back on itself since I couldn't remember linux rename command.  I checked it and I did indeed have the orig info there.  I checked inittab and it was still where i had left it: "id:5:initdefault"

I rebooted and it took it's sweet time but did flash the Nvidia white splash at me for a sec or 2 and then light gray blank background screen, and then blue kubuntu background with a message I had gotten before:
```
Kaccess - KDialog
Will not save configuration.
Configuration file "/home/kristi/.kde/share/config/kaccessrc"  not writeable.
Please contact your system administrator.
```

This is of course owned by root root/
when I installed kubuntu,   I created all new partitions (/boot, /, /home ) so it is not a resedue prob.

---

### Post by digby on 2005-04-04
I checked my kaccessrc,  and it is owned by my user, not root.  Chown that to yourself (user and group) and see what happens.

Oh, and the rename command is the same as the move command: mv.

---

### Post by kristi on 2005-04-04
getting mad   8-[   so set up task bar icon to sudo konqueror with execute in root - click on that, it asks for password, and then I can do anything.  Had one of those set up in Xandros, then MDK - handy.

Changed the permissions  - didn't get that message any more.

Menu / system / kynaptic - and updated everything.

No more Nvidia.  

Put Nvidia back on.  rebooted.  fine.

Used my root konqueror to mod xorg.conf and remembered that I had typed Options  with an "s"  bad bad bad   [-X   and that was why I wound up with a 2 in inittab - it reverts if you give it garbage.

Works fine now - many thanks for your patience and help!
Kristi   (I have several more questions (tvtime, firefox, thunderbird) but I'll start a new thread.)

---

### Post by digby on 2005-04-04
Always glad to help with the questions that I can.  Congrats on getting it working.

---

### Post by cwaldbieser on 2005-04-04
Just as a note, it seems that Ubuntu uses runlevel 2 for the graphical display.  This is different from other distros I have worked with (like Mandrake) where runlevel 5 is the norm for the X Server, and 3 was the norm for a console login.

---

### Post by kristi on 2005-04-04
Seems to be true - I set inittab to 2 and rebooted and it came up just fine.

Thanks!
Kristi

---

### Post by Ptero-4 on 2005-04-04
[QUOTE=kristi]Seems to be true - I set inittab to 2 and rebooted and it came up just fine.

Thanks!
Kristi[/QUOTE]
 Actually, Debian (and Debian based) uses runlevel 2-5 as graphical and 1 as single user console. And the runlevel doesn't revert to 2, it's set to 2 by default (and whenever your do a dpkg-reconfigure in anything that deals with the runlevels).
And as for starting X from the console it is done by typing gdm in Ubuntu or kdm in Kubuntu.

Hope it helps.

---

### Post by digby on 2005-04-04
[QUOTE=Ptero-4]Actually, Debian (and Debian based) uses runlevel 2-5 as graphical and 1 as single user console. And the runlevel doesn't revert to 2, it's set to 2 by default (and whenever your do a dpkg-reconfigure in anything that deals with the runlevels).[/QUOTE]

Any idea why they do it this way?  I don't have any need for it, but is there no way to have a multi-user system with only command line access?

---

### Post by Julius on 2005-04-04
[QUOTE=digby]Any idea why they do it this way?  I don't have any need for it, but is there no way to have a multi-user system with only command line access?[/QUOTE]

Can't that be done with control+alt+f1, control+alt+f2... etc?

---

### Post by kristi on 2005-04-04
Actually this thread is dead and done, though I thank all for their comments.

kubuntu appears to be a debian without a repository, or rather without the ease of modifying the repository that ubuntu aparently has.  Apparently damn difficult and no clear instructions.

kubuntu appears to have no easy way to mount, or have mounted other partitions.  I created kubuntu on 3 new partitions, so there's perhaps 8 others that I have need to use/look at while in kubuntu.  This is inexcusable.  This was very easy unter MDK (MCC) and also under Xandros (which does it automatically and for which I have more respect with each new distro I try.)

There is very little support for kubuntu - none for the topics above.

I might take a look at again if it has another major release, but for now, I feel it's a long way from ready.
Thanks to all.
Kristi

---

### Post by suziequzie on 2005-10-03
[QUOTE=digby]It's actually as easy as possible now.  From your console just type each of these two lines:

     $ sudo apt-get install nvidia-glx nvidia-settings
     $ sudo nvidia-glx-config enable

As an optional step. you can disable the nVidia splash screen that shows up when you start X by following the steps [here]("http://ubuntuguide.org/temp/#disablenvidialogo").

edit:  I guess that I should mention that after you run the enabler command, you have to restart X (ctrl+alt+backspace).[/QUOTE]

Thank you, thank you, that was a lifesaver... I can now play Tuxracer without any problem!

I know, it's a little thing, but it makes me happy.\\\\:D/

---

