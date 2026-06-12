---
title: "Ubuntu on Dell laptops"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by conphara on 2007-08-13
Hi,

does anyone know (in details) how much work the Dell people have done to make Ubuntu work on their laptops. Because it would be awesome if they actually made Ubuntu work better (tweaking) than I would by a standard installation. For instance; is the battery life improved, how about fan control and so on......???

---

### Post by 1/0 on 2007-08-13
You can check what's supported [here]("http://www.linux-on-laptops.com/dell.html") or [here.]("http://tuxmobil.org/dell.html") I don't think they've done that much more than normal but instead chosen components that are supported so that way everything should work as it is supposed to. I know that they are starting to put preassure on the hardware suppliers to make better POSIX drivers.

There is an issue with hard drive drivers on laptops under linux. They wear out fast due to a signal at shutdown. This has been resolved as of  2.6.22. Just a minor note.

---

### Post by conphara on 2007-08-15
What is that about the hard drive driver issues. They wear out?

---

### Post by 1/0 on 2007-08-17
When the kernel kills all processes at shutdown it gives a pulse to the HD:s that's bad for them. It wears them out faster, so its been fixed as of 2.6.22. In Gentoo you would already be using 2.6.22 but in Ubuntu you'll have to wait until its stable (which is good). I think Ubuntu 7.10 is using 2.6.22.

---

### Post by standingfire on 2007-08-17
You should not have any problems with a L(attitude). I have a D610 that has been loaded with x(ubuntu) and has been that way for about 24 months. Wireless works, video works, the only item I have not gotten to work is the Palm hot sync. [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)
Talking
Other than that, the next bugaboo I need to work with is the Virtual Machine and I will run windows in it. That way it will not screw with my hardware.

---

### Post by Tsega on 2007-08-17
Hello People! I just wanted to know if the new Dell laptop with Ubuntu pre-installed is a good choice for someone who uses a dial-up internet connection. In short does it have a modem? I read on Dell  that it does have a modem but does Ubuntu recognize and use it?

---

### Post by phyrewall on 2007-08-20
> **Tsega said:**
> Hello People! I just wanted to know if the new Dell laptop with Ubuntu pre-installed is a good choice for someone who uses a dial-up internet connection. In short does it have a modem? I read on Dell  that it does have a modem but does Ubuntu recognize and use it?

If the laptop itself has a modem (which I don't see why it wouldn't), Ubuntu will recognize it. I've had no problems with the modem on m XPS.

---

### Post by Tsega on 2007-08-20
Thanks phyrewall I just needed to check that before I considered buying it.

---

### Post by bananskall on 2007-08-20
Hi! I can not order an Pre-installed Ubuntu from us.dell.com, because i live in norway. Also the keyboard layout would be weird. So i wonder: if i order one with vista, from a norwegian shop, and choose the same version laptop wich dell sells with Ubuntu on. Will it "just work" when i install from a downloaded image? Or does dell have specific drivers that i need, and wich are not included in Ubuntu?

Inspiron Notebook 1420 N
Intel® Core™ 2 Duo T5250 (1.5GHz/667Mhz FSB/2MB cache) (Will order 2.* GHZ, if ok.)
1GB1 Shared Dual Channel3 DDR2 at 667MHz (Will order 2GB, if ok.)
80GB2 SATA Hard Drive (5400RPM) (Will order 160GB, if OK)

..Is the one they sell on us.dell.com.

I need wireless to "Just work" too, because i need it in the classroom at school, wich started yesterday... not much time to debug.
Our school requires us to have a laptop, but we've been allowed to use other systems than windows (Great! they even teach OpenOffice and GIMP!). Support it! ;)

Will it Just Work?

---

### Post by timseal on 2007-08-20
> Will it "just work" when i install from a downloaded image? Or does dell have specific drivers that i need, and wich are not included in Ubuntu?
It probably will not "just work".  Dell has a few drivers that they supply with the 1420N.  One thing that doesn't work well is the video card, unfortunately.  (unless you get the nvidia option on the vista machine.)  After Gutsy is released, you should be OK though as those drivers should all make it in.

---

### Post by bananskall on 2007-08-20
Thank you

So, i'll look for one with intel cpu and nvidia graphics card. But what is the recommendation for Wifi? Is there an wifi device that will "Just work"?

Pardon if there is a list i should know of. Please point.

---

### Post by Tsega on 2007-08-25
> **bananskall said:**
> 
Pardon if there is a list i should know of. Please point.
 Check this like here, it's the list of all the laptops tested by Canonical and the Community.
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

