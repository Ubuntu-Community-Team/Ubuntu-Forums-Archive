---
title: "Help With Ubuntu"
date: 2009-04-12
forum: General Help
---

### Post by Tanner2007 on 2009-04-12
Hello first off im new here and also brand new to Linux/Ubuntu related OS and programs.
Well first off I got the alternate cd, at first I had the live cd and got the error where the video wont display so people on irc gave me link to the alternate cd. I downloaded the 

PC (Intel x86) alternate install CD

But I do have an Athlon 64 bit processor so I am guessing the 

64-bit PC (AMD64) alternate install CD 

Could have worked as well, but I will try that if nothing here gets fixed.

So as off now I have windows vista with a recovery partition and now with the PC (Intel x86) alternate install CD, I have Ubuntu INSTALLED onto different partition and its separate swap partition (So I have 4 partitions On My hard drive 1=windows 2=windows recovery 3=ubuntu 4=swap for ubuntu)

So once I was done installing it I got the same problem as I did with live cd, But the thing with the live cd is I could not get past the install screen before the error showed while with alternate it install successfully but gets it on boot up

Now this is what happens

1)I turn on pc
[http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104657.jpg](http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104657.jpg)
and as you see I select ubuntu

2)Loading
[http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104712.jpg](http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104712.jpg)
As you see its loading fine

3)boot up error
[http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104805.jpg](http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/20090412104805.jpg)
now as you see here it wont display but I hear the bootup sound when its loading the desktop
now as said above with live cd this happen during install while with alternative cd it only happens on start up when, I dont know if I should wipe it out and run the AMD 64 bi alternate cd or is there something else I can do?


right now I have
compaq presario
Sr5130nx

AMD Athlon 64 x2 3800+
NVIDIA GeForce 6150 Se Vid Card
4 gb of ram (installed)
And (Dont know size) but 1024x768 res Dell monitor

---

### Post by Thura on 2009-04-12
We need to more info to help you ... 
Could you give us more detailed description ?

When exactly did the error occur ? More information could help us give better and detailed answer ...

---

### Post by Tanner2007 on 2009-04-12
Sorry sir, re-read the first post I edited it with more info

---

### Post by Bucky Ball on 2009-04-12
Download the 64bit version. Burn disk and boot from it. Run the 'Try Ubuntu' option (after you have run the 'Check CD for defects' option) and make sure that runs okay. If it doesn't, you have a problem with hardware compatibility, probably the monitor. That would give us somwhere to start.

The problem is that it is starting the Gnome desktop environment and crashing. From the grub menu, choose the recovery kernel (second one down) and see if that gives any clues.

---

### Post by Tanner2007 on 2009-04-12
There is no try option, just
install ubuntu
check cd for defects
test memory
boot from first hard drive
rescue a broken system

---

### Post by Tanner2007 on 2009-04-12
I just deleted the partition, bu i downloaded the desktop amd disk and that one lets me try it out before installing, 

and got same problem

Cannot display this video mode but heard the startup sound
anyone got any ideas?

EDIT: it works in Safe Graphics mode
so how could I still get atleast 1024 x 768 res when I re install it and it works since right now it works on safe graphics mode while booting from cd

---

### Post by Thura on 2009-04-12
Ok, now boot again, when you reach to the error ...
try pressing  Ctrl+Alt+"-" ( minus ) ... It is a hotkey for reducing screen resolution ...

If it doesn't work, press "Ctrl+Alt+F1", then you will get to text mode ...
Then login , and run 
```
sudo nano /etc/X11/xorg.conf
```

If it asks for password, enter the password ...

Find the screen section in that text file
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
[COLOR="Red"]        Modes       "1024x768"[/COLOR]
    EndSubSection
