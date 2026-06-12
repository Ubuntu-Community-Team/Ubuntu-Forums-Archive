---
title: "competability with Inspiron 11z"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by orengolan on 2009-11-03
I think of buying this laptop with the intel su4100 cpu (not the celoron).

can you share your experience with this laptop?
what issues do you have and do you like the touchpad?

Thanks

---

### Post by cyberfella on 2009-11-06
11z and ubuntu 9.10 works perfectly, with or without the restricted drivers for the networking hardware.  desktop effects work perfectly too, as does the touchpad.  i can't fault it.  i'm well impressed.

just a tip before installing off a bootable usb stick - boot 9.10 desktop cd on another machine, create the bootable usb stick using the utility in ubuntu, dont try using unetbootin, i had issues with that, but the ubuntu desktop utility on a freshly formatted stick worked perfectly.

its a very sweet little laptop, i must say!

---

### Post by orengolan on 2009-11-06
Thanks for the quick reply, This is great news for me.

I read bad reviews of the touchpad (with window os) - something about zooming unexpectedly or too sensitive. 
Do you use the default configuration or do you have to tweak 
it's behavior to make it more usable?

---

### Post by iggykoopa on 2009-11-10
I just got mine in yesterday. Everything working well here as well. The touchpad works with two-finger scrolling out of the box, but other multi-touch stuff like zooming doesn't work so it's not an issue. The mouse seems much better under ubuntu, not nearly as jumpy.

---

### Post by orengolan on 2009-11-14
I got the Inspiron and it took 5 minutes to install xubuntu 9.10 from a usb. amazing!

The following are not working:
brightness keys (F4/F5).
Zoom in/out using 2 fingers on touchpad.

Also, I want to make the touch less sensitive.  how do I configure it? 
Thanks!

---

### Post by Zaraka on 2009-11-17
Install the BIOS update (rev. A04, I think)  to resolve the problems with the brightness.

The touchpad identifies itself like a mouse attached to a ps/2 port, so gnome don't display the touchpad options. I don't really care the zoom, but I'd like to have horizontal scroll...

---

### Post by orengolan on 2009-11-18
thanks for the tip!

I googled for bios upgrade and found this:
[http://ubuntuforums.org/showthread.php?t=648824&highlight=biosdisk](http://ubuntuforums.org/showthread.php?t=648824&highlight=biosdisk)

But I failed on step 3: sudo aptitude install sysutils syslinux
it can't find them.

Is there another guide I can follow?
Also, what can I do to minimize the risk of upgrading the bios?

---

### Post by Zaraka on 2009-11-18
The BIOS is here:
[http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INSPIRON1110&hidos=WLH&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INSPIRON1110&hidos=WLH&hidlang=en&TabIndex=)

I have do it through the "bad" way, yet the easiest. That is, in windows.

---

### Post by orengolan on 2009-11-21
I have the exe file, I am not sure what to do with it (-:
I tried following the instructions here- [http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk)
but got confused.

any link to a step-by-step will be great.
 
btw, can I try to disable the tap in the touchpad while I am typing by running this: syndaemon -t 
but get this: 'unable to find a synaptics device'.
I am curious if it's working for you, and if it is, please share your xorg.conf.

here is the bug on launchpad, my reply is the last one -
[https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627)

and [here]("http://ubuntuforums.org/showthread.php?p=8454167#post8454167") is a new thread I started.
thanks!

---

### Post by orengolan on 2010-04-12
I just upgraded to 10.4 (pre-release) and the video out key is not working.
before I submit a bug report, let me know if you have the same issue.

---

### Post by macey on 2010-04-14
> **orengolan said:**
> I just upgraded to 10.4 (pre-release) and the video out key is not working.
before I submit a bug report, let me know if you have the same issue.

Are you running 64 bit 10.04?
Did you 'upgrade' or fresh install?

---

### Post by orengolan on 2010-04-14
32 bit and upgrade. not fresh install.

---

### Post by macey on 2010-04-15
> **orengolan said:**
> 32 bit and upgrade. not fresh install.

I have ordered the same machine, can you tell me why you are not running 64 bit? Just wondered if there are any technical reasons that I should be aware of.

---

### Post by orengolan on 2010-04-17
I didn't even know it support 64bit.

---

### Post by jackharvest on 2010-08-09
> **orengolan said:**
> I didn't even know it support 64bit.

Yeah, this little guy supports 64-bit right out of the box. Pretty surprising for it's size. Well worth the extra boost, since the 4100su processor utilizes it well.

---

