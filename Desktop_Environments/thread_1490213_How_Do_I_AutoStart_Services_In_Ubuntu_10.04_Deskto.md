---
title: "How Do I AutoStart Services In Ubuntu 10.04 Desktop?"
date: 2010-05-22
forum: Desktop Environments
---

### Post by matthodge on 2010-05-22
I have installed a fresh copy of Ubuntu 10.04 Desktop x64. It is running desktop with XBMC plugged into my TV, but is also used as a server.

I have installed several packages including
- xinetd (for GLFTPD)
- webmin
- VirtualBox
- NXServer

When I reboot the system, none of the applications automatically start.

I have to ssh into the box and run:
sudo /etc/init.d/xinetd start
sudo /etc/init.d/webmin start

etc for each application I want to start.

How do I start applications automatically in Ubuntu 10.04? Do I have to use upstart?

I usually use webmin to set my services to autostart but with upstart it doesn't work anymore.

Thanks.

---

### Post by ls8_ on 2010-05-22
This is my first post so it might not help you at all.

Start a terminal, ```
$ gnome-session-properties
```then add the programs.

---

### Post by matthodge on 2010-05-22
Thanks ls8.

I was hoping there would be a way to add them from the command line though.

---

### Post by hok00age on 2010-05-22
> **matthodge said:**
> Thanks ls8.

I was hoping there would be a way to add them from the command line though.

try using modconf

---

### Post by matthodge on 2010-05-22
Can you please elaborate? Modconf seems to be a driver installer:

[http://packages.ubuntu.com/hardy/modconf](http://packages.ubuntu.com/hardy/modconf)

---

### Post by exactt on 2011-01-19
i case somebody wants to know the answer:

try something like this:

```
update-rc.d tomcat6 enable 2
```

this automatically starts(enables) tomcat6 in runlevel 2.

---

### Post by crtlbreak on 2011-01-22
> **exactt said:**
> i case somebody wants to know the answer:

try something like this:

```
update-rc.d tomcat6 enable 2
```

this automatically starts(enables) tomcat6 in runlevel 2.

Hi exactt, 
not sure I understand you - are you saying he should start the modconf in runlevel 2 as you had started your tomcat6?

Suggested [assumption code] ```
 sudo update-rc.d modconf enable 2
```

---

### Post by exactt on 2011-01-24
I was referring to the original post regarding

- xinetd (for GLFTPD)
- webmin
- VirtualBox
- NXServer

Put them in place for tomcat6 . Regarding the appropriate runlevels I am actually not 100% sure...

```
sudo update-rc.d xinetd enable 2
```

---

### Post by HandeH on 2011-02-03
I have succeeded to run scripts and start applications by [gnome-schedule]("apt://gnome-schedule") or by putting into gnome-session-properties a quoted command starting with bash -c, like this way: 
```
bash -c "rm -rf ~/.macromedia/Flash_Player/#SharedObjects/*"
``` as suggested [here]("http://ubuntuforums.org/showpost.php?p=10120454&postcount=4"). 

There is also another fresh [thread]("http://ubuntuforums.org/showthread.php?p=10423781") on this issue. And some bug reports: [460746]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/460746"), [518740]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/518740"). Consider to mark those affecting you also.

---