EndSection
```

Then in the Modes line, you probably have high setttings, like "1280x960", edit it to "1024x768" ... as I highlighted ... You're done editing. Press CTRL+O to save changes and CTRL+X to quit ...

Now, back at the prompt, run
```
sudo /etc/init.d/gdm restart
```

Then if you are lucky, you can log in now ...
Don't hestitate to post further if you still have problems ...

---

### Post by Tanner2007 on 2009-04-12
> **Thura said:**
> Ok, now boot again, when you reach to the error ...
try pressing  Ctrl+Alt+"-" ( minus ) ... It is a hotkey for reducing screen resolution ...

If it doesn't work, press "Ctrl+Alt+F1", then you will get to text mode ...
Then login , and run 
```
sudo nano /etc/X11/xorg.conf
```

If it asks for password, enter the password ...

Find the screen section in that text file
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
[COLOR="Red"]        Modes       "1024x768"[/COLOR]
    EndSubSection
EndSection
```

Then in the Modes line, you probably have high setttings, like "1280x960", edit it to "1024x768" ... as I highlighted ... You're done editing. Press CTRL+O to save changes and CTRL+X to quit ...

Now, back at the prompt, run
```
sudo /etc/init.d/gdm restart
```

Then if you are lucky, you can log in now ...
Don't hestitate to post further if you still have problems ...
I will try it, but before I do I Deleted the partition, So when I reinstall (which still get same error) Should I use desktop or alternative cd?

PS, My screen is a dell and highest res it supports is 1024 x 768

---

### Post by Thura on 2009-04-12
I think it doesn't really matter which cd you use, since it is going to be the same ...

Since you can boot up with safe mode, you can also try this, 
when you reach grub ( the first screenshot ) choose the first entry and press "e", then find the line like this, ( it may not be the exactly same) 
```
kernel	/boot/vmlinuz-2.6.27-7 ro quiet splash [COLOR="Red"]vga=771[/COLOR]
``` press "e" and append the vga as highlighted, where 771 must be your desired resolution according to the table below ... then press "b" to boot with that settings ...

```

Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  [COLOR="MediumTurquoise"]769      771       773      775[/COLOR]
32000     (15bit)|  [COLOR="MediumTurquoise"]784      787       790      793[/COLOR]
65000     (16bit)|  [COLOR="MediumTurquoise"]785      788       791      794[/COLOR]
16.7 Mill.(24bit)|  [COLOR="MediumTurquoise"]786      789       792      795[/COLOR]

```

---

### Post by hyper_ch on 2009-04-12
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Tanner2007 on 2009-04-12
Thura: I did the 

```
sudo nano /etc/X11/xorg.conf
```

but it was blank (did it twice)

And i reinstalled it with alternative cd and cannot load in safe mode as i did in my ealier post since it was just to run it not install it

either way i also did the 

kernel	/boot/vmlinuz-2.6.27-7 ro quiet splash vga=771

and nothing

---

### Post by Thura on 2009-04-12
> but it was blank (did it twice)
So, it doesn't show the "cannot display this video modes " ? Just black screen ? 

Make sure you added [COLOR="Red"]"1280x768"[/COLOR], (  I mean including the double quotes ) ... Why not try lowerer resolution "800x600" ? ...

Also try regenerating xorg.conf ( which manage your screen resolution, refresh rate .... ) with this command ( in text mode )
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

One more tip, delete "spash" and boot in "kernel /boot/vmlinuz-2.6.27-7 ro quiet vga=771", so that it doesn't use spalash and  boot in text mode which is more informative ...

---

### Post by Tanner2007 on 2009-04-12
> **Thura said:**
> > but it was blank (did it twice)
So, it doesn't show the "cannot display this video modes " ? Just black screen ? 

Make sure you added [COLOR="Red"]"1280x768"[/COLOR], (  I mean including the double quotes ) ... Why not try lowerer resolution "800x600" ? ...

Also try regenerating xorg.conf ( which manage your screen resolution, refresh rate .... ) with this command ( in text mode )
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

One more tip, delete "spash" and boot in "kernel /boot/vmlinuz-2.6.27-7 ro quiet vga=771", so that it doesn't use spalash and  boot in text mode which is more informative ...

After doing the
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the file now shows this

```
http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/09c34551.jpg
```


PS. found something interesting, i found a way around it but not a fix..right now the file is the way it is in that sceenshot,..but if i edit it and add 

depth 24
modes "1024x768"

it loads up but says error..and gives me an option to run in low graphic mode..from there i updated all the drivers...but yet.....it still gives me error so rather i erase what I added and get that error message..or keep it and keep getting another error and selecting low graphic mode where I can access it..

