---
title: "wrong keyboard layout"
date: 2005-11-29
forum: Desktop Environments
---

### Post by sigmar on 2005-11-29
Hi.

I upgraded to breezy and since then the keyboard acts like english one, despite that layout is set to estonian. But I need it to be estonian. I thought that I did something wrong during upgrading and so I made new clean install, but the problem exist ](*,)

Any ideas?

---

### Post by syd2o2 on 2005-11-30
I have the same problem. I need the language set to Bosnian, but the layout stays English, even after I removed English from the keyboard layout selector. I tried some other languages, and the layout always stays english.

---

### Post by sigmar on 2005-12-01
Doesn’t anybody know this?

---

### Post by teaker1s on 2005-12-01
sudo dpkg-reconfigure xserver-org

failing this check out this bug



[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963)[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963")

---

### Post by sigmar on 2005-12-01
I tried but the result was: 
xserver-xorg config warning: failed to infer keyboard layout from layout/lang
   'et--et_EE'

What does this means?

I have ee keyboard configuration file in etc/X11/xkb/symbols and also in xorg.conf the XkbLayout is ee, but...

---

### Post by LadyLuck on 2005-12-01
[QUOTE=sigmar]Hi.

I recently installed breezy and since then the keyboard acts like english one, despite that layout is set to estonian. But I need it to be estonian. I thought that I did something wrong during upgrading and so I made new clean install, but the problem exist ](*,)

Any ideas?[/QUOTE]

Hi
Being a newbie myself I had the same problem when I installed. My keyboard layout was US English although I specifically chose another flavour. By sheer luck I stumbled on Keyboard under Preferences in the System menu (Desktop). There one can choos keyboard layout and activate it. 

(However writing this email I have come across one key that is not working properly. Hm)

cheers
LL

---

