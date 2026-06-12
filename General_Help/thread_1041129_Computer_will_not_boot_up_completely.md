---
title: "Computer will not boot up completely"
date: 2009-01-16
forum: General Help
---

### Post by mikeric on 2009-01-16
The other day I tried to start my computer and it it would boot up to the login screen but the operating system would not load. I had Xubuntu on it at the time. I ended up reinstalling ubuntu 8.10 and it installed fine and then when it restarted at the end it did the same thing the operating system would not start. I tested my harddrive with the Drive Fitness Test and it came back fine. Im not sure what to do next. Any ideas?

---

### Post by taurus on 2009-01-16
Do you mean X would not start or do you mean the system just hangs?  Take a screenshot with a camera if you could.

---

### Post by linux_tech on 2009-01-16
Any error messages?

If possible, post output of ```
dmesg
```
You are unable to load desktop--right?  
If so, at cmd prompt try booting in recovery mode & startx-
```
startx
```
or
```
/etc/init.d/gdm start
```
If nothing, then re-install desktop-
```

sudo apt-get install ubuntu-desktop
```

---

### Post by matey3 on 2009-01-16
did you try the other ttys? like terminal 2?
do control-alt-F2 or F3 etc.
My 1st terminal is like that too? I dont know what it is? may be something in my menu.lst? But when I go to the tty1 (if u count tty0 as the 1st) up to tty6 (7 is the GUI) then it is all good!

---

### Post by mikeric on 2009-01-16
The first picture shows what i get. Just the tan background. When i went to take the picture it did what the second one has for the first time. Now im just getting a black screen with the mouse cursor on it.

---

### Post by taurus on 2009-01-16
Looks to me like X crashed!  What graphic card do you have?  Try booting into recovery mode from GRUB menu and run the fix X server, xfix, option.

---

### Post by mikeric on 2009-01-16
Im not sure on the graphics card, the computer was my girlfriends old one. She was having a ton of issues with it running really slow on xp last year so i just ended up switching to Ubuntu. I tried the fix X server option and it didnt make a difference, when I boot it it still does the same thing.

---

### Post by mikeric on 2009-01-16
Linux_Tech this is what I got when I ran dmesg

[IMG]http://i499.photobucket.com/albums/rr355/Mikeric03/IMG_0060.jpg?t=1232126252[/IMG]

---

### Post by linux_tech on 2009-01-16
Have you tried booting in recovery mode typing ```
startx 
```or
```
/etc/init.d/gdm start
```

if not, can you restart in recovery mode and use the ```
xfix
``` option?

try these options, then report back

---

### Post by mikeric on 2009-01-16
If I reboot with startx I just get a black screen.

When I use /etc/init.d/gdm start I get what i was getting beore then a black screen with the mouse cursor, that freezes.

I tried using xfix and it didn't change anything.

---

### Post by linux_tech on 2009-01-16
what are the system specs:
make, model
graphics card
RAM
cpu?

In terminal type:
```

sudo lshw
```then cut and paste the output into your post reply
or attach as text file to post

---

### Post by linux_tech on 2009-01-16
If I knew the make and model I can find the specs online 
and provide further assistance

---

### Post by mikeric on 2009-01-16
The computer is a dell dimensions 2400. It is from 2003. Everything should be original other than a dvd drive and I added 1gb of ram. here is what i got when I ran sudo lshw.

[IMG]http://i499.photobucket.com/albums/rr355/Mikeric03/IMG_0061.jpg[/IMG]

---

### Post by mikeric on 2009-01-17
Does anyone have any other ideas?

---

### Post by linux_tech on 2009-01-17
Boot to bios, check the setting for integrated video memory- if it is set to 1MB, select 8MB,  

To do this press f2 at boot, enter bios setup and change the 'Onboard Video Buffer' from 1MB to 8MB 

The video buffer option is under the 'Integrated Devices (LegacySelect Options)' menu in the BIOS.

Also check this solution here:
[https://answers.launchpad.net/ubuntu/+question/51790](https://answers.launchpad.net/ubuntu/+question/51790)

(set Onboard Video Buffer to 8 )

8)

---

### Post by mikeric on 2009-01-17
I changed the onboard video buffer to 8mb. Then I tried to do everything that said but was confused at this part. I could not get it to download the update. I got the error message it talked about in that post. 

> sudo nano /etc/network/interfaces

"here you will have a file pulled up where your code that runs your network interface is located. It should look something like what is below

# The primary network interface - use DHCP to find our address
auto eth0
#iface eth0 inet dhcp

it is kind of hard to see, but that is without spaces # i f a c e remove the number sign (comment) you will have to go before it and press delete, backspace for some reason didn't work at least not on mine."

My computer said this when that file was loaded.
> 
auto lo
iface lo inet loopback

It is still doing the same thing, other than one time i got the ubuntu loading screen, and another I got a black screen with the circle cursor for when things are loading. Thanks for all the help so far.

---

### Post by mikeric on 2009-01-19
I know everythign on the computer is working correctly right now. Was somethign changed in recent updates that could cause this? The computer has been running ubuntu for almost a year now with no problems. I am using windows 7 beta right now, but still want to get ubuntu working again.

---

### Post by mikeric on 2009-01-24
Well i got the computer working. I got an nvidia 8400GS and now everything is working. It must have been a problem with the integrated intel graphics. I don't know why it all of a sudden started though.

---

