---
title: "Ubuntu 7.10- Bluetooth"
date: 2007-10-17
forum: Dell  Ubuntu Support
---

### Post by igggyc on 2007-10-17
Hi guys

I installed Ubuntu 7.10 on my laptop (Dell Inspiron 1720).

It has a "Bluetooth Manager" icon on the system tray. I right click on it, and press "browse device". It finds my phone, yet when I select what it has found and press "connect", it gives me the following error: ""obex://[00:1a:dc:d1:bc:2d]" is not a valid location. Please check the spelling and try again".

Can anyone suggest anything?

My phone model is a Nokia N95.

p.s, sending files from my phone to the laptop works fine!! just no luck doing anything from the laptop to the phone.

---

### Post by PmDematagoda on 2007-10-17
I have the same issue as well except in my case the computer just freezes without returning back to normal. I was trying to browse the contents of a K510i myself. Does anyone know how this could be done?

---

### Post by cygnis1 on 2007-10-17
I get a similar message.  My message says "service not supported".  I have a new Motororazr V3XX.  I would like to use audacity to make ringtones and upload them to my phone.
Thanks
Cygnis1

---

### Post by raggari on 2007-10-18
This is just guess but do you have package **gnome-vfs-obexftp** installed? I'm pretty sure that is needed for BT file transfer.

EDIT: Yes, you need that package. I also worked for me with Nokia N80.

---

### Post by cygnis1 on 2007-10-18
I have installed  gnome-vfs-obexftp  and it still does not transfer.  I have been able to send a file to the computer, but not from the computer to the phone.  Is there another program that I can use?
Thanks,
Cygnis1

---

### Post by cygnis1 on 2007-10-18
I am sorry for being so stupid.  I restarted the computer and it now works.
Thanks,
Cygnis 1

---

### Post by omiazad on 2007-10-20
> **igggyc said:**
> Hi guys

I installed Ubuntu 7.10 on my laptop (Dell Inspiron 1720).

It has a "Bluetooth Manager" icon on the system tray. I right click on it, and press "browse device". It finds my phone, yet when I select what it has found and press "connect", it gives me the following error: ""obex://[00:1a:dc:d1:bc:2d]" is not a valid location. Please check the spelling and try again".

Can anyone suggest anything?

My phone model is a Nokia N95.

p.s, sending files from my phone to the laptop works fine!! just no luck doing anything from the laptop to the phone.

I faced the same problem. I wanted to use the Nokia 6233 as modem over BlueTooth, but it said the same thing.

But it picked up my Microsoft Bluetooth mouse and worked 100% well, but I have no idea why Phone didn't work. I also tried Nokia 5500 and 5300, same bad result.

Can anyone give us a solution?

---

### Post by bluenova on 2007-10-21
omiazad,

Did you install the package mentioned above; gnome-vfs-obexftp? Everything worked for me after I installed that.

---

### Post by omiazad on 2007-10-21
> **bluenova said:**
> omiazad,

Did you install the package mentioned above; gnome-vfs-obexftp? Everything worked for me after I installed that.

Na,
I didn't install anything, because I think obexftp is for transferring files to cell phones.. I don't want to transfer files to my cell phone. I want to use the mobile phone as modem over Bluetooth. Do you have any GUI solution for that?

---

### Post by PmDematagoda on 2007-10-22
> **omiazad said:**
> Na,
I didn't install anything, because I think obexftp is for transferring files to cell phones.. I don't want to transfer files to my cell phone. I want to use the mobile phone as modem over Bluetooth. Do you have any GUI solution for that?

Yep, Blueman Bluetooth Manager, it is very good and very functional, I was able to connect to the internet using my K510i. It can be found here:-

