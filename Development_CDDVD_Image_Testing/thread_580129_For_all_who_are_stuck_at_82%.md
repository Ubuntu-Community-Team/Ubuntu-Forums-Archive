---
title: "For all who are stuck at 82%"
date: 2007-10-18
forum: Development CD/DVD Image Testing
---

### Post by evilc on 2007-10-18
If you find when installing Gutsy you get stuck/frozen at about 82% on your panel bar disable your network connection (temporary). After it tells you it's added to sources list you can reconnect it, I think the problem is the servers are overloaded/down and it can't get the updates.
I found it best to disconnect after files installed (about 79%) that way if you have a finicky network it has by then seen it and installed the required files.

---

### Post by xc3RnbFO8P on 2007-10-18
I had this problem, so I started Synaptic Package Manager and change mirror from USA to Denmark and it took 15 min untill it started again.

---

### Post by MasamuneX on 2007-10-18
I just let it sit for a couple of minutes and then moved the window around on screen (as in clicking the window border and dragging it around the desktop).  This was after several minutes and suddenly it picked right back up.

---

### Post by jerrylamos on 2007-10-18
Stuck at Configuring apt, 82%, scanning the mirror.  Forever.

Forums to the rescue again.  Changing Synaptic to point to Denmark worked.  Just for giggles I tried a reload but that didn't quite finish before it hung.  Install worked fine.

Usual Ubuntu bugs but that's another post.

Thanks much!  Jerry

---

### Post by xc3RnbFO8P on 2007-10-19
> **jerrylamos said:**
> Stuck at Configuring apt, 82%, scanning the mirror.  Forever.

Forums to the rescue again.  Changing Synaptic to point to Denmark worked.  Just for giggles I tried a reload but that didn't quite finish before it hung.  Install worked fine.

Usual Ubuntu bugs but that's another post.

Thanks much!  Jerry
 This is not a bug, just heavy traffic on server. You should change it back to the server nearest to you.

---

### Post by FredB on 2007-10-19
Yes. Servers are under an heavy "attack" from upgraders and clean installers.

All will be ok in a few days.

---

### Post by quique1hn on 2007-10-19
Tank's for that that's why I needed:guitar:

---

### Post by malagent on 2007-12-08
Configuring the Apt
82%
scanning the mirror"

Is driving me freaking insane...

Been trying this off and on for a week now.
Changing servers does not good for. Left it for 2 days and still "82% scanning the mirror". Disabling network prior to 82% results in a message stating some security updates were unable to be installed, you should investigate this later. When I click OK the button depresses and that's it - It just sits there forever from that point.

And of course as my luck would have, upon restart the Windows Vista partition is inaccessible as well. It's still there, it just wont boot the evil OS under any circumstances. I think if I can get Ubuntu to get past 82% and install then the evil Vista partition should be accessible as well, If not I'll just have to sit through the mind numbing install process for that too. :confused:

---

### Post by yesha243@aol.com on 2008-12-10
hey im having the same problem with the 82% thing. Just wondering if there were any updates on the situation and if anyone has any further advice since the 8.10 update. Thanx in advance.

---

### Post by vishalrao on 2008-12-23
it is for such reasons (my net connection is also slow) that i usually disconnect the LAN cable during install so it moves along.

if not already done, should we file a bug/wishlist to have the installer ask/prompt to go online (if it detects a connection) before attempting it?

---

### Post by vishalrao on 2008-12-25
> **vishalrao said:**
> if not already done, should we file a bug/wishlist to have the installer ask/prompt to go online (if it detects a connection) before attempting it?

Found a bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/294523](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/294523)

---

### Post by obscur156 on 2009-02-24
I had similar problem with jaunty alpha 4 and it gave me a big error message= maybe a bad iso,maybe a damaged cd,badly burned and even saying that its too hot and that i might move the computer in a cooler place.

MD5SUM is ok and cd too.

So i got a big fan that i am using when its hot in the house,put it in front of the open casing of my pc.I restart the installation and it completed without any problem.

It did that for my 2 pc that i have.So i am wondering if it can be the cdrom overheating when copying files?

Maybe i am wrong but just thought I'd toss that out there.
Regards

---

### Post by tmairs on 2009-02-27
Unplug your network cable.  I have built Ubuntu 20 times on virtual machines and every time I get stuck at this point.  Disconnecting the network adapter ( unplugging the cable) lets the install finish.

---

### Post by vkcooke90 on 2009-07-29
> **yesha243@aol.com said:**
> hey im having the same problem with the 82% thing. Just wondering if there were any updates on the situation and if anyone has any further advice since the 8.10 update. Thanx in advance.

If your installing 9.04 and this thing happens where it gets stuck at 82%, just move the box around the screen, and if that doesnt work then just minimize the window and bring it back up, if your using a PC for the ubuntu computer use CTRL+TAB and if your installing ubuntu on a Mac use control(NOT COMMAND OR APPLE KEY)+tab.

---

