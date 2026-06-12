---
title: "rendering of characters in Firefox (periodic problem)"
date: 2011-01-29
forum: Desktop Environments
---

### Post by Termo on 2011-01-29
I have a weird issue in Firefox on Ubuntu 10.10, and sadly it's a periodic mistake that I don't know how to initiate...

Sometime in firefox some of the characters seems not fully rendered, and as I recall it can also happen in menu fonts sometimes. In the attached screen-shot you can see that it's the a character that has the problem - but only for one font type or? But I have seen this with most characters I think - and as stated this happens randomly.

For instance right now I looked again in the tab in firefox where I just 5 minutes ago did the screen-shot and now all characters are correct?? I have tried to reload or even restart firefox when it occurs, but this is now guaranty for a solution...

Any ideas of what courses this and how I can stop it from happening. When it happens it makes many homepages unreadable :(

Best regards Rasmus

---

### Post by Termo on 2011-01-29
[Update]
Actually now 5 minutes later again it's now the "y" character in the same homepage?!?!?

---

### Post by digismack on 2011-02-02
I am having the same problem. I have noticed it in Firefox (3.6.13) and in the console when using nano or similar text editors. I can have the same website open in Firefox and Chrome.. Firefox renders the font with the problem at hand, Chrome renders the website fine. I am a web developer / designer so I can't just not use Firefox. 

I have ran memtest86+ and it completed with no errors. Anyone able to help us out here? Would be greatly appreciated.

(Edit: Updated error info.)

---

### Post by Termo on 2011-02-09
*BUMP*

It's really annoying, there must be someone out there with a hint or an idea on how to find what is causing this... ](*,)

---

### Post by Krytarik on 2011-02-09
Does this also happen with a fresh user profile?

---

### Post by Termo on 2011-02-10
Thank you for suggestion - I have myself thought of completely remove firefox settings folder in home and then slowly migrate settings back...

Anyway, just made a new user, and now already in the window title the "o"s this time was partly rendered. So this issue is not to do with firefox explicit but general character rendering. This also goes find in hand with my observation from firefox that when making fonts bigger or smaller (ctrl + or -) would make the issue disappear in the other sizes, but re-enter when back to normal size.

Switching user back shows no rendering error in my normal user account. Switching back again still shows the rendering error...


So with this new information where to look now??

---

### Post by Krytarik on 2011-02-10
Try fiddling with the options in "System -> Preferences -> Appearance -> Fonts -> Details".

---

### Post by Termo on 2011-02-11
I have now been playing around a bit with fonts settings in Firefox to find out where and what changes this...

First I thought that disabling "Allow pages to choose their own fonts" would make the difference, but then the rendering error also came when I had my settings to control fonts on pages.

Then I thought it only had to do with Serif fonts, but that apparently just depends on what I choose in "proportional", which by standard is for Serif in firefox. When I changed this to sans-serif the error came again at some point...

As the two types of uploaded screenshots show does the error change when I change font - but these two screenshots also show that it happens both for the Droid and the DejaVu font. So not font specific apparently :-s

---

### Post by Krytarik on 2011-02-11
I thought it was already clear to you, that the issue doesn't have anything to do with Firefox, since it also occurs in the window titles of Nautilus, the previously posted screenshots.

What about the general font rendering settings I mentioned? Though I doubt this would fix it.

---

### Post by Termo on 2011-02-11
True that the error is not specific to firefox - but I only very rarely see it in the general fonts used in Ubuntu. So when I saw it in Firefox again I tried to get some knowledge into if it was specific for any specific font...  But that does not seem to be the case.

Yes I tried to look into the Appearance but the only difference I saw to the Ubuntu install I have on a usb-HDD was the 'Document font' that I changed to Sans as on the usb. But the problem still came back in Firefox.

---

### Post by Krytarik on 2011-02-11
> **Termo said:**
> 
Yes I tried to look into the Appearance but the only difference I saw to the Ubuntu install I have on a usb-HDD was the 'Document font' that I changed to Sans as on the usb. But the problem still came back in Firefox.
Please! ;):
> **Krytarik said:**
> Try fiddling with the options in "System ->  Preferences -> Appearance -> Fonts -> Details".

---

### Post by Termo on 2011-02-12
Fair enough...

my point being though is that in appearance it is only the font choices that could be the ones to play around with - right? And in firefox when I see the error now I can change font choice explicitly, changing font choices in "appearance" does not affect font rendering in the pages in firefox.

Anyways now had the error in a terminal window and then changed the monospace font in "appearance" to stop the error - for now.

Really the error seems to come with any of the serif/sans serif/monospace type fonts, and with both the Ubuntu, DejaVu and Droid fonts. Changing the affected font choice to another font removes the error, but to my knowledge so far it will come again with the new font choice...

Edited:
Sorry, just saw now that you explicitly suggest to play with settings in "Details". I will try this for now and get back...

---

### Post by Krytarik on 2011-02-12
> **Termo said:**
> 
Sorry, just saw now that you explicitly suggest to play with settings in "Details". I will try this for now and get back...
I could have made it more conspiciuous.:)

---

### Post by Termo on 2011-06-01
I just did a fresh install of Ubuntu 11.04, and the problem persists?!?

I was actually thinking that it had to do with some configuration that I had played with at some point - but now on a fresh install of Ubuntu I also have the problem:(

In the attached screenshot please note that the problem is only in Firefox not in the printed pdf shown next to it. As before changing the font size in Firefox makes the problem go away, but only in the new sizes. When going back to normal size the problems are still there...

A new thing is the rendering problem also in graphics as seen here in the Home icon in the top right?!?!? I have now also seen the same problems in buttons on home pages.

Any ideas where to look for this. This really makes home pages hard to read at times...

---

### Post by Horseboy on 2011-06-01
Happens to me as well, but not just in Firefox...

---

### Post by Krytarik on 2011-06-01
As you already experienced earlier, is that issue not entirely confined to Firefox, although it occurs much more often in the latter.

So, the root cause might be more an issue with the video hardware/driver than Firefox.

What video card/chip do you have?
What driver are you running?
How did you install those?

You may also post the output of:
```
lshw -c video
```That will include the name of the video controller as well as of the running driver.

---

### Post by Termo on 2011-06-01
Hi Krytarik.

Ones again thank you for taking your time...


lshw output:
```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:a0080000-a00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:a0000000-a003ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:80200000-8027ffff


```

I believe that you are right that this problem is not strictly related to Firefox. In regard to your questions am I just running the standard xorg-intel driver. The only thing I remember with this install to have done extra is that I'm currently running the Xorg-edgers PPA, because I read somewhere that that could help on the bit slow Unity interface at times. I will try to purge this PPA back, and see if this changes anything.

I have tried to google a bit the unclaimed i915 driver and can find this bug: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/154729]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/154729")

But I can actually use my laptop just fine with external monitor and switch fine between them. The only thing in that regard is that open lid after it has been closed does not turn on my screen again. This one has existed since 10.04 sadly...

---

### Post by ux386 on 2011-09-14
I was having this same problem with Debian testing. The problem seems to be indeed the video driver, but downgrading X didn't work. I downgraded to kernel 2.6.32 and it seems to have fixed the problem.

---

