---
title: "Dell Mini 10v Touchpad"
date: 2009-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Greasy_Larry on 2009-08-05
I know I have posted a lot of questions in the last few hours, but I am trying to configure my new netbook properly. The touchpad is horrific on this .thing and I was wondering if anybody had any solutions. Whenever I left or right click the mouse jumps down or to the left or right. Often this results in me clicking on some stupid advertisment. I could not find a configuration setup. Anybody have a solution? Thank You

---

### Post by karamu on 2009-08-08
I can't confirm this will solve your problem because I haven't tried anything spoken about there, but here is a thread talking about this issue:

[http://www.mydellmini.com/forum/dell-mini-10v-discussion/9552-10v-linux-trackpad-driver-3.html](http://www.mydellmini.com/forum/dell-mini-10v-discussion/9552-10v-linux-trackpad-driver-3.html)

Hope that helps.

---

### Post by Tyrathect on 2009-09-20
Here's an easy to follow fix:

[http://ubuntuforums.org/showthread.php?t=1270382]("http://ubuntuforums.org/showthread.php?t=1270382")

---

### Post by Hosmion on 2009-09-20
Sorry to go off topic but there is touchpad laptops now??

---

### Post by fjgaude on 2009-09-21
> **Greasy_Larry said:**
> I know I have posted a lot of questions in the last few hours, but I am trying to configure my new netbook properly. The touchpad is horrific on this .thing and I was wondering if anybody had any solutions. Whenever I left or right click the mouse jumps down or to the left or right. Often this results in me clicking on some stupid advertisment. I could not find a configuration setup. Anybody have a solution? Thank You

Well, on my mini 10, there's an icon in the panel called "elan smart-pad" that permits configuring the touch control like you wish. It is extremely complex what with one, two, three, and four finger movements. I set mine to using just one finger, which is conventional for most laptops.

I can't remember, but the elan program was auto installed with the machine. I believe it's the program called **xserver-xorg-input-synaptics**, which is in the repositories.

There's also a program ready to install call **gsynaptics** that will do the same job as **elan**.

---

### Post by Tyrathect on 2009-09-21
The mini 10 has a different trackpad than the 10v.  The 10v has a multitouch pad with no buttons.  The bottom of the pad depresses to produce clicks.  It's a terrible idea, it makes it almost impossible to click small buttons, and without the patch, you can't hold the button down and drag something on the screen.

---

### Post by fjgaude on 2009-09-22
AFAIK, the mini 10 and the 10v have the same touch pad... my mini 10 doesn't have buttoms for left and right clicks, just one big pad. The config program permits you to set the pad up as you like it. Very advanced!

---

### Post by superm1 on 2009-09-22
> **fjgaude said:**
> AFAIK, the mini 10 and the 10v have the same touch pad... my mini 10 doesn't have buttoms for left and right clicks, just one big pad. The config program permits you to set the pad up as you like it. Very advanced!
No, actually the 10 has an Elantech touchpad and the 10v has a synaptics.  They're very similar looking hardware, but different functionality and configuration.

---

### Post by fjgaude on 2009-09-22
Elantech and Synaptics, eh? Wow, something new to learn each day. Thanks!

---

### Post by Zackez on 2009-11-21
Hi boys and girls, i'm borrowing this thread for a little while.

First of all, i'm totally new to linux, installed it yesterday. I have the Dell Mini 10v with XP installed, but i'm using ubuntu 9.10 "karmic koala remix" version for netbooks via Wubi. 
My touchpad works OK, but not perfect. The tap-function is not sensitive enough, and sometimes i have to tap it for a few times before it responds. I've tried varying the values under "mouse" without any luck.

Know a fix to this? I'd love any kind of help, since i'm a total newbie to linux..

Thanks

---

### Post by arm-c on 2009-12-13
UPDATE:  I have found that the successor to the gsynaptics program - gpointing-device-settings works to help address the touchpad problems.

You have to run it from the terminal, as there is not icon installed in the system menu.

activate the "enable faster tapping" option on the tapping tab.  If grayed out, ensure that the first tab has "touchpad on"

This seams to have addressed my primary issue with tapping.  

There might also be a problem with the "disable while typing" options causing a delay in tapping sensitivity... not sure.  But will play around with it more.  :)

---

### Post by orengolan on 2010-01-23
I am having the same problem with Dell Inspiron 11Z.
it also has Elan touchpad and I can't find a driver for ubuntu so I can configure it.

here is the driver for windows on dell's website:
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=dhs&catid=&impid=&os=WLH&osl=en&ServiceTag=CWWS1L1&SystemID=Inspiron1110](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=dhs&catid=&impid=&os=WLH&osl=en&ServiceTag=CWWS1L1&SystemID=Inspiron1110)

Here is a link to Elan's site - [http://www.emc.com.tw/eng/tpn_sp_fun.asp](http://www.emc.com.tw/eng/tpn_sp_fun.asp)
it say on their site that it's should work with linux.

I found this link - [http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)
and contacted the guy but got no reply.

I also contacted dell (chat) and they told me to contact Canonical using this number - 1-866-982-8688.
I called them but still got no reply.

Here is similar thread about this topic:
[http://ubuntuforums.org/showthread.php?t=1347942&page=2](http://ubuntuforums.org/showthread.php?t=1347942&page=2)

Elantech Touchpad Users Unit!
contact Dell, Elan and Canonical until they give us driver for this touchpad!

---

### Post by orengolan on 2010-01-25
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.

Thanks!

---

### Post by orengolan on 2010-04-11
I just upgraded to 10.4 and it was not fixed.
here are the 2 bug reports, please go there and add a comment with your machine etc.

[https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-input-evdev/+bug/123775](https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-input-evdev/+bug/123775)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192)

I also post it on kernel-team mailing list:
[https://lists.ubuntu.com/archives/kernel-team/2010-April/009826.html](https://lists.ubuntu.com/archives/kernel-team/2010-April/009826.html)

go there and reply, tell the developers it's a real issue.

Also go to #ubuntu-kernel on irc and ask about it.

---

