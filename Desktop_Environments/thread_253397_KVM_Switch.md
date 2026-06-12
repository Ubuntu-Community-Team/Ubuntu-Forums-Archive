---
title: "KVM Switch"
date: 2006-09-08
forum: Desktop Environments
---

### Post by McBainUK on 2006-09-08
I'm thinking of getting [this KVM switch]("http://www.ebuyer.com/UK/product/75629") to allow me to have my gaming PC and my dev/HTPC machine hooked up to one monitor, keyboard and mouse.

Have a 19" Samsung running off VGA, one PC with WinXP only and another with WinXP and Ubunu linux on dual boot. I want to use the KVM with a Microsoft Multimedia keyboard and IntelliMouse.

Questions/Issues
* Googling I've found that not all keyboards work with KVM due to a Scroll Lock key problem, does this include my Microsoft Multimedia keyboard?
* Would a KVM introduce lag on keyboard/mouse commands? This would be a nightmare when playing games.
* Would all the extra multimedia buttons on the keyboard still work when used through a KVM?
* Do all KVMs work with Linux/Ubuntu?

Anyone help?

---

### Post by breuerp on 2006-09-08
* Googling I've found that not all keyboards work with KVM due to a Scroll Lock key problem, does this include my Microsoft Multimedia keyboard?

This is not an issue if you buy a KVM that supports USB mice.  This if *FAR* more common than it used to be.  Belkin, IOGear and others sell 2 and 4 port KVMs that support USB keyboards, mice and sharing sound speakers as well.

* Would a KVM introduce lag on keyboard/mouse commands? This would be a nightmare when playing games.

You won't see any lag at all.

* Would all the extra multimedia buttons on the keyboard still work when used through a KVM?

The multimedia buttons work through the drivers in the operating system.  The KVM shouldn't affect this at all.

* Do all KVMs work with Linux/Ubuntu?

I guess the safe answer here is "no."  I'm sure there's one out there that doesn't but as far as I know, they all work.  I'm using a Belkin 4-port USB KVM on my Ubuntu box to type this.  I've never had an issue.

---

### Post by McBainUK on 2006-09-08
> This is not an issue if you buy a KVM that supports USB mice. This if *FAR* more common than it used to be. Belkin, IOGear and others sell 2 and 4 port KVMs that support USB keyboards, mice and sharing sound speakers as well.
It's a PS/2 keyboard but a USB mouse, but would connect the mouse via a MS supplied USB->PS/2 converter. Would this be a problem?

---

### Post by Crooksey on 2006-09-08
I have that setup on like a 4 year old KVM switch, 19" monitor, gaming box (windows and linux) and a test box. Works fine. 

I used to have an inteli mouse and it worked, and i am using the converters from usb to serial aswell, not a problem.

---

### Post by McBainUK on 2006-09-08
> **Crooksey said:**
> I have that setup on like a 4 year old KVM switch, 19" monitor, gaming box (windows and linux) and a test box. Works fine. 

I used to have an inteli mouse and it worked, and i am using the converters from usb to serial aswell, not a problem.
Great, just what I wanted to hear :)

---

### Post by whizbaby on 2006-09-08
> **McBainUK said:**
> 
* Do all KVMs work with Linux/Ubuntu?

I think kvm are OS-independant (all devices I know are useable at BIOS-boot time when no OS is yet loaded). There only could be hardware-issues...

---

### Post by Crooksey on 2006-09-08
I have never found an OS not to be supported by my KVM

---

### Post by CaveRat on 2006-09-08
I'm using a Trendnet KVM with no problems at all. I'v had Winxp, Win2000, 98, Ubuntu, and Fedora machines plugged in to it with no issues at all.

---

### Post by McBainUK on 2006-09-08
> **Crooksey said:**
> I have that setup on like a 4 year old KVM switch, 19" monitor, gaming box (windows and linux) and a test box. Works fine. 

I used to have an inteli mouse and it worked, and i am using the converters from usb to serial aswell, not a problem.
Was it a Belkin?

---

### Post by dmizer on 2006-09-10
my usb kvm will not switch when pressing scroll lock twice in the GUI environment.  it's a ratoc systems usb kvm.  and i have both a usb mouse and a usb keyboard.  i can switch if i am in the virtual terminal (ctrl+alt+f1) but not when i'm in the gui.

