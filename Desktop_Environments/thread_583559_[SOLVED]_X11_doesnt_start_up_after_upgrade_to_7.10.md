---
title: "[SOLVED] X11 doesnt start up after upgrade to 7.10"
date: 2007-10-20
forum: Desktop Environments
---

### Post by ohwhatever on 2007-10-20
Upgraded from 7.04 to 7.10 using update manager on my Dell Inspiron 5100. After upgrade and restart, I can hear the Ubuntu drum roll but no screen. I typed my user id <enter> password on the blank screen and could hear the logon music but no screen yet. Rebooted and started in safe mode, tried startx, sudo startx and still no screen.
Also removed .ICEAuthority file from the home folder and rebooted. No luck.

Any suggestions? Help greatly appreciated! :confused:

---

### Post by tylerspaska on 2007-10-20
i have the exact same problem with the same dell model. i've tried 

sudo dpkg-reconfigure xserver-xorg

but the reconfigured monitor still doesn't display anything.

---

### Post by pbcartwright on 2007-10-20
can you reboot and at the blank screen hit :
CTRL-ALT-F1 ?
if this gets you to a text-based login prompt, then you have a video problem. More than likely an ATI or NVIDIA card..
if you look at your /etc/X11/xorg.conf file ( if you can login on the text- login screen)
if your device driver says : nvidia
if you can edit it using vi and change it to nv you will be able to log in.
then install envy or go to the NVIDIA web page and download the latest driver , red the HOW-TO and install it.

---

### Post by ohwhatever on 2007-10-20
Thank you for your time!
Yes I am able to get the text based login prompt and I see the following in the xorg.conf file:

Section "Device"
  Identifier "ATI Technologies...."
  Driver "ati"

What do I need to change "ati" to?

---

### Post by pbcartwright on 2007-10-20
I am not familiar with Ati cards, but this wiki seems to have the HOW-TO:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by ohwhatever on 2007-10-20
Thank you once again! Attempted the steps in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (Method 1).

I get the following errors in /var/log/Xorg.0.log
(EE) VESA(0): No vaild modes ...
....
(EE) Screen(s) found, but none have a usable configuration.

Any suggestions anyone? Thanks a lot for all help!

---

### Post by buster65 on 2007-10-20
I seem to be having a similar problem. I followed those instructions and the error i get is "cannot open display:0"

---

### Post by ohwhatever on 2007-10-20
> **ohwhatever said:**
> Thank you once again! Attempted the steps in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (Method 1).

I get the following errors in /var/log/Xorg.0.log
(EE) VESA(0): No vaild modes ...
....
(EE) Screen(s) found, but none have a usable configuration.

Any suggestions anyone? Thanks a lot for all help!
Also when I reboot after following the steps in the link, the start up seems to be stuck at :
* Running local boot scripts (/etc/rc.local)

---

### Post by ohwhatever on 2007-10-20
Searched for * Running local boot scripts (/etc/rc.local) in the forum and stumbled upon 
[http://ubuntuforums.org/showthread.php?t=581374](http://ubuntuforums.org/showthread.php?t=581374)

Tried sudo dpkg-reconfigure xserver-xorg, picked VESA and restarted gdm. I got a GUI!

Now off to solve network connectivity! (I am unable to connect to internet!)
Thanks everyone for all help.

---

### Post by ohwhatever on 2007-10-20
Network connectivity also fine. I had to restart then System > Network ...Wired connection was in Roaming mode. Unchecked roaming mode and voila..connected.

---

### Post by buster65 on 2007-10-20
Thanks alot it worked for me as well. my network works fine on the wired side but i'm having some issues with my wireless.

---

### Post by ohwhatever on 2007-10-21
You might want to check System>Administration>Restricted Drivers Manager. I beleive it detects your wireless chipset and allows you to download its firmware (if ur system doesnt have it already).

---

### Post by moose4204l on 2007-12-10
I did method 1 but where does the rest of the instructions pick up, where does method 2 end?

---

