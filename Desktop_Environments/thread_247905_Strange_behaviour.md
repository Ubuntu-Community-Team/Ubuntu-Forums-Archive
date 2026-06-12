---
title: "Strange behaviour"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Jebenko on 2006-08-31
Hello,
  I have Kubuntu 6.06
   and I have a strange problem. Some apps like: xmms, firefox or konqueror randomly disappear/crash.  When i am surfing the web firefox just disappears like someone would  close it. Sometimes when xmms jumps from one MP3 to another it closes itself. And konqueror does the same if I for example move the mouse over some directories. It is random. I was till now not able to reproduce it. And I don't know where should I begin with the "investigation".  It might be also affecting other apps but I noticed it only by this 3. 

I suspected a bad RAM. Run memtest86 - no errors.   :sad:

Any suggestions?

---

### Post by 1800Zeta on 2006-08-31
I am having the same problem with firefox randomly closing.  I ran memtest for 13.5 hours and not one fault was found.  Using the latest download of Ubuntu and have all the available updates.

I have found this to happen with Igloo FTP as well

---

### Post by 1800Zeta on 2006-08-31
I have just had this happen on Mozilla as well.  I am a newbie to the Linux scene although I do have exposure to some older unix systems.

---

### Post by Jebenko on 2006-09-01
It seems to be app. independent. My DC++ client just crashed the same way. And again, it cannot be reproduced.   :sad:

---

### Post by gruffy-06 on 2006-09-01
I recommend updating your system if you haven't done so. Installing updates can improve over bugs and security flaws.

Make sure you have an active internet connection and run the following:
sudo apt-get update
sudo apt-get upgrade

If this is the first time you update and it says "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded", ensure that you have enabled the network software sources in Synaptic or Adept or by editing /etc/apt/sources.list.

---

### Post by amo-ej1 on 2006-09-01
open a terminal and take a look at the output of the 'dmesg' command, take a look at the bottom if you're not spotting any errors there.  Behaviour like this is typically cause by bad hardware ... but if memtest nor dmesg fails to show any kind of hardware failure it might be software but it's way easier to blame it on hardware ;-)

---

### Post by greg m on 2006-09-01
or in firefox extensions, do you have fireftp? if so remove it

---

### Post by Jebenko on 2006-09-01
I update my system regularly. Extra[]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") reposituries are enabled. I could not find any errors in dmesg. 
 Only this: 
dmesg | grep error
 [17179572.392000] ahci: probe of 0000:00:1f.2 failed with error -12

 The last crash with DC++ was the first that I could reproduce. If I started it again it crashed again right after a attempt to reconnect to a user. I turned on the DC++ option "Log system messages" but in the log was after the next crash nothing. After the fifth crash was all working fine again.
   I had today also 2 xmms crashes. 
Also from time to time crashes the KDE panel. I have to start it again with the "kicker" command.


My root fs is encrypted with LUKS according to this guide.
[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

Is it possible that there is some kind of a connection between this crashes and the fact that the file system is encrypted?

---

### Post by Jebenko on 2006-09-01
I have in the firefox extensions only adblock and some English language pack.

---

### Post by H.E. Pennypacker on 2006-09-03
I definitely have the Firefox problem.  For some weird reason, it disappears.  I have no idea why.  I wasn't doing anything weird before it closed.  It just closes.  I believe it is the only application which closes itself.  Can it at least tell me why? :(

---

