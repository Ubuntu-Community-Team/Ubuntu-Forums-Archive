---
title: "Black screen after logging in, (after updating)"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kinglink on 2009-10-10
Hey all. 

I've recently got a Linux laptop from Dell (15n series) which is now set up to dual boot Linux and Windows 7 RC, and to do that I decided to remove the recovery partitions.

Anyways I'm kind of stuck, this is the third time I got the official updates to Ubuntu and my linux install doesn't work.  This time I'm not definite that the ubuntu update caused this but since it happened the last two times I'm going to run with that assumption for the moment.  The first two times I reinstalled Linux, I don't want to have to keep doing that.

So the only thing that works after logging in is failsafe terminal, my Windows install works (of course) so I can use that to at least log into the computer.  I don't believe I can use wireless in failsafe terminal, but I can use a wired connection.

So what's happening is I will log into my linux box like normal. Once my authorization goes throw the screen changes to black.  But the top bar of interface will not come up.  In failsafe mode the top bar of any dialog doesn't appear. 

I'm relatively new to ubuntu (and my linux knowledge is out dated) so please feel to treat me like a n00b.   Is there a log I should start by checking/posting to see what's going on?   

I believe the version of ubuntu is v13 or 9.04 or something like that, I saw a command to get the version but I can't remember that right now. 

Let me know what to do and I'll do what I can to get more info.

Frank

---

### Post by coffeeaddict22 on 2009-10-11
Hi,
We're all noobs.  You just have to pick something you don't do often, and we're all pretty green.

I'm not sure of your terminology.  From what you're describing, you are able to boot into Linux via a recovery console?  In GRUB, if you choose the option below the normal boot option, you get a menu selection which includes booting to a terminal with network access, which may be part of what you're looking for.

I'm uncertain what the top bar of interface refers to.  Do you mean X is starting, but not getting to a usable state?  If so, in the recovery menu there's an option to "repair my graphics" which would be worth a try.

The message logs may also be helpful.  Try booting up, then look in /var/log/dmesg.

Post back if you want more help.

---

### Post by Kinglink on 2009-10-11
Well let's see what I can do about clearing this up.   

On my Grub booter I see 
Ubuntu 9.04, kernel 2.6.28-13-generic
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Windows 7 Loader 

The last being my function.  And the kernel number I believe is correct (-13 is s my current kernel)

Now I have already run the recovery program but I'll run it again.  I ran the second option.  Then selected xfix.  Camer back to the recovery menu so I'm good so far.  Then I choose netroot to read some files.  /var/log/dmesg of coure looks fine.

So then I reboot so I can try X (Gnome).  booting with out going into grub, I get the standard Ubuntu start up screen with "Username" (and then "password") I try to log in normally here. and I get the black screen.  Normally there's "application" "Places" and "settings" I believe, which appears on the top bar of the screen (what would be the start menu in Windows).  No idea what it's called.  However that doesn't appear on my interface, so to get into X and have any control, instead of typing my Username, I first have to choose options in the bottom left corner, then selection session, then Failsafe Terminal, finally selecting "change session" and then log in. 

Dmesg doesn't seem to have an issue but I'll upload it here in case I miss something 
obvious.

P.S. I've uploaded dmesg as dmesg.doc otherwise it would not allow an upload.

Link

---

### Post by coffeeaddict22 on 2009-10-11
Sorry to be obtuse.  Are you in a graphical display manager or in a terminal when you've finished booting but unalbe to do anything? 
What's in xorg.log?

---

### Post by Kinglink on 2009-10-11
I am using X display manager with Gnome desktop environment.  

I'm a little confused at what's going on in the Xorg.log but I'll upload it to see if there's something wrong.  (accidentally misnamed it to Xor, but that's the log)

---

### Post by coffeeaddict22 on 2009-10-12
What's your video card?  (output of ```
lshw -C display

```

---

### Post by Kinglink on 2009-10-12
This uses the Intel mobile video card, I could look up the exact model number but this should be the information you are looking for

```
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
 
```

Is the second one necessary?  I know I have one for the screen, but there is also a VGA output on this laptop that does work.

---

### Post by coffeeaddict22 on 2009-10-12
Ubuntu 9.04 and Intel graphics don't mix.  Strongly suggest you upgrade to the 9.10 beta.  Have a look [here for more info]("http://ocaoimh.ie/ubuntu-laptop-intel-graphics-speed-boost/")

---

### Post by Kinglink on 2009-10-13
Bingo! took me a while to install (openoffice bug) but I'm up and running again, and it feels good.    Thank you very much.

---

### Post by v1nsai on 2009-12-14
I set up the X-retro PPA and whenever I try to install 'xserver-xorg-video-intel-2.4' it tells me the package doesn't exist o_0

Is there a way to browser only packages from a particular source?  This is really frustrating, I know I put in everything correctly, I added the key and did apt-get update and it still says the package isn't there.....

I'm using karmic 64 bit.  Maybe it isn't available for 9.10?  I'm trying to install this because my display driver is labeled unclaimed when I use 'lshw -C display' and my compiz effects are a little laggy.

---

