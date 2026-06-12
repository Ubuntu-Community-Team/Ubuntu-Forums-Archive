---
title: "why can't i get my visuals working?"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by horsy-raver on 2008-01-20
i've just done a dual-boot with vista and gusty and i can't get the visual effects to work, it's just says "desktop effects could not be enabled" when i try to activate them, i have looked at some other threads on this forum but they don't seem to help.

i am new to linux so it could be nothing wrong with my machine i just need a point in the right direction

cheers for your help

---

### Post by gspat on 2008-01-20
First off, we need to know some particulars... like what your  graphics card is.

---

### Post by Ub1476 on 2008-01-20
Post the output of this:

```
lspci | grep VGA

compiz
```

---

### Post by horsy-raver on 2008-01-20
graphics card: ATI Mobility Radeon X1300

"lspci | grep VGA" output:
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]

"compiz" output:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by sowelie on 2008-01-20
You need to ensure that you have the fglrx drivers installed.  And you'll also need to follow a guide to get xgl installed.

Check this guide out, should work in your situation:
[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200")

I think you need to install the xserver-xgl package first as well.

```
sudo aptitude install xserver-xgl
```

---

### Post by horsy-raver on 2008-01-20
kk, i got this out put with "sudo aptitude install xserver-xgl":
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "xserver-xgl"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done

---

### Post by horsy-raver on 2008-01-20
i still can't get anything to work, i just seem to be missing so many little bits that i can't follow any help guides. can somebody please help me through this step by step or i'm just gunna give up on Linux all together.

---

### Post by Ub1476 on 2008-01-20
Unfortunately your graphic card is [blacklisted]("http://ubuntuforums.org/showthread.php?t=582112"). You may use it at your own risk though. 

However, ATI has just released new drivers (for the first time in the Linux history..) and those might work better with Compiz-Fusion for your graphic card. [Envy]("http://albertomilone.com/nvidia_scripts1.html") can download and configure it for you. Those first (beta) drivers, lead to video corruption when using CF (visual effects), so you would have to disable CF if you want to watch movies.

After Envy has installed you can run it by typing:

```
envy -g
```

> kk, i got this out put with "sudo aptitude install xserver-xgl":
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "xserver-xgl"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done 

You have to enable more sources in System>Administration>Software-Sources (source-code is not needed). You do **not** need to download that package if you plan on using Envy.

---

### Post by horsy-raver on 2008-01-21
when i tried to install envy the status reads:
Error: Dependency is not satisfiable: xserver-xorg-dev

what does this mean?

---

### Post by sowelie on 2008-02-06
Sounds like you need the xserver-xorg-dev package.  Try installing it via:
```
sudo aptitude install xserver-xorg-dev
```

It sounds like you may also have a conflict, since envy is supposed to handle installing that stuff for you.  So, you may see a message that asks you to resolve the conflict.  Be careful, as sometimes this can lead to important packages being removed.  If you want, paste the output here and I'll let you know if it looks okay.  You can quit without committing the conflict resolution by hitting 'q' and enter I believe, it should tell you in the prompt.

---

