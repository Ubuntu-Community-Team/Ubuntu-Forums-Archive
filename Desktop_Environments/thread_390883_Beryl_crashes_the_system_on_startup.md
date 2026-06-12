---
title: "Beryl crashes the system on startup"
date: 2007-03-22
forum: Desktop Environments
---

### Post by pillu on 2007-03-22
Hi all,

I installed Beryl on my Kubuntu 6.10 Edgy laptop (intel centrino duo with i945 on board graphics and 1 GB RAM) using the instructions for AIGLX. It seemed to work well without any problems. Then I tried to get beryl as an option on startup following this link
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl)

Now when I startup I do not get a login screen. The screen just freezes and then it shows my the tty1 login screen. Switching to tty7 shows me just a blinking cursor. When I login to tty1 and type the startx command, it throws up a bunch of errors and doesn't start the x server.

Thinking that it was beryl causing all these problems, I deleted /usr/bin/startberyl.sh file. But still it does the same thing. Note that I still haven't deleted the /usr/share/xsessions/Beryl.desktop file.

A possible source of the problem might be my kde settings that are causing this weirdness to happen. In my settings in kde, I had my splash screen selected as NONE. It didn't do anything earlier but it might be the problem now.

Please give any suggestions for salvaging my desktop without reinstalling everything. If you think that the splash screen is the problem then is there any way to change it in a plane jane bash command prompt ? I wouldn't mind just reverting to the kde desktop and starting beryl manually everytime. Eagerly waiting for replies.

Pillu

---

### Post by Waappu on 2007-03-22
Hi

Login tty1 and try to find startup programs.

In gome
```
~/.config/autostart
```
KDE
```
~/.kde/Autostart
```

Ps: nice alias you have =)

---

### Post by pillu on 2007-03-22
> **Waappu said:**
> Hi

Login tty1 and try to find startup programs.

In gome
```
~/.config/autostart
```
KDE
```
~/.kde/Autostart
```

Ps: nice alias you have =)

~/.kde/Autostart is empty except for a .directory which I don't know what to do with..Any other suggestions ?
I am going to try /etc/init.d/kdm start and see if it works

Glad u like my alias...yours isn't too bad either

Pillu

---