weird, but the res did let me select 1024x768 when it running in low graphic mode which it is the max res my screen supports..

so besides this little loop hole..I still need a fix :(

---

### Post by Bucky Ball on 2009-04-13
What graphics card are you using? If you are tweaking xorg you are probably tweaking the generic open source graphics that come with Ubuntu. I would advise you install Ubuntu and then we fix before trying to do anything. Any changes you make are not going to stick unless you are making them to a hard disk install and you will find yourself chasing shadows.

Once installed, you will be able to download the nvidia or ati drivers and your problem will probably be fixed. Or at least more quickly. There is a good chance that installing envyNG from the repositories would fix any nvidia card problems but that is a waste of time running from the disk. But as I said in the first place, now we know it is a graphics problem. Install to hard drive and focus on getting the right driver. You can find your card by typing in a terminal:

```
lspci
```

Your graphics will be somewhere in the list there.

Your xorg.conf file will probably show nothing because you are not installed. If you were, there would be a section defining your driver; vesa, ati or nvidia (or a custom permutation). Xorg doesn't actually do much anymore ...

---

### Post by Thura on 2009-04-13
According to your graphics card, you need to install nvidia driver ... then run 
```
sudo nvidia-xconfig
```
It will automatically configure xorg.conf to use nvidia ...

---

### Post by Tanner2007 on 2009-04-13
Bucky Ball:

It is installed, and when running that command says,

"00:0d:o VGA Compatible:nVidia Corporation Geforce 150SE nForce 430
rev a2"


Thura:

u sure its my vid card and not my monitor? it seems like my monitor is displaying that message not the system its self, anyways how could I install the drivers onto it if it wont load up? when i did that glitch and got in under safe graphics mode i updated the vid drivers and etc and yet no change,

also i tried the commend anyways and got

"Validation error:data incomplete in file /etc/x11/xorg.conf.
device selection "configured video device" must have a driver line"

---

### Post by soltanis on 2009-04-13
Display problems usually are video cards. They control the monitors, so if you can't interface correctly to them, your video output is going to be messed up.

When your system boots, instead of staring at the Xorg screen, hit Ctrl-Alt-F1 and try

```

sudo apt-get install nvidia-glx-177

```

To try to install the most stable binary nvidia driver.

And please post your xorg.conf file.

---

### Post by Tanner2007 on 2009-04-13
Hey everyone I got it working.. I dont know how, but 

after sudo nvidia-xconfig

I did that glitch and loaded up in safe graphics mode or what ever..

and from there not sure what I did I uninstalled and reinstalled the drivers and did that command again and then forgot what  did I think maybe I edited something, Not Sure either way here.

[http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/d3bc0074.jpg](http://i72.photobucket.com/albums/i172/Tanner2007/TEMP/d3bc0074.jpg)

Any who, how can I backup and save these files before some how they get messed up again

Thanks So Much To Everyone Who helped, Just Need to know how to backup the file before I Mess it up again :P

---

### Post by Bucky Ball on 2009-04-13
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```or whatever you want to call it. That will save a copy (cp) into the same directory you have xorg.conf .. 

Then you can experiment. If you screw up, reverse the command:
```

sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf
```That will overwrite the dodgy one with the backup of the old working one and name it xorg.conf

:)

---

### Post by Tanner2007 on 2009-04-14
Is there a way to save a physical copy of it to the desktop so I can back it up on a jump drive

---

### Post by Bucky Ball on 2009-04-15
It is already accessible from the desktop. You will find at the same address. Open Places->File System->etc->X11 and you will see your xorg.conf file in there. Drop a copy onto your dongle. In other words:

/etc/X11/xorg.conf

 :)

---

### Post by Tanner2007 on 2009-04-16
> **Bucky Ball said:**
> It is already accessible from the desktop. You will find at the same address. Open Places->File System->etc->X11 and you will see your xorg.conf file in there. Drop a copy onto your dongle. In other words:

/etc/X11/xorg.conf

 :)

Thank you, now im starting to get the hang of this

---

### Post by Bucky Ball on 2009-04-18
Pleasure. Good to hear it. Have fun with Ubuntu.

---

