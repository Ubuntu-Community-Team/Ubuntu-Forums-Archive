---
title: "Trying to return to default Ubuntu login page after uninstalling Lubuntu desktop."
date: 2014-04-26
forum: Desktop Environments
---

### Post by Bill Grabowski on 2014-04-26
I successfully installed Ubuntu 14.04 64bit, and wanted to try the Lubuntu desktop as an alternate. I tried Lubuntu desktop, then uninstalled it, but now when I log out or reboot, instead of getting the default Ubuntu login page, I get a version of the Lubuntu login page, which I don't prefer. I have tried to remove all vestiges of Lubuntu using the Software Updater and Synaptic package manager, but this does not solve the problem. Short of reinstalling Ubuntu, what can I do?

Bill :(

---

### Post by deadflowr on 2014-04-26
Try this
```
sudo dpkg-reconfigure lightdm
```
at the page select lightdm and then ok.
Reboot.

---

### Post by Bill Grabowski on 2014-04-26
deadflowr,

Tried  [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure lightdm [/FONT][/COLOR]but did not get a page or option to select lightdm. After reboot, still had odd login screen.

Bill

---

### Post by deadflowr on 2014-04-26
By login page, do you mean the page you enter your password, or the page the comes up as it's booting?

---

### Post by Bill Grabowski on 2014-04-26
The page where I enter my password.

---

### Post by deadflowr on 2014-04-26
I wonder if you need to reinstall lightdm and unity-greeter.
Just a thought.

Don't know if this help but it might
[http://askubuntu.com/questions/371742/how-to-restore-ubuntu-login-screen-after-lubuntu-install](http://askubuntu.com/questions/371742/how-to-restore-ubuntu-login-screen-after-lubuntu-install)

---

### Post by Bill Grabowski on 2014-04-26
[SIZE=2][FONT=arial]Your suggestion pointed me to the solution. The problem was that **lightdm.conf** was still giving preference to Lubuntu. There was a directory [COLOR=#333333]/etc/lightdm/lightdm.conf.d containing a config file for lubuntu, which I removed. [/COLOR]So ...
[COLOR=#333333] 
             sudo gedit /etc/lightdm/lightdm.conf

...then enter:

[B][SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter[/B]

Save, exit, and importantly ... REBOOT. 

Before I did the above, I also did this ...

sudo apt-get purge lightdm
sudo apt-get install lightdm

... but I'm not sure that was really part of the solution.

Thanks for the help!!

Bill[/COLOR][/FONT][/SIZE]

---

