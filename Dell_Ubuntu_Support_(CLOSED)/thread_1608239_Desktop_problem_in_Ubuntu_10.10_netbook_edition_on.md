---
title: "Desktop problem in Ubuntu 10.10 netbook edition on dell inspiron 6400"
date: 2010-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aref.Ariyapour on 2010-10-28
Hi guys

I am somewhat new to ubuntu. I have just installed Ubuntu 10.10 netbook edition on my Inspiron 6400, but there is a serious problem in my desktop. It doesn't properly show the taskbars on the left and top of the screen and instead of that it shows faded taskbars. Here are screenshots of my desktop:
[[IMG]http://imagenic.net/images/7pzv04whv2vpmo5sdm1s_thumb.png[/IMG]]("http://imagenic.net/viewer.php?file=7pzv04whv2vpmo5sdm1s.png")[[IMG]http://imagenic.net/images/aqog4c112dk4fdrwlsjc_thumb.png[/IMG]]("http://imagenic.net/viewer.php?file=aqog4c112dk4fdrwlsjc.png")[[IMG]http://imagenic.net/images/690wc43f32du919riw8_thumb.png[/IMG]]("http://imagenic.net/viewer.php?file=690wc43f32du919riw8.png")
I should mention that It works perfectly in desktop edition when I change the session in log in screen. There is no problem in desktop edition.
Can anyone please help me, to find out how should I fix this problem? I really want to experience the netbook edition, because I have heard so much about it.

Thanks so much

---

### Post by CoolJohnB on 2010-10-29
Try re-installing unity from Synaptic or software centre

---

### Post by Aref.Ariyapour on 2010-11-02
> **CoolJohnB said:**
> Try re-installing unity from Synaptic or software centre
Hi dear friend.
Thanks so much for your help. As you said, I tried to install all the packages related to unity, but I couldn't install one of them. It gives an error like this:

ubuntu-netbook-unity-default-settings:
 Depends: ubuntu-netbook-default-settings but it is not going to be installed

But  ubuntu-netbook-default-settings has been already installed.I also tried to re-install  ubuntu-netbook-default-settings package while installing ubuntu-netbook-unity-default-settings but it didn't work too.
Any further help?
Thanks so much

---

### Post by franckn on 2010-11-04
I have this exact same problem on a Compaq R4000. Have you found a solution yet?

---

### Post by Aref.Ariyapour on 2010-11-05
> **franckn said:**
> I have this exact same problem on a Compaq R4000. Have you found a solution yet?
Hi dear friend.
No I have not found yet. I am still seeking for a solution.

---

### Post by ijntema on 2010-11-05
Hi
I have same issue on a Medion E1315. I hope you find quickly a clue.
System has an ATI Radeon Xpress 1250 graphics - if it matters.

Cheers
Hans

---

### Post by kerry_s on 2010-11-05
make sure you have your drivers installed unity requires 3d acceleration.

try adding "export CLUTTER_VBLANK=none" to ~/.profile.

---

### Post by Aref.Ariyapour on 2010-11-08
> **kerry_s said:**
> make sure you have your drivers installed unity requires 3d acceleration.

try adding "export CLUTTER_VBLANK=none" to ~/.profile.

Hi dear Kerry. My system has ATI Radeom mobility x1400 and I have installed all the necessary drivers. I have also enabled all the desktop effects and they are running fine.

I added export CLUTTER_VBLANK=none to ~/.profile but nothing changed.

I hope someone can help us.
Thanks so much

---

### Post by CoolJohnB on 2010-11-09
At the moment the Netbook edition isn't all that good, there are several threads on this, probably best to stick to the desktop edition until the problems are ironed out.

---

