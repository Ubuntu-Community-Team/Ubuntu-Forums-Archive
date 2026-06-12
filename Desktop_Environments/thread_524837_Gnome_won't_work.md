---
title: "Gnome won't work"
date: 2007-08-13
forum: Desktop Environments
---

### Post by Trunk_z on 2007-08-13
Hey there.

Originaly I posted this in the Installation forum, but thought it would be better suited here.


My problem is that when i start Ubuntu (after a clean install) and log in, nothing happens.
Well.. the Gnome loading screen comes up, disepears, the background changes sligtly, but then nothing happens.

I can only use the "Failsafe Terminal" option via the "select session" button.

I have re-installed Gnome and all of its components.


What i see when I boot & login:
[[IMG]http://img79.imageshack.us/img79/7756/13082007047fm1.th.jpg[/IMG]](http://img79.imageshack.us/my.php?image=13082007047fm1.jpg)

What I can use:
[[IMG]http://img79.imageshack.us/img79/5438/13082007048za7.th.jpg[/IMG]](http://img79.imageshack.us/my.php?image=13082007048za7.jpg)

What I get when I run "startx" (well, after removing a locked file or something):
[[IMG]http://img461.imageshack.us/img461/9366/13082007049pg0.th.jpg[/IMG]](http://img461.imageshack.us/my.php?image=13082007049pg0.jpg)


Sorry for the pics, thought they may be useful.

Can anyone please help me with this? I've tried installing graphic drivers and stuff.

Laptop's spec:
P4 2.8GHz
512MB Ram
128MB ATI Radeon Mobility IGP (shared memory with ram)
I'm using the external monitor output, as the screen is broken if that helps?

Thanks,
Chris

---

### Post by merlinus on 2007-08-13
You will need to install the correct drivers for your video card.

In the meantime, try this at a CLI:

```

sudo dpkg-reconfigure xserver-xorg

```You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

or reboot.

-merlin

---

### Post by Trunk_z on 2007-08-13
Hey, thanks for the quick reply

CLI = command line interface?
(sorry, kinda a noob)

I managed to install the ATI drivers as per the instructions on their website, I think i did at least.. is there a way to check?

Anyways, I ran through that command, rebooted, typed in my user name and password and again its just a blank orange screen with a mouse cursor in the middle. I think its taunting me..

---

### Post by merlinus on 2007-08-13
Yes, for CLI.

Did you select vesa for your video driver?  Does that work?

Once up-and-running, you can reinstall the ATI driver.

-merlin

---

### Post by Trunk_z on 2007-08-13
Cool.

Yeahyeah, selected Vesa as the driver.

The Gnome loading screen came up, the background changed to a different shade of orange. Then things stopped happening

---

### Post by merlinus on 2007-08-13
I wonder if it has something to do with the monitor.

Can you select Recovery mode at the grub prompt and see what happens?

-merlin

---

### Post by GuidoCalvano on 2007-08-13
NOTE THAT I AM NO EXPERT!! PLEASE WAIT TO TRY THIS 

The orange screen after the ubuntu loading splash is exactly what I had earlier today. I had no installation problems though, my orange screen was caused by shutting down improperly. I didn't have any driver problems and install went seemlessly. If you have the orange screen maybe you can access the failsafe gnome as well?

In that case this is what I did to fix it (wait untill someone who knows what he/shes doing responds);

I removed the following directories from my home folder .gnome and .gnome2 (BY MOVING THEM INTO A FOLDER I MADE AS A BACKUP) then I logged in normally which resulted in a working desktop. 
These folders are hidden, so when you do this using nautilus (places->home folder) from the failsafe dont forget to check "view->show hidden" files to true. Otherwise you won't see the two folders ;).

Logging in after this gnome recreated these directories with proper settings.

Note that this would have to have caused the loss of some gnome related settings!!!

I followed advise of another user on the forum (slightly differently so I am not quoting or basing myself on experience just a lucking try loosly based on what he said). He/she said that creating a new user and logging in as this user would verify if removing the .gnome folder would solve the problem. It didn't, I removed .gnome2 and then it did work.

I haven't checked every app I installed yet. But everything seems ok.

Any of you experts out there can confirm this is safe to try in this case?

---

### Post by Trunk_z on 2007-08-13
I dont know how to get into the GRUB thing like you suggested, merlinus. Any help on this please?

GuidoCalvano, thanks for the tip, but unfortunatly it doesnt work either.


The gnome startup screen has some music, but it sounds like it "cuts-off" 1/2 way through. At the bottom is says Nautilus, and has 3 icons on the left.

I tried the Live CD again, and that does work fine. Which to me is very odd if it works there, but not when its installed.

Anything else I can try?

Thanks so far,
Chris

---

### Post by GuidoCalvano on 2007-08-13
Don't forget to put things back!!

---

### Post by Trunk_z on 2007-08-13
> **GuidoCalvano said:**
> Don't forget to put things back!!

Already done =] Thanks for the reminder though

---

### Post by ajgreeny on 2007-08-13
You can try copying the /etc/X11/xorg.conf file from the live CD when it's running and pasting it to the install when that is in cli mode.  Copy it to a usb disk or something similar and go from there.  You will need to know the mount point of your usb disk when running your installed system, so plug it in and then in the terminal type:-
dir /media
This will tell you what folders are in /media and there will be one related to your usb disk, perhaps sda1 or the usb manufacturer name or something similar, so cd to that folder and do "ls" in terminal, which should show the xorg.conf file.  Now, once you have found it type :-
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
and hit return.  Then
cp xorg.conf /etc/X11/xorg.conf

This will put the file you know works into your installed system, so should work there.  Now you can try installing the proprietary ati driver if you really want, but be warned it can be a real problem with some ati cards and you may be better with the OS ati driver.

---

### Post by se7en on 2007-08-13
I had a similar problem with my laptop twice. In the terminal I typed ```
sudo apt-get install gnome 
```and it installed Gnome like it was never installed in the first place! I still haven't been able to figure out why it did that

---

### Post by Trunk_z on 2007-08-13
> **se7en said:**
> I had a similar problem with my laptop twice. In the terminal I typed ```
sudo apt-get install gnome 
```and it installed Gnome like it was never installed in the first place! I still haven't been able to figure out why it did that


Already tried that, and yes, it did seem like a lot of files were missing. Or at least... a lot more got installed. Thanks anyway though.

AJGreeny, I'm trying your suggestion as we speak, so keep your fingers crossed... i have been all day

---

### Post by Trunk_z on 2007-08-13
> **ajgreeny said:**
> You can try copying the /etc/X11/xorg.conf file from the live CD when it's running and pasting it to the install when that is in cli mode.  Copy it to a usb disk or something similar and go from there.  You will need to know the mount point of your usb disk when running your installed system, so plug it in and then in the terminal type:-
dir /media
This will tell you what folders are in /media and there will be one related to your usb disk, perhaps sda1 or the usb manufacturer name or something similar, so cd to that folder and do "ls" in terminal, which should show the xorg.conf file.  Now, once you have found it type :-
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
and hit return.  Then
cp xorg.conf /etc/X11/xorg.conf

This will put the file you know works into your installed system, so should work there.  Now you can try installing the proprietary ati driver if you really want, but be warned it can be a real problem with some ati cards and you may be better with the OS ati driver.


Unfortunatly this didnt work for me either. Is there a log file or anything that I could read to try to identify the problem?

It did exactly the same this time btw. Gnome loading screen, 3 icons, plays part of the intro music but stops dead

Also, I kinda need to go to bed, but I'll try new ideas and reply when I get up.

Thanks for all your help so far guys
Chris

---

### Post by Trunk_z on 2007-08-13
forgot to mention, KDE works fine... im just more familiar with gnome, so much prefer using it

---

### Post by yogo on 2007-08-13
I switched to XFCE4 as I had the same problems with Gnome, it definately beats the hell out of Gnome hanging after login.

---

### Post by Trunk_z on 2007-08-14
> **yogo said:**
> I switched to XFCE4 as I had the same problems with Gnome, it definately beats the hell out of Gnome hanging after login.


Yep, have just done that. Gave up on Gnome so switched to XUbuntu, which uses XFCE4 =]

Thanks guys,
Chris

---

