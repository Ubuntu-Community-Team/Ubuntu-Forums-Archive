---
title: "E1505 Resolution Prob - bad hw?"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by DonA on 2007-06-19
My E1505 laptop arrived yesterday.  Out of the box, after the initial setup stuff, I noticed the graphics were weird.  I have the Nvidia card and the wsxga+ (1680x1050) display.  The resolution appears OK, but I'm not sure about the refresh rate (indicated as 50hz).  Pictures are unrecognizable and fonts are fuzzy and broken.  The Ubuntu default "baby doo-doo" wallpaper is decidedly purple.  (In fact, when I registered for this forum, I had to go to another PC because I couldn't make out the letters in the image.)  I've tried the nv and nvidia drivers, rebooting in between.  (I've not even tried Beryl yet.)  I've done the "
    sudo dpkg-reconfigure xserver-xorg
to no avail.  
A buddy at work asked me is I was sure the hardware was OK.  I don't know how to isolate the hardware, and I'm not sure I've exhausted all of the configuration possibilities.  I've seen similar posts but they seem to involve the standard Intel video card--fixed by the 915resolution package.  That doesn't seem to be applicable to the Nvidia card.
Any ideas?  I'm stumped!   Thanks:   ..DonA

---

### Post by DonA on 2007-06-19
Oh yeah...  I did a
sudo ddcprobe
and the output was:
[INDENT]vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: G72 Board - keylh0 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail
[/INDENT]
I'm not sure what to make of this since I don't see the native resolution and default depth (1680x1050x16m) in the list.   Is this significant?

..DonA

---

### Post by Mlehliw on 2007-06-19
I suppose you could try booting the diagnostics utility. To do this just hit f12 at the bios screen to bring up a list of boot options. Choose the Diagnostics one.

---

### Post by DonA on 2007-06-19
Thanks Mlehliw.

I'm posting this from another PC while the E1505 is running the Diagnostics suite.  It came to a 1st stopping point with no errors detected thus far, and I've allowed the diags to continue.  I do notice that in this Diagnostics display, the icons aren't "crisp".  I can make out the green circles with yellow check marks on the tests that have passed; the others are less clear.  All of the gray areas have either a black or white vertical line interlaced with gray.  But the blue outer border is solid.  I suspect this is a normal display, but I'm not sure.

..DonA

---

### Post by binkl on 2007-06-19
I have the same laptop and screen and it's very sharp and the colors are normal. Mine also shows the refresh rate is 50 Hz. I think that's normal.  I get the same output from ddcprobe.

I saw on the dell wiki that they have a special support telephone number for these machines: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Desktops_and_Notebooks_with_Ubuntu_Desktop_Edition_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Desktops_and_Notebooks_with_Ubuntu_Desktop_Edition_7.04)

 They might be able to help.

binkl.

---

### Post by DonA on 2007-06-20
Thanks binki,

I was hoping to exhaust all "configuration" possibilities.  I think I may have done that.  So as you suggested, I called Dell's hardware support line. They say it does sound like either a bad LCD or graphics card. I have the option to send the unit back for an exchange, or have a tech come by the house to fix it.  Either would take 8-10 business days; I opted for the in-house tech, scheduled for June 28.

I hope to be back online with a clear display in a week or so.  Sigh.

..DonA

---

### Post by walkerk on 2007-06-20
You should try to add the native resolution.. check out ubuntuguide.org for instructions..

---

### Post by DonA on 2007-06-20
I should mention--and I should have done this earlier--that I've tried a couple of Live CDs that were lying around.  Each came up with similar graphical "nastiness," and even before X started, the display was not crisp (small vertical lines interlaced).  So I believe the preloaded Ubuntu is OK, and either the nVidia card or the LCD is bad.  

..DonA

---

### Post by DonA on 2007-06-20
I also should have tried this before,,,  I just plugged an external monitor into the unit, and the display is quite nice.  I guess the internal LCD is implicated.  I hope the repair tech brings one.

..DonA

---

### Post by fjgaude on 2007-06-20
Hello, Don!

Funny I have the same screen as you and my ddcprobe shows just what yours show, but my screen is perfect.

I tried the same probe on a 1600x1200 box and the same thing happens, no values that match. So I think this is not the right test.

Try putting the default value in your xorg.conf file in /etc/X11 and see what happens after you reboot.

The tech person may be of more help.

frank

---

### Post by mike999999 on 2007-06-20
> **fjgaude said:**
> Hello, Don!

Funny I have the same screen as you and my ddcprobe shows just what yours show, but my screen is perfect.

I tried the same probe on a 1600x1200 box and the same thing happens, no values that match. So I think this is not the right test.

Try putting the default value in your xorg.conf file in /etc/X11 and see what happens after you reboot.

The tech person may be of more help.

frank

It's actually gonna be interesting what the tech says since it's not on a 'windoze' box.

Let us know how it goes. :p

---

### Post by fjgaude on 2007-06-21
> **mike999999 said:**
> It's actually gonna be interesting what the tech says since it's not on a 'windoze' box.

Let us know how it goes. :p

The tech will likely just replace the video card and see what happens. If that doesn't fix it, then the screen gets changed out. <smile>

frank

---

### Post by DonA on 2007-06-27
Oh joy..  rapture..  peace, harmony, contentment..  ubuntu..

I ended up sending the E1505N back to Dell for repair.  (In a subsequent chat with Dell Hardware Support, I learned that no order had been placed for a technician to make a house call to fix the unit.  Apparently my warranty selection did not include that option.  I suspect I would not otherwise have learned that until Thursday--when the technician was supposed to arrive--had come and gone.

Anyway...  The repair slip indicated that the technician had simply opened the unit and reseated the cable to the LCD, and all was well.  I feel pretty silly; that's a repair I'm capable of making, but I'm a bit hesitant to open up a unit that's under warranty.

Now the fun begins.  So far I'm lovin' it.

..DonA

---

### Post by Paul S on 2007-06-27
I also have the E1505 and replaced my ATI video card with the nvidia to get better linux performance.  I did it myself.  The service manual from dell is awesome .. everything clearly depicted and it only took a couple hours.  No need to be reluctant in the future.

regards,

---

