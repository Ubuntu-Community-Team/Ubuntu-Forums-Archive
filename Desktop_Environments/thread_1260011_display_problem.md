---
title: "display problem"
date: 2009-09-07
forum: Desktop Environments
---

### Post by levian on 2009-09-07
i installed ubuntu 9.04 days ago, with success installation of skype,  scim, a network printer, n updated all the items in "update manager". however, the screen is somehow, always distorted after a while the laptop is turned on. i tried changing the appearance n fonts rendering but failed to reduce the "defects". attached is the screenshot, it gets more serious if more are performed during one session. what should i do to fix this? thanks!

---

### Post by levian on 2009-09-07
attaching more screenshots.

---

### Post by levian on 2009-09-07
anyone else face this problem before?

---

### Post by overdrank on 2009-09-07
> **levian said:**
> anyone else face this problem before?

Hi and welcome, are you by chance using intel graphics on Jaunty? I have seen this issue on my son's laptop with Jaunty. If so you may look at the link in my signature about intel graphics in Jaunty.

---

### Post by levian on 2009-09-07
overdrank, thanks!

the laptop is a Pentium III, is it safe to assume that it is using Intel graphics? i looked at the link in your signature. do i have to follow all the instructions under Part A-D? sorry, i have very little linux knowledge.

---

### Post by overdrank on 2009-09-07
> **levian said:**
> overdrank, thanks!

the laptop is a Pentium III, is it safe to assume that it is using Intel graphics? i looked at the link in your signature. do i have to follow all the instructions under Part A-D? sorry, i have very little linux knowledge.

Hi and you can use the command in the terminal ```
lspci | grep VGA
``` and this will identify your hardware. The terminal is located under applications, accessories. I choose the Safe Configuration for my son's system. :)

---

### Post by levian on 2009-09-07
it returned:

```
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)
```

did you son's system tend to have words disappearing every now n then? i have to drag the window all around just to see the words, even in terminal.

---

### Post by levian on 2009-09-07
i tried Safe Configuration, but received an error message after line 2: 

```
$ sudo apt-get update
...
...
Reading package lists... Done
W: GPG error: httpL//ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23 BF810CD5
W: You may want to run apt-get update to correct these problems

```

what does it mean?

---

### Post by overdrank on 2009-09-07
> **levian said:**
> i tried Safe Configuration, but received an error message after line 2: 

```
$ sudo apt-get update
...
...
Reading package lists... Done
W: GPG error: httpL//ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23 BF810CD5
W: You may want to run apt-get update to correct these problems

```

what does it mean?
Hi and you will have to add the keys as the instruction direct.```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9

```

---

### Post by levian on 2009-09-07
i did. here is the ouput:

```
user@user-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

---

### Post by levian on 2009-09-09
i tried to change the fonts i used under System>Preferences>Appearance but it didn't work. i copied some .ttf from windows fonts into /usr/share/fonts/truetype/, again changed the fonts under Appearance, it didn't work too. any other ways can i try?

---

### Post by levian on 2009-09-13
reinstalling ubuntu 9.04 doesn't work either. the same problem appears in fresh installation. i don't understand what is the cause.

---

### Post by levian on 2009-09-28
i tried some more of the ubuntu based os - 9.04, 8.04, mint, fedora, etc. n still ended up with the same graphic problem like what i faced in my current 9.04. are there any other os that i should be trying?

the bug was found on launchpad as well: **[here]("https://bugs.launchpad.net/bugs/293059")**.

---

### Post by overdrank on 2009-09-28
> **levian said:**
> i tried some more of the ubuntu based os - 9.04, 8.04, mint, fedora, etc. n still ended up with the same graphic problem like what i faced in my current 9.04. are there any other os that i should be trying?

the bug was found on launchpad as well: **[here]("https://bugs.launchpad.net/bugs/293059")**.

Hi and 8.04 Hardy should work well with the intel graphics or at least it has for me. Have you checked the bios on the system to see how much memory is shared with the intel graphics.

---

### Post by levian on 2009-09-28
> **overdrank said:**
> Hi and 8.04 Hardy should work well with the intel graphics or at least it has for me. Have you checked the bios on the system to see how much memory is shared with the intel graphics.

how do i check the memory shared? i tried 8.04 n it lagged very bad.

---

### Post by overdrank on 2009-09-28
> **levian said:**
> how do i check the memory shared? i tried 8.04 n it lagged very bad.

Depending on the system, some use the F2 keys when booting to enter bios. It is sometimes displayed when the system is booting at the bottom of the screen. When in the bios you should be able to find and adjust the amount of memory shared with the graphics. What is the model of  the system.

---

### Post by levian on 2009-09-28
> **overdrank said:**
> Depending on the system, some use the F2 keys when booting to enter bios. It is sometimes displayed when the system is booting at the bottom of the screen. When in the bios you should be able to find and adjust the amount of memory shared with the graphics. What is the model of  the system.

it is an asus s1300. i should get into the bios n adjust the memory shared? is there a ratio or something that i should refer to? i am not quite following why.

---

### Post by overdrank on 2009-09-29
> **levian said:**
> it is an asus s1300. i should get into the bios n adjust the memory shared? is there a ratio or something that i should refer to? i am not quite following why.

Hi and yes there are some systems that will allow you to adjust the memory amount shared with the integrated graphics. Some system do this automatically when more memory is installed. How much memory is in the system now?

---

### Post by levian on 2009-09-30
> **overdrank said:**
> Hi and yes there are some systems that will allow you to adjust the memory amount shared with the integrated graphics. Some system do this automatically when more memory is installed. How much memory is in the system now?

it has 256mb RAM, so it is around 240+mb left.

---

