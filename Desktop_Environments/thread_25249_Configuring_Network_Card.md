---
title: "Configuring Network Card"
date: 2005-04-09
forum: Desktop Environments
---

### Post by giorgosc61 on 2005-04-09
Hello,
I just installed KUBUNTU and I have the problem to set the network card settings.
Every time I boot I have to enter in konsole
su
******** (my password)
ifconfig eth0 192.168.1.2 broadcast 192.168.0.255 netmask 255.255.255.0 up
route add default gw 192.168.1.1
nano -w /etc/resolv.conf
nameserver 193.92.150.3
nameserver 194.219.227.2

and only then I can have internet access through my adsl router.
Can someone tell me is there something I can do so I don't have to enter these on every boot??

Thank you in advance.

---

### Post by edubarr on 2005-04-09
Have a look at the interfaces man-pages (man interfaces). It should be able to help you with your problem.

---

### Post by poofyhairguy on 2005-04-09
[QUOTE=giorgosc61]
Can someone tell me is there something I can do so I don't have to enter these on every boot??

Thank you in advance.[/QUOTE]

Make a script for it and make it load on startup!

---

### Post by giorgosc61 on 2005-04-10
I think I found some kind of solution.
I accessed Control Center -> Internet & Network -> Network Settings -> Administrator Mode
and manually entered the settings there.
I clicked apply in the first and third tab but forgot to apply the second tab (default gateway).
The problem is now in every boot i have to enter in konsole 
route add default gw 192.168.1.1

I tried to access administrator mode in Control Center again but there seem to be a bug that doesn't let me enter administrator mode after password in Control Center in general now.
If there is a way to access the network settings in Control Center under administrator I could enter the setting and everything will work fine.
(Note that the password that worked the first time in administrator mode was the user passwd and not the passwd the root user that i have created has)

Please help me  ](*,)  .

---

### Post by Jonathan2007 on 2005-04-10
I also had a similar issue yesterday. Many things in Kubuntu seem to be quite unstable. I was attempting to give my pc a static ip address instead of using DHCP and I never got it working. I changed some settings using the KDE Control Center. I had to go into administrator mode. When I tried to get into this later I was unable to. It would just load the list of all the different modules I could get into using the KDE Control Center. I eventually had to do a "kcmshell --list" in konsole. This gave me a list of all the different modules I could pull up. I then used "kcmshell kcm_knetworkconfmodule". This opened up just the Network config dialog. I had to resize it to see the administrator mode button. I tried it and it logged in fine. I later tried to adjust my network settings again and still couldn't get into. I then tried the "kcmshell kcm_knetworkconfmodule" and tried to login using the administrator mode. Guess what it didn't work. I was flabergasted (sp?). I couldn't believe it. So using my little but growing linux knowledge I used the command "sudo kcmshell kcm_knetworkconfmodule". And it worked and I didn't need to enter administrator mode as the app was already running as root. The funny thing is when I try to run Kcontrol as root ("sudo kcontrol") I get this error.

Error: "/var/tmp/kdecache-jonathan" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.

Kcontrol opens for a second but then closes real quick. Well anywho that should solve your problem giorgosc61. And if anyone knows why kcontrol crashes when it tries to run as sudo please post.

P.S. Later yesterday night I tried running Kcontrol reguarly and I got into the administrator mode somehow. Crazy things.  :shock:

---

### Post by vltakacs on 2006-06-28
Dear Staff,

I am using Ubuntu 6.06 with KDE and I am having similar problems.
Every time I start up my computer I have to load the correct profile using the Network Settings module (#kcmshell kcm_knetworkconfmodule) Unless, i have no internet connection. Why can't I set it to be loaded automatically upon startup?

Regards,

Viktor L. Takacs

---

