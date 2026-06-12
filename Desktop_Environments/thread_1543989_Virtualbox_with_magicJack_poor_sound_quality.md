---
title: "Virtualbox with magicJack poor sound quality"
date: 2010-08-01
forum: Desktop Environments
---

### Post by lbrty on 2010-08-01
I'm currently dual booting Ubuntu 10.04 and Windows XP (just for magicJack). I have installed Virtualbox and have created a Windows XP virtual machine. I plug in the magicJack and it installs, loads and gets a dial tone with no problems. Once I make a call, the sound quality is extremely poor on my end and the other person cannot hear me at all. I do not have this issue when I boot into Windows XP directly instead of using the Windows XP virtual machine with Virtualbox. 

Does anyone else have sound quality problems with magicJackin virtual machines? If so how did you solve the sound quality issue (on either Virtualbox or VMware)?

How do I install VMWare Server or should I install VMWare Player?

Thank you in advance for your help!

EDIT: ALL magicJack users please read the last post on the configuration setup.

---

### Post by lbrty on 2010-08-23
bump

Anyone?

---

### Post by georgemc on 2010-08-23
I'm on 10.04.1LTS and I use VMPlayer with a XP guest to run the Magicjack.
 

 About 6-7 months ago I tested (i.e. played around with) how the MJ performs in VBOX, VMWare, and the VMPlayer.
 

 I found that VBOX has really bursty network transmission (haven't tried lately) and I couldn't figure out how to correct that.  With Vmware and VMPlayer the network transmissions are smother.
 

 I prefer VMPlayer over the Vmware because of the UI.
 

 I have a Cisco RVS4000 router and in the &#8220;QoS&#8221; > &#8220;Bandwidth Management&#8221; section set the UDP/TCP ports 5060 & 5070 up/down stream to the highest priority.  Not sure if this helps a lot.
 

 Here's a link to the Vmplayer download.  I think you need to register to activate it.
 

 [http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0](http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0)
 

Every now and then I need to restart the XP guest because the MJ acts up.  Other than that it runs 7/24 and the phone quality is ok.



 Hope this helps.
 

 George

---

### Post by lbrty on 2010-08-23
Thanks for the reply georgemc! 

I downloaded VMWare Player and it has a .bundle extension. I tried running and it did not work. I then tried converting the package to a .deb file with alien and it did not recognize the .bundle file. How did you install VMWare Player? Thanks!

---

### Post by georgemc on 2010-08-24
Hmmm – looks like the “Start Download Manger” button on the website down loads a HTML and not a binary.  Try the “Manual Download” and save the file to a directory and then verify the check sum with md5sum.
 

 The file should be on the order of 105MegBytes.
 

 I then make it executable “chmod +x <filename>” in a terminal and run it.  
 

 George

---

### Post by lbrty on 2010-08-24
Thanks again George! I really appreciate it! I couldn't figure out how to run it until I found this thread:

[http://ubuntuforums.org/showthread.php?t=841441](http://ubuntuforums.org/showthread.php?t=841441)

Once I ran this command:
```
chmod +x <filename> 
```to make the file run, it would state I needed root access. 

So I entered: 
```
sudo -i
```and then
```
./<filename>.bundle
```and it worked!

Thanks again for all your help!

---

### Post by lbrty on 2010-08-24
After I installed VMWare Player, I installed WinXP to test the magicJack for sound quality and it works perfectly! VMWare Player is perfect for magicJack users and there no sound quality issues!

For you magicJack users, problem solved!
My configuration below:

Ubuntu 10.04 LTS Lucid Lynx
VMWare Player
Install Windows operating system within VMWare Player (in my case Windows XP)
Plugin in your magicJack and your ready to make calls!

Thanks again George!

---

### Post by georgemc on 2010-08-24
Glad you got it work and I am happy to help.

George

---

