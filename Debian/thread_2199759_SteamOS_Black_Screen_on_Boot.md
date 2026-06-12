---
title: "SteamOS Black Screen on Boot"
date: 2014-01-15
forum: Debian
---

### Post by King Dude on 2014-01-15
I've recently installed SteamOS on my friend's computer, and it ran "okay" initially (low frame rate and mysteriously dim screen), but after I ran ```
~/post_logon.sh
``` and rebooted it will only give me a black screen and hang until I power it of, which I then see a terms and agreements pop up for a brief second before powering off. My friend's computer is a **Sony VAIO ModelNum: SVF15N17CXB**.

Here are the hardware specifications for the laptop.
[https://docs.sony.com/release/specs/SVF15N17CXB_mksp.pdf](https://docs.sony.com/release/specs/SVF15N17CXB_mksp.pdf)

---

### Post by dannyboy79 on 2014-01-16
first of all what does ~/post_logon.sh script do? can you post it's contents on pastebin and then post the link here? also we really need to see the Xorg.0.log file to know what the error is. and maybe even ~/.xession-errors file as well. if you only have access to tty1 than you may be able to install pastebinit with 
```
sudo apt-get install pastebinit
```
then issue the following to upload the log file using 
```
pastebinit /var/log/Xorg.0.log
```
and
```
pastebinit ~/.xsession-errors
```

then write down the links it spits back at you and post those links here.

---

### Post by Elfy on 2014-01-17
*Thread moved to **Other OS/Distro Support**.*

---

### Post by King Dude on 2014-01-17
> **Elfy said:**
> *Thread moved to **Other OS/Distro Support**.*
Thank you.

> **dannyboy79 said:**
> first of all what does ~/post_logon.sh script do? can you post it's contents on pastebin and then post the link here? also we really need to see the Xorg.0.log file to know what the error is. and maybe even ~/.xession-errors file as well. if you only have access to tty1 than you may be able to install pastebinit with 
```
sudo apt-get install pastebinit
```
then issue the following to upload the log file using 
```
pastebinit /var/log/Xorg.0.log
```
and
```
pastebinit ~/.xsession-errors
```

then write down the links it spits back at you and post those links here.
I can't get to terminal anymore. It boots, I see the VAIO logo, then the Steam logo, and then it goes pitch black and hangs forever with no way of typing terminal commands. It doesn't even make it to the sign in screen.

~/post_logon.sh performs the post-install customizations, deletes itself, then reboots into the recovery partition capture utility. ([#9 on Custom Installation]("http://store.steampowered.com/steamos/buildyourown"))

---

