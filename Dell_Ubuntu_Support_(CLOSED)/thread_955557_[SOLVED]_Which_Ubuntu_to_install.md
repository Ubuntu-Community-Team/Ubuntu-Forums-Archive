---
title: "[SOLVED] Which Ubuntu to install"
date: 2008-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by suncoolsu on 2008-10-22
Hi I have a dell studio 1535. I am new to linux. I want to install Ubuntu/Kubuntu but I am still not sure which version to install. 

I tried installing the 64 bit version of Ubuntu but all i get at the end is series of colored lines after the bootscreen. The desktop wont show up. Tried the same with Kbuntu but leading to the same result .. 

please help, I really want to get rid of my Vista. 
Also if I install ubuntu - will I be able to use the attached wifi, bluetooth webcam and mike etc? are the drivers available?

Its becoming harder for me to tolerate vista.

thanks for any help..
B.

---

### Post by anjilslaire on 2008-10-22
Install the x86 version of Ubuntu 8.04.1. Even better, try the [Dell install ISO]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO")

---

### Post by suncoolsu on 2008-10-22
i will try the dell's version - the description appears nice

thnks for the advice

---

### Post by suncoolsu on 2008-10-22
it didn't work .. the same problem still exists :( .. the same white screen with a few colored lines - the only new thing this time was a new sound 

thanks

---

### Post by superm1 on 2008-10-22
Would you mind taking a digital camera shot of this failure screen?  Also, what BIOS do you have,  and what graphics (if you know)?

---

### Post by suncoolsu on 2008-10-23
I have attached the pictures of my laptop screen in the order of their occurrence. 

My Laptop is a recently launched Dell Studio 1535 
configuration is as follows
Intel Core 2 Duo T8100 2.1 Ghz
Video Card - Intel® Integrated Graphics Media Accelerator X3100
OS - Windows Vista ( I tried installing UBuntu with Vista - though i plan to get rid of vista asap)


Please tell if you want to know anything else?

Anyhelp is appreciated .. thanks

---

