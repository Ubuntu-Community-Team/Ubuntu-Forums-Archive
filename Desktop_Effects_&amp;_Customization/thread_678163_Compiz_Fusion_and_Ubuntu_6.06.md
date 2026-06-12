---
title: "Compiz Fusion and Ubuntu 6.06"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by mariner8905 on 2008-01-25
I'm using an old Ibook G3 PPC with an ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (old i know) and i would like to get Compiz Fusion on my machine. so far ive followed the instructions on [this thread ]("http://ubuntuforums.org/showthread.php?t=515169") and ive gotten to the point of needing to logout and login to the session named "gnome with XGL' but when i try it boots me back out saying i didnt log out so there is something wrong with the installation. If anyone could help me get past this and get me up and running with Compiz Fusion i would greatly appreciate it. Im fairly new to linux so as much detail as you can give me would be great. if you need to know more let me know

---

### Post by Ub1476 on 2008-01-25
Is there any reason to run the LTS release? The next LTS release will be released in April, and Gutsy Gibbon (Ubuntu 7.10) is a very stable OS as well. It's **very** much easier to get Compiz working on Gutsy, so I suggest you use it. However, for getting XGL and Compiz on Edgy, look [here]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29"). You can drop everything related to "beryl" (I assume you will use Compiz-Fusion). In other words, make sure xserver-xgl is installed and start at "*Make a startup script for xgl*".

---

### Post by rosegarden78 on 2008-01-25
As far as I know Fusion works on a fresh install of Ubuntu GG 7.10.  You need to use Synaptic to add all packages with compiz except one.  That will ask you to remove compiz - don't use that package.  Install all the other compiz packages including compiz-kde.  Press Alt-F2 type compiz to restart.  I posted more detailed instructions [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").

---