[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

---

### Post by MarkoSK on 2007-10-23
i had the same problem connecting and sending files to mobile phone and installing **gnome-vfs-obexftp** and restarting blue tooth services did the job...tnx for info...

---

### Post by BeastlyKings on 2007-10-23
It didn't do the job for me :(
It just tells me:
Couldn't display "obex://[00:16:b8:26:cf:f8]".
Check if the service is available.

It DOES work, but only when I first start the computer, and only for a few transfers, then it just stops and I get this error every time I try again.

Help?

---

### Post by techpr on 2007-10-24
Thank You...!!!  installed gnome-vfs-obexftp and my Nokia and Motorola phones worked fine in Ubuntu 7.10.

---

### Post by omiazad on 2007-10-24
> **techpr said:**
> Thank You...!!!  installed gnome-vfs-obexftp and my Nokia and Motorola phones worked fine in Ubuntu 7.10.


Did you try using the phone as Modem? Will 
gnome-vfs-obexftp help me to use my phone as modem?

---

### Post by techpr on 2007-10-24
> **omiazad said:**
> Did you try using the phone as Modem? Will 
gnome-vfs-obexftp help me to use my phone as modem?

Sorry no, it was for photo transfer. Worked in seconds and fast.

---

### Post by techpr on 2007-10-24
But I still have some issues using my Microsoft Bluetooth keyboard. It works OK but disconnects if I don't use it from 10 or 15 minutes and I must run again **sudo hidd --search** to connect again.

It does not work from the Bluetooth Applet.

---

### Post by techpr on 2007-10-27
I had my Microsoft Bluetooth Keyboard working great on boot time in 7.04. Now on 7.10 I have to manually run **sudo hidd --search** all the time, even past the 10 or 15 minutes I must use my regular PS2 Keyboard to connect **again** my Bluetooth Keyboard.

I'm trying to determine if this applies to me.
[https://launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)


This is my /etc/default/bluetooth

```

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect 00:50:F2:E8:80:5A --server"

```

---

### Post by illbashu on 2007-10-31
i want to run my bluetooth headphones what do i need to do/install to get them to work?

EDIT! they are A2DP headphones with mic

---

### Post by illbashu on 2007-10-31
bump! someone plz help... ok, i can see the headphone and when i go to connect to them and type the password in and press ok i get this error "Couldn't display "obex://[00:07:a4:f2:64:e6]".

---

### Post by plasticM on 2007-10-31
I'm getting the same error when trying to connect to my SE k750i.  My dongle is an f8t012uk (
Actually recommended here:
[https://wiki.ubuntu.com/UKTeam/Hardware](https://wiki.ubuntu.com/UKTeam/Hardware)
)  It pairs but nothing else.  Really annoying as it used to work under 7.04 with kbluetoothd, but I can't find that any more. :(

---

### Post by dysolve on 2007-11-04
install obex as said before.. obex should work for everything except dailup connects..

---

### Post by krcabrer on 2007-11-22
Some help:
I have a Motorola L6 phone and I follow all the instructions,
but I alway got the message:

Can't show <<obex://[00:17:00:f5:99:b3]>>

Check if the service is available.

I modify the pin file, I restart the computer, I install the obex 
vfs, and stills the problem.

When the system search for a bluetooth device, my phone
iluminate the screen, but I still got the problem

Please help me.

---

### Post by krcabrer on 2007-11-22
I forget, sorry my system:
I am running ubuntu 7.10 and the  phone is a Motorola L6.

Thank you for your help

---

### Post by krcabrer on 2007-11-22
Finaly it works.

I got blueman from the homepage... and now it works.
Why? I don't know.

Thank you.

---

### Post by Blackgirl on 2007-11-25
Okay. Well im new to Ubuntu and not sure if im posting in the right thread! But i am trying to get Bluetooth working on my computer!! I have ubuntu 7.0 and yeah my phone wont pick up the omputer or anything, I downloading the obex thing and yeah cant find it so please someone help me!!!

---

### Post by Blackgirl on 2007-11-25
by the way my phone is a Motorola V3

---

### Post by raxso on 2007-11-26
Install Blueman Bluetooth Manager, this works for me..
Here is the link [http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

enjoy.

---

### Post by adityam on 2007-11-26
> **raxso said:**
> Install Blueman Bluetooth Manager, this works for me..
Here is the link [http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

enjoy.

Thank you for the link. I was struggling with connecting my Nokia 5300 to my laptop. With blueman, I can connect and transfer data.

Aditya

---

### Post by raxso on 2007-11-27
> **adityam said:**
> Thank you for the link. I was struggling with connecting my Nokia 5300 to my laptop. With blueman, I can connect and transfer data.

Aditya

Glad to help.....:)

---

### Post by geeree on 2008-04-12
> **BeastlyKings said:**
> 
It DOES work, but only when I first start the computer, and only for a few transfers, then it just stops and I get this error every time I try again.

I have this same problem. I installed gnome-vfs-obexftp and tried to communicate with a K510i for transferring files. I could transfer a few files successfully but after that I again get this error: 

```

Couldn't display "obex://[00:1a:75:34:e1:8c]".
Check if the service is available.
```

Rebooting doesn't help. What could be happening? 

Thanks,
Girish.

---

### Post by tbraun on 2008-06-16
Hello!

The problem is solved for me now!

After having the same "can't display" problem as most other people here, I stumbled across a page that talked about a package I hadn't heard before: obexfs.

After I installed it (it's in the repositories), I could use 'blueman' (and presumably other Blutooth apps) to connect. The "can't display" error message went away.

Hope that helps...

---

### Post by tbraun on 2008-06-16
Argh!

It worked ... once.

Now that I disconnected and connected again, I am receiving the "can't display" error once more.

Before I was able to do "nautilus --browser" and then select "obex:///" in the location bar. It would show the device and I was able to browse to it.

Now this doesn't work anymore. Nautilus takes forever and finally comes back with the usual error message ("can't display...").

I stopped and restarted the bluetooth services, I even reinstalled obexfs ... no luck. Some setting must have been changed the first time I successfully connected, which made it impossible for me to connect again.

Dangit!

---

### Post by tbraun on 2008-06-16
Ok, so logging out of Gnome and then logging back in made it work ... once. For one file.

This is all very, very odd. It would be great if that could be made to actually work!

---

