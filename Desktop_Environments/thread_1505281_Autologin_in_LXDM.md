---
title: "Autologin in LXDM"
date: 2010-06-09
forum: Desktop Environments
---

### Post by beastrace91 on 2010-06-09
Howdy All,

I was wondering how I can toggle auto-login while using LXDM. I add the line ```
[base]
autologin=jeff
``` to my **/etc/lxdm/lxdm.conf** file but that did not do the trick.

What do I need to do to enable auto login?

Per advice I found [here](http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html) for Lubuntu I also added the above line to my **/etc/xdg/lubuntu/lxdm/lxdm.conf** and it still does not auto log in for me :-/

~Jeff

---

### Post by cavalier911 on 2010-07-06
My configuration to turn on numlock wasn't working.Edited both files you indicated identical but lxdm wasn't reading the configuration.The first time I ran the command for update-alternatives there was no current choice indicated with an asterisk.I choose 0, the asterick showed when I ran the command again.I rebooted and my numlock light came on.

There is more details in _man lxdm_ and _man update-alternatives_


```
sudo update-alternatives --config  lxdm.conf
```

There are 2 choices for the alternative lxdm.conf (providing /etc/lxdm/default.conf).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        auto mode
  1            /etc/lxdm/lxdm.conf               50        manual mode
  2            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        manual mode

Press enter to keep the current choice[*], or type selection number:

---

### Post by SteveDee on 2010-10-29
With Lubuntu 10.10 it now seems that you only need to change: /etc/xdg/lubuntu/lxdm/lxdm.conf

```

[base]
autologin=steve

```

---

### Post by xepe on 2010-10-31
> **SteveDee said:**
> With Lubuntu 10.10 it now seems that you only need to change: /etc/xdg/lubuntu/lxdm/lxdm.conf

```

[base]
autologin=steve

```
I changed /etc/xdg/lubuntu/lxdm/lxdm.conf and got an Xsession error, I think lxdm is looking for a gnome session

---

### Post by SteveDee on 2010-11-01
> **xepe said:**
> I changed /etc/xdg/lubuntu/lxdm/lxdm.conf and got an Xsession error, I think lxdm is looking for a gnome session

Oh, that's odd. I've only tried this on one Lubuntu system, which has a pretty clean install, and as I said I only need to change one copy of lxdm.conf.

However, I have another computer where I selected auto login during install, and just checking this, I see both copies of lxde.conf are identical. So the safest advice is probably to keep the 2 conf files the same.

---

### Post by lordyarox on 2010-11-03
I recovred my password here to post what worked for me. I just installed lxde on my server (need it for a gui hava app) and I too needed it to auto log-in.

Add autologin=username to the first line of base in /etc/lxdm/default.conf

Good luck!

---

### Post by dabbi2000 on 2010-11-29
is there any way to select a user by default, without auto-login?

(that is only having to write the password)

---

### Post by beastrace91 on 2010-11-29
> **dabbi2000 said:**
> is there any way to select a user by default, without auto-login?

(that is only having to write the password)

Not currently.

~Jeff

---

### Post by AugustinMa on 2011-03-10
I have summarized some of this information in this tutorial:
[http://linux.overshoot.tv/wiki/system/desktop_auto_login](http://linux.overshoot.tv/wiki/system/desktop_auto_login)

I still have some pieces missing (See: [http://ubuntuforums.org/showthread.php?t=1703824](http://ubuntuforums.org/showthread.php?t=1703824) ), so if you have more information to complete the article, let me know.

Thanks.

---

### Post by n8bounds on 2011-07-04
LXDM supports themes:
[http://blog.lxde.org/?p=595](http://blog.lxde.org/?p=595)

And I'd like one that supports a user list, although I'm not the first to think of this:
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590)
 -&-
[http://forum.lxde.org/viewtopic.php?f=8&t=1953](http://forum.lxde.org/viewtopic.php?f=8&t=1953)

Maybe I could rip one off another distro? Does anyone know of another LXDE-based distribution that already has a LXDM theme with user list support?

---

### Post by zipizap on 2012-06-26
Ubuntu Server 10.04.4 LTS, with LXDE installed manually - to enable autologin, I had to do 2 steps:

1) add a new line "autologin=yourUserName" just after the "[base]" line
```
sudo nano /etc/lxdm/lxdm.conf
``` 


2) Run the following, to use the configuration changes made in 1)
```
sudo update-alternatives --config lxdm.conf
```

Next time you reboot, lxdm will do autologin and send you straight to the desktop session

---

