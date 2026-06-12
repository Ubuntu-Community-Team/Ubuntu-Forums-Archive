---
title: "No resolution in Ubuntu for my screen?"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by swskeptic on 2008-04-14
Hello there, this is my first post here and today was my first day ever using Ubuntu. I used it for just a few minutes and it got me really excited, but I have one problem, no proper screen resolution.

I've gone and tried to configure it but it only gives me 4 choices:

1280x1024
1024x768
800x600
640x480

None of which go with my resolution which is 1280x720.

I'm using a Gateway FPD1775W TFT 17" Widescreen LCD. I have a NVIDIA GeForce 6150 SE Graphics card.

I'm pretty sure there is a solution to this somewhere but I am VERY new to Linux and have never used it before. A lot of the language used is like me trying to read Chinese or something, it's crazy. I'm not a computer novice or anything, it's just I've never had to do REALLY advaced kinds of things. I really would like to give Linux a fair shot though as I am coming over from Vista.

I hope someone here can help me out.

Also, a last bit of info is that I'm trying Ubuntu out first, I haven't fully installed it. I'm launching it from a CD so just in case I decide not to keep it I won't lose all my files/programs/ect.

---

### Post by LinuxGuy1234 on 2008-04-14
> **swskeptic said:**
> Hello there, this is my first post here and today was my first day ever using Ubuntu. I used it for just a few minutes and it got me really excited, but I have one problem, no proper screen resolution.

I've gone and tried to configure it but it only gives me 4 choices:

1280x1024
1024x768
800x600
640x480

None of which go with my resolution which is 1280x720.

I'm using a Gateway FPD1775W TFT 17" Widescreen LCD. I have a NVIDIA GeForce 6150 SE Graphics card.

I'm pretty sure there is a solution to this somewhere but I am VERY new to Linux and have never used it before. A lot of the language used is like me trying to read Chinese or something, it's crazy. I'm not a computer novice or anything, it's just I've never had to do REALLY advaced kinds of things. I really would like to give Linux a fair shot though as I am coming over from Vista.

I hope someone here can help me out.

Also, a last bit of info is that I'm trying Ubuntu out first, I haven't fully installed it. I'm launching it from a CD so just in case I decide not to keep it I won't lose all my files/programs/ect.

The closer resolution is  1024x768. Choose that.

---

### Post by swskeptic on 2008-04-14
I tried that resolution and it's close, but it's still a little stretched out lenghtwise and I don't want that.

---

### Post by tedt on 2008-04-14
1st you might want to try this command in the terminal

sudo dpkg-reconfigure -phigh xserver-xorg

then restart the X server ctl-alt-backspace

The other issue could be that you haven't installed it

---

### Post by swskeptic on 2008-04-14
> **tedt said:**
> 1st you might want to try this command in the terminal

sudo dpkg-reconfigure -phigh xserver-xorg

then restart the X server ctl-alt-backspace

The other issue could be that you haven't installed it

Yeah see, I understood the last sentence and "ctl-alt-backspace". Mostly because I've had to use "ctl-alt-delete" so often in windows lol.

sooo, could you explain to to me please?

---

### Post by tedt on 2008-04-14
Ok in Ubuntu 

press alt + F2

in the dialog box enter

gnome-terminal


at the command line (the flashing cursor thingy) enter

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by paul101 on 2008-04-14
> **swskeptic said:**
> 
sooo, could you explain to to me please?


go to Applications > Accessories > Terminal and copy and paste the code (ctrl + shift + v to copy into terminal :) )

---

### Post by swskeptic on 2008-04-14
Thanks tedt and paul101, I got it thanks to you. It's at 1280x700 or something like that. It's not perfect, but close enough.

Thanks again for the help. I'll give Ubuntu a run for a week, if I like it, I'll stick with it, if not, it was worth a try.

---

### Post by Zorael on 2008-04-15
There is a solution, before you give up, but it's a bit complicated.

You want to open the **/etc/X11/xorg.conf** file with superuser permissions. But before that, you'll want to make a backup. Open a terminal and enter this. It will ask for your password.
```
$ sudo cp /etx/X11/xorg.conf /etc/X11/xorg.conf.08-04-15
```

Then enter the following.
```
$ gksu gedit /etx/X11/xorg.conf
```

I'm not sure how your xorg.conf looks, but somewhere close to the end you will see a Screen section that corresponds to your videocard and your monitor. It should mention resolutions, default depth, etc. You don't want to mess with the device names, though, or you might end up in failsafe mode upon starting.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Videocard"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth      24
        Modes      **"1280x720"** "1024x768" "800x600"
    EndSubSection
EndSection
```

There may be a plethora of options and settings listed there; this is just a barebone example. If there are resolutions mentioned, just add your wanted resolution there. To make it default to it, remove any higher ones (like, 1600x1200, 1280x1024, etc). You shouldn't need to reboot the whole system to see the changes; just restart your graphical environment with Ctrl+Alt+Backspace. Save unsaved work first.

---

### Post by t52wa_r0x on 2008-06-17
Using a new Benq T52WA (15-inch wide) monitor.
Tried the standard procedure, which was to edit "xorg.conf" in the way that Zorael has demonstrated above.
Nearest I could go was 1280x768.

Got it working by manually changing to 1280x720 by using the "xrandr" command while X is running.
**The following is copy-and-pasted from somewhere else:**

This worked for me:


Generate desired modeline using the "gtf" command:
"gtf 1280 720 60"
Copy and paste the resulting modeline into "Monitor" section of "/etc/X11/xorg.conf". You could give it a reasonable name like "1280x720_60". (You can name it anything you like.)

Under the "Screen" section, under the subsection "Display", there is a line as follows:
**Modes "XXxXX" "XXxXX" "XXxXX"** (and so on)
You should enter the name of your new modeline (e.g. "1280x720_60") in here.
By right, we would like to put it as the first mode, but that's not necessary (since it won't work automatically, anyway).

Now start the xserver with "startx".
Yes -- the modeline is not working yet.
Don't worry, open a term and do:
"xrandr --output VGA --mode 1280x720_60"

If it works, your screen will switch to the new mode.
Congrats!
If you want to apply "1280x720_60" on every X startup,
please insert the following as the 1st line of "~/.xinitrc":
**xrandr --output VGA --mode 1280x720_60**

---