### Post by Bucky Ball on 2008-10-23
[http://support.dell.com/support/topics/global.aspx/support/dsn/en/tree?c=us&cs=555&dl=false&l=en&s=biz&treeid=56F2C1A4C8ADCC5FE040AE0AB7E16850&doclang=en](http://support.dell.com/support/topics/global.aspx/support/dsn/en/tree?c=us&cs=555&dl=false&l=en&s=biz&treeid=56F2C1A4C8ADCC5FE040AE0AB7E16850&doclang=en)

This any good?

---

### Post by suncoolsu on 2008-10-23
Nope- not helpful :(

---

### Post by zakirs on 2008-10-23
try to boot with the noapic no lapic options .. wait a min iam actually searching for a post which describes the procedure ... its quite easy

---

### Post by zakirs on 2008-10-23
aah just when u boot into cd , a menu might have come,  then hit f6 and then add these  options 
> noapic nolapic 

---

### Post by suncoolsu on 2008-10-23
So this is what happened when I added noapic nolapic after pressing F6. 

The white screen doesnt appear at all. Instead something like a black screen with something written on to it appears saying

BusyBox v1.1.3 (debian and stuff ..) (no0b - so please excuse)

(initramfs) help (i typed help - because it prompted me to do so.

then after displaying various unix commands ... liek wget kill etc.

COMRESET Failed Errorno = -16

- Does the above discritpion sound familiar?

---

### Post by Bucky Ball on 2008-10-23
Try typing:

startx

---

### Post by DrMelon on 2008-10-23
Seems to be a video failure by the looks of it.

---

### Post by superm1 on 2008-10-23
> **suncoolsu said:**
> I have attached the pictures of my laptop screen in the order of their occurrence. 

My Laptop is a recently launched Dell Studio 1535 
configuration is as follows
Intel Core 2 Duo T8100 2.1 Ghz
Video Card - Intel® Integrated Graphics Media Accelerator X3100
OS - Windows Vista ( I tried installing UBuntu with Vista - though i plan to get rid of vista asap)


Please tell if you want to know anything else?

Anyhelp is appreciated .. thanks
This looks like something I've seen with the failing nvidia cards, shortly after the driver is loaded.  I'll see if I can reproduce it at all on a 1535.  One last question: what BIOS version are you on?

---

### Post by suncoolsu on 2008-10-23
Can you please tell me - how to check for Bios version? That will help me in giving you the exact information which you want.

Thanks

---

### Post by superm1 on 2008-10-23
> **suncoolsu said:**
> Can you please tell me - how to check for Bios version? That will help me in giving you the exact information which you want.

Thanks
Yes, hit F2 at the BIOS boot splash screen and you will be taken to the BIOS settings.  It should tell you somewhere there.

---

### Post by suncoolsu on 2008-10-23
The BiOS is A04 - do u want any thing else?

---

### Post by superm1 on 2008-10-24
That should be it.  I'll see if I can reproduce and identify at all.

---

### Post by tgrimley on 2008-10-24
Just wanted to add that I have gotten this before on a Dell 530n and it was resolved..so I don't know that it's necessarily a hardware failure.  I wish I remembered how I did it. (Running 8.10 now.)

---

### Post by suncoolsu on 2008-10-26
i changed xorg.conf - to atleast make the problem of "white screen" go away.

I changed video driver to vesa to solve the problem (helped in this forum by bodhi...). Now I can see the desktop and work with ubuntu on my laptop (i feel very good).

But I am still not able to run the ubuntu with its "full aesthetically pleasing" looks. I have to google search and work on my own.

If anyone happens to know the solution to this problem - help will be appreciated a lot.

My video card is Intel Graphics Accelerator X3100.

Thanks for the help guys ..

B.

---

### Post by Teamgeist on 2008-10-26
> **suncoolsu said:**
> i changed xorg.conf - to atleast make the problem of "white screen" go away.

I changed video driver to vesa to solve the problem (helped in this forum by bodhi...). Now I can see the desktop and work with ubuntu on my laptop (i feel very good).

But I am still not able to run the ubuntu with its "full aesthetically pleasing" looks. I have to google search and work on my own.

If anyone happens to know the solution to this problem - help will be appreciated a lot.

My video card is Intel Graphics Accelerator X3100.

Thanks for the help guys ..

B.

Have you considered using Ubuntu 8.10 on this machine?
You can grab the Release Candidate here:
[http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-rc-desktop-amd64.iso](http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-rc-desktop-amd64.iso)

It works very good on my xps m1330. The Final Version will be out on Oct. 30th.

---

### Post by netlaptop on 2009-01-05
> **suncoolsu said:**
> i changed xorg.conf - to atleast make the problem of "white screen" go away.

I changed video driver to vesa to solve the problem (helped in this forum by bodhi...). Now I can see the desktop and work with ubuntu on my laptop (i feel very good).

But I am still not able to run the ubuntu with its "full aesthetically pleasing" looks. I have to google search and work on my own.

If anyone happens to know the solution to this problem - help will be appreciated a lot.

My video card is Intel Graphics Accelerator X3100.

Thanks for the help guys ..

B.

Thank God, After days looking for the solution, Now I am here!! I have got exactly the WHITE SCREEN like yours.

If you can please tell me how you did it.

Is this process:

1- Press F6
2- Type "startx"

Then how to change xorg.conf, video driver to vesa? 

And do the Webcamera, Bluetooth, Directmedia (touch keyboard) work in Ubuntu? Divers?

My Dell Studio 1535 info:
Studio 1535, Intel Core 2 Duo T5750, 2.0GHz, 667Mhz, 2M L2 Cache
Intel Graphics Media Accelerator X3100
Integrated 2.0M Pixel Webcam
Dell Wireless 370 Bluetooth Module (2.0)

---

### Post by abn91c on 2009-01-05
try disabling desktop effect or remove compiz

---

### Post by netlaptop on 2009-01-07
The problem is that I can not install or boot Ubuntu successfully, How can I disable or enable desktop effect! :D

:D

---

### Post by anjilslaire on 2009-01-07
Once you're at a terminal prompt, do:
```

sudo nano /etc/X11/xorg.conf

```

Find the driver entry in the file, change it to vesa, and save the file (directions at bottom of screen for proper commands. I forget at the moment)

then restart X with 
ctrl+alt+backspace

---

### Post by Maheriano on 2009-01-07
oops, wrong thread

---