this is beyond annoying, and i can't find any answers anywhere.

---

### Post by whizbaby on 2006-09-10
> **dmizer said:**
> my usb kvm will not switch when pressing scroll lock twice in the GUI environment
Perhaps experimenting with the keyboard layout options *XkbModel* and *XkbVariant* in /etc/X11/xorg.conf can activate the scroll-lock key. (If you can switch at boot time there would be no BIOS problem)

---

### Post by tturrisi on 2006-09-10
> **dmizer said:**
> my usb kvm will not switch when pressing scroll lock twice in the GUI environment.  it's a ratoc systems usb kvm.  and i have both a usb mouse and a usb keyboard.  i can switch if i am in the virtual terminal (ctrl+alt+f1) but not when i'm in the gui.

this is beyond annoying, and i can't find any answers anywhere.
Try scroll lock twice + arrow down key.

---

### Post by dmizer on 2006-09-12
> **tturrisi said:**
> Try scroll lock twice + arrow down key.

no dice on that.

---

### Post by McBainUK on 2006-09-12
Arrgh! I just plugged in the Belkin 2port KVM (PS/2) but can't get it to switch! :mad: Tried it with a MS Multimedia Keyboard and a unbranded one.

Any ideas?

---

### Post by McBainUK on 2006-09-13
FYI: Found that the Belkin 2-port kvm also responds to to double tapping CTRL and then hitting UP or DOWN to swtich computers.

---

### Post by Russty of Oz on 2006-09-13
I use the Belkin KVM. I have no problem with it at all.  I have a wireless keyboard and a usb mouse and they both work fine.  I tried a cheaper brand at first but it wouldn't work at all with my keyboard and mouse, so what every you buy, ensure you can return it if it doesn't work and then try another brand.  The KVM switch is a great idea!

Russty.

---

### Post by pony-tail on 2006-11-07
Not all KVM switches work with Linux - A lot of them screw up the mouse when switching between two running machines . This is caused by poor mouse emulation in the Switch itself K/Ubuntu seems more susceptible to this than some other distros - I run 6 computers on 3 monitors all on 2 way KVMs  and I am still searching for one that does exactly what it is supposed to how it is supposed to . Further be careful with KVMs and nForce 4 chipsets as they can be very flakey (IO gear is one that can be very bad Aten is another )

---

### Post by zenon212 on 2007-05-24
I was messing around trying to solve this KVM/Scroll Lock problem and found something interesting. Everything in my TrendNet KVM Manual says that the Scroll Lock is the key to use, but when I hit the Num Lock key twice in either Ubuntu or Vista it switches just fine. I only looked because the Scroll Lock wasn't lighting up the LED. I hit the Number Lock key once to turn it on and light up the LED and then again to turn it off and I was switched back to my Windows box.

So, for me, Num Lock works in both, but Scroll Lock only works in Windows.

---

### Post by meghuizen on 2007-07-20
I've found a possible solution for this problem. It's from the following site: [http://www.catherders.com/tiki-view_blog_post.php?blogId=1&postId=113&highlight=scroll%20lock](http://www.catherders.com/tiki-view_blog_post.php?blogId=1&postId=113&highlight=scroll%20lock)

Changed for ubuntu:
First, regular text mode (non-X) -
Put this in the /etc/rc.local file (or somewhere else where it will be executed before the login prompt)

echo 'keycode 70 = F70'|/bin/loadkeys

and second, to remove the Scroll Lock mapping from terminal sessions of X-Windows, put this in the .bashrc file.

xmodmap -e 'keycode 78 ='

---

### Post by chapterthree on 2007-12-27
> **zenon212 said:**
> I was messing around trying to solve this KVM/Scroll Lock problem and found something interesting. Everything in my TrendNet KVM Manual says that the Scroll Lock is the key to use, but when I hit the Num Lock key twice in either Ubuntu or Vista it switches just fine. I only looked because the Scroll Lock wasn't lighting up the LED. I hit the Number Lock key once to turn it on and light up the LED and then again to turn it off and I was switched back to my Windows box.

So, for me, Num Lock works in both, but Scroll Lock only works in Windows.

You are my HERO!!!!   Thank you so much, this has been driving me nuts for [quite a while](http://ubuntuforums.org/showthread.php?t=231700) (and apparently I didn't do enough searching when I originally had this problem).

---

