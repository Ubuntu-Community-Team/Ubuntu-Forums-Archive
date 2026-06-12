---
title: "XRDP XFCE Theme messed up"
date: 2014-05-26
forum: Desktop Environments
---

### Post by rompelstilchen on 2014-05-26
Hello,

[xubuntu 13.10]

first I could not connect with XRDP, so i found on the web I should uninstall it, install tightvncserver and reinstall xrdp
works fine but my theme is messed up/keyboard settings are wrong...

the theme looks like the one that is sometimes setup as i do a regular logon to my odroid screen
usualy i reboot a couple of times and the theme goes back to normal (wtf i dont know)

anyone had this issue ?

---

### Post by Toz on 2014-05-26
There is a bug with xfsettingsd in Xfce 4.10 (shipped with 13.10) that is fixed in 4.11 (shipped with 14.04). 
More info [here]("http://ubuntuforums.org/showthread.php?t=2202276&highlight=xfce+xrdp"), [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/354830") and [here]("http://forum.xfce.org/viewtopic.php?id=8603").

---

### Post by rompelstilchen on 2014-05-27
ok thanks :-)

---

### Post by rompelstilchen on 2014-05-27
I just checked, I already have version 4.11 installed
so back to square one, how could i fix this ?

i tried to add . /etc/profile at the top of /etc/xrdp/startwm.sh  
i also tried . /etc/environment but still the same issue

---

### Post by Toz on 2014-05-27
What version of xfsettingsd do you have:
```
xfsettingsd -V
```

Once connected via xrdp, can you run the following commands:
```
ps -ef | grep xfsettingsd
```
...and:
```
xfsettingsd --replace
```
...and post back any error messages.

IIRC, All I had to do was install xrdp and add:
```
startxfce4
```
...to my ~/.xsession file. I didn't fiddle with the startwm.sh file

---

### Post by rompelstilchen on 2014-05-27
v4.11


odroid@odroid:~$ ps -ef | grep xfsettingsd
odroid    3065  2901  0 16:39 ?        00:00:00 xfsettingsd --display :0.0 --sm-client-id 248a6a7dd-3f20-402b-8a36-18f08a6b0299
odroid    3755  3611  0 16:46 pts/0    00:00:00 grep xfsettingsd


xfsettingsd --replaceXlib:  extension "RANDR" missing on display ":10.0".


(xfsettingsd:3760): xfsettingsd-CRITICAL **: No RANDR extension found in display :10.0. Display settings won't be applied.
Xlib:  extension "XInputExtension" missing on display ":10.0".


(xfsettingsd:3760): xfsettingsd-CRITICAL **: XI is not present.


(xfsettingsd:3760): xfsettingsd-CRITICAL **: Failed to initialize the Xkb extension.


(xfsettingsd:3760): xfsettingsd-CRITICAL **: Failed to initialize the Accessibility extension.

---------------------------------------------

sorry for the bad editing but they keyb is messed up and copy paste dont work on rdp

---

### Post by rompelstilchen on 2014-05-27
i got xfce4-session in .xsession
anyway xfce is starting but with the wrong settings
it seems it cannot find RAND ...

---

### Post by Toz on 2014-05-27
> **rompelstilchen said:**
> v4.11


odroid@odroid:~$ ps -ef | grep xfsettingsd
odroid    3065  2901  0 16:39 ?        00:00:00 xfsettingsd --display :0.0 --sm-client-id 248a6a7dd-3f20-402b-8a36-18f08a6b0299
odroid    3755  3611  0 16:46 pts/0    00:00:00 grep xfsettingsd


xfsettingsd --replaceXlib:  extension "RANDR" missing on display ":10.0".


(xfsettingsd:3760): xfsettingsd-CRITICAL **: No RANDR extension found in display :10.0. Display settings won't be applied.
Xlib:  extension "XInputExtension" missing on display ":10.0".


(xfsettingsd:3760): xfsettingsd-CRITICAL **: XI is not present.


(xfsettingsd:3760): xfsettingsd-CRITICAL **: Failed to initialize the Xkb extension.


(xfsettingsd:3760): xfsettingsd-CRITICAL **: Failed to initialize the Accessibility extension.

---------------------------------------------

sorry for the bad editing but they keyb is messed up and copy paste dont work on rdp

This was the error I was getting in 13.10, but I don't get anymore in 14.04. Perhaps its not entirely an issue with Xfce but rather with Xfce's integration with X?

---

### Post by rompelstilchen on 2014-05-28
ok but who is dealing with this ? i dont understand there is no update/fix for this
the problem is that as it is an armhf platform, i cant install 14.04 wich is not yet available

---

### Post by Toz on 2014-05-28
There are existing bug reports [here]("https://bugzilla.xfce.org/show_bug.cgi?id=10342") and [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/354830").

I know that ran into this problem with 13.10, but it was fixed in 14.04. Sorry that I can't offer any more assistance.

---

### Post by rompelstilchen on 2014-05-28
no worries, you already helped me alot
maybe i should use gnome or kde for remote desktop, i'll have a look
thx

---

