---
title: "Changing the mouse polling?"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by Cappy on 2007-03-24
Special Thanks to: Cesare Tirabassi and everyone contributing in this thread

Beginner Tip: You must use sudo when editing these files.
Such as: ```
 gksudo gedit /etc/modules 
```

**Blackmagic's solution:**
Edit /etc/modules
```
gksudo gedit /etc/modules
```

Add these two lines onto the end:
```
-r usbhid
usbhid mousepoll=2
```

reboot.

**Alternate solution that may work on Feisty (try the first one first):**
Add
```

options usbhid mousepoll=2

```
on its own line at the end of /etc/modprobe.d/options

and then add
```

usbhid

```
on the end of /etc/modules
reboot

**Alternate solution that may work on Edgy:**
Add
```

options usbhid mousepoll=2

```
to /etc/modprobe.d/usbhid 

and then add
```

usbhid

```
on its own line at the end of /etc/modules
reboot

**aidanr's alternate feisty solution**
Create a file at /usr/local/bin/mymousesettings with the following inside:
```

#!/bin/bash
rmmod usbhid && modprobe usbhid mousepoll=2

```

     or if you want to use lomoco (a program for changing the resolution on Logitech mice) you can use this instead:
     (G5 and G7 mice don't need lomoco because they are software-independant)
{
     Install:
```

sudo apt-get install lomoco

```
     lomoco's Homepage: [http://lomoco.linux-gamers.net/]("http://lomoco.linux-gamers.net/")

```

#!/bin/bash
# -4 for 400 cpi, -8 for 800 cpi, -m for 1200 cpi, -h for 1600 cpi, -g for 2000 cpi
lomoco -h && rmmod usbhid && modprobe usbhid mousepoll=2

```
}

After doing either method enter the command
```

sudo visudo

```
and replace the line that says
```

%admin ALL=(ALL) ALL

```
with
```

%admin ALL=(ALL) ALL, NOPASSWD:/usr/local/bin/mymousesettings

```
Use Control + O and then hit enter to save and then use Control + X to exit.

Add that command to startup in System --> Preferences --> Sessions by clicking add and then adding ```
sudo sh /usr/local/bin/mymousesettings
``` as a new entry.
reboot

---

### Post by Eazy© on 2007-03-24
In my experience you have 2 choices:

1. Open a console and do this:
```
sudo kate /sys/module/usbhid/parameters/mousepoll
```
(if you use Ubuntu, replace kate with gedit)

change the 0 to a 2 (500hz) and save the file. Then disconnect the USB-connector for your mouse and put it back again. You have to do this every time you boot your system.

2. Compile your own kernel with the mouse-polling you prefer. You find some info on it [[COLOR="Red"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=374469") 
I have recently compiled kernel 2.6.20.3 from kernel.org with the mouse-polling-patch mentioned in the above link. I did have to use "su" when I applied the patch, "sudo didn't work". Applying the patch is not enough, you also need to change the value to a 2 in xconfig.

---

### Post by Cappy on 2007-03-24
Fixed it with the help of the Gentoo guide:
[http://gentoo-wiki.com/TIP_Change_mouse_hz](http://gentoo-wiki.com/TIP_Change_mouse_hz)

I added
```

options usbhid mousepoll=2

```
to /etc/modprobe.d/usbhid 
(using "sudo nano")

and then I added
```

usbhid

```
on the end of /etc/modules


=)
```

$ cat /sys/module/usbhid/parameters/mousepoll
2

```

---

### Post by Eazy© on 2007-03-25
Nice that worked for you!

I have tried this and it didnt work for me, but that was on Kubuntu Breezy so it was some time ago. I will try this again when kubuntu Feisty comes.

I will add this to my guide.

---

### Post by Cappy on 2007-03-25
I read your UT2004 guide (that's the only game I play - AS @ Omnipotents when I'm bored, otherwise TAM/Freon) and that's what got me into trying to change my mouse polling =) The mouse polling for my G5 was 2ms in Windows and now it feels MUCH better in linux too! I don't have to "jerk" the mouse around as much and my shots are much better with hitscan.

---

### Post by kr0n1x on 2007-04-13
in Windows i'm using at 250hz...how to use 250 hz also in ubuntu?

anyway..if i try to edit mousepoll file with gedit, i can't do it! only with nano i can!

2 = 500 hz

and 250hz??

thanks, bye

---

### Post by Eazy© on 2007-04-13
Here are all the mouse polls:

 1 = 1000Hz
 2 = 500Hz
 4 = 250Hz
 8 = 125Hz
10 = 100Hz (Default)

---

### Post by kr0n1x on 2007-04-14
ok i've edit the 2 files (look Cappy's post)
but i've set mousepoll to 4 (250 hz). i think is more stable with my mx310

thanks, bye

---

### Post by Eazy© on 2007-04-14
2 ms = 500hz should work with your mouse, but use what you think is best for you :)

---

### Post by Cappy on 2007-04-23
-

---

### Post by Cappy on 2007-04-23
This doesn't work on my 64 bit Feisty! I followed the same exact steps =( Adding the usbhid on the end of my GRUB didn't do anything. The only way I'm getting it to work now is by manually changing /sys/module/usbhid/parameters/mousepoll to 2 and replugging in my mouse. I'm using 2.6.20-15-generic.
Anyone have any ideas/solutions on why the usbhid isn't working for me now?

---

### Post by Cappy on 2007-04-24
Cesare Tirabassi on launchpad told me to add

options usbhid mousepoll=2

to /etc/modprobe.d/options

It works on my feisty now. ^^

---

### Post by aidanr on 2007-04-24
> **Cappy said:**
> I followed the same exact steps =( Adding the usbhid on the end of my GRUB didn't do anything. The only way I'm getting it to work now is by manually changing /sys/module/usbhid/parameters/mousepoll to 2 and replugging in my mouse. I'm using 2.6.20-15-generic

same thing here, adding it to /etc/modprobe.d/options (or usbhid)  and /etc/modules doesn't set it to 2 on a reboot, only manually changing it and unplugging the mouse has worked for me so far

which sucks because i've had a jerky mouse problem since installing feisty and this is the only thing that has cleared it up and made it buttery smooth

edit:// i can use ```
sudo rmmod usbhid && sudo modprobe usbhid mousepoll=2
``` which means i don't have to unplug the mouse but it would still be nice to get it working automatically on boot

---

### Post by Cappy on 2007-04-24
My current setup is this:
"options usbhid mousepoll=2" --> to /etc/modprobe.d/options
The file "/etc/modprobe.d/usbhid" is blank.
The file "/etc/modules" does not have "usbhid" in it.
Try making these settings the same as mine, it might work.

Otherwise, you can try adding that command onto your startup session in System --> Preferences --> Sessions

---

### Post by aidanr on 2007-04-24
thanks, i tried that and still no dice, however the following got the job done:

/usr/local/bin/mymousesettings
```
#!/bin/bash
lomoco -h && rmmod usbhid && modprobe usbhid mousepoll=2
```
sudo visudo
```
%admin ALL=(ALL) ALL, NOPASSWD:/usr/local/bin/mymousesettings
```

and add the command mymousesettings to my startup items
probably not ideal but works just fine

thanks a million for the guide, been pulling my hair out for the past week trying to figure out why the mouse was so jerky, even went as far as recompiling the kernel, now everything's shiney \\:D/

---

### Post by aidanr on 2007-04-25
just noticed the edit to the original post, the lomoco -h part is for 1600dpi on certain logitech mice, you may or may not want that

---

### Post by B1ackmagic on 2007-05-30
Just a quick note:

I noticed that aidanr's profile says he's using Xubuntu (as am i)
and that the /etc/modprobe.d/options changes had no effect for me as well.

After spending all day trying to discover why the options
were being ignored or overwritten, I gave up and used this simple hack instead,
which I find  to be simpler than what aidanr did.

Since "/etc/modules" is parsed by a simple sh script ("/etc/init.d/module-init-tools"),
I added the following two lines to "/etc/modules":

```
-r usbhid
usbhid mousepoll=2
```

I would also like to note, that lomoco (if you have the most recent version)
may be easily configured without a script by changing the "/etc/default/lomoco" file.

~ B1ackmagic

---

### Post by Cappy on 2007-06-03
Hey, awesome! I reinstalled Ubuntu and for whatever reason my own method would not work. I just tried your method and it works on my new installation!

I'll update the first post with this information. Thanks for sharing ^^

How did you figure out this "hack"? Can you explain why it works in more detail (or a link, if you have it)?

---

### Post by kr0n1x on 2007-07-25
hi, i tried all method...but i need ever to unplug and plug my mouse in usb port to change the rate:(

then...all settings are set correctly..but i need to unplug the mouse to take effect on reboot...

why???

now i have the Blackmagic method "ON"...and the file /sys/module/usbhid/parameters/mousepoll edited to 2.

what i need to solve the problem of "unplug and replug" on reboot?

thanks bye

ps: i'm using Ubuntu Feisty (desktop, 32bit) and lomoco drivers

---

### Post by High_Yield on 2008-01-18
> **Cappy said:**
> Cesare Tirabassi on launchpad told me to add

options usbhid mousepoll=2

to /etc/modprobe.d/options

It works on my feisty now. ^^

You earlier stated you were using 64 bit - which I am as well - an x2 4600+.

So - how do you tell if it's "working" or not ?  Do you run a script that shows the present polling rate ??

Thanks

---

### Post by Cappy on 2008-01-18
```
cat /sys/module/usbhid/parameters/mousepoll
```
will show the polling rate that is currently active.

---

### Post by kurisu_rs on 2008-05-08
as for Hardy...

I tried quite a few things to change the mouse polling rate but none worked until I tried Blackmagic's:

Add the following to /etc/modules:

```
-r usbhid
usbhid mousepoll=2
```

After a reboot type:

```
cat /sys/module/usbhid/parameters/mousepoll
```

and you should get '2' returned.

This has made Counter-Strike quite a bit less jerky! Yes, CS on Linux! :)

---

### Post by Sycron on 2011-02-09
> **kurisu_rs said:**
> as for Hardy...

I tried quite a few things to change the mouse polling rate but none worked until I tried Blackmagic's:

Add the following to /etc/modules:

```
-r usbhid
usbhid mousepoll=2
```

After a reboot type:

```
cat /sys/module/usbhid/parameters/mousepoll
```

and you should get '2' returned.

This has made Counter-Strike quite a bit less jerky! Yes, CS on Linux! :)

Works on Natty too.

---

