---
title: "Starting compiz fusion help"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by shaan.mi on 2007-07-25
Hi, when i enter compiz --replace & in the terminal it gives me an error saying this : shaan@shaan-desktop:~$ Fatal: Failed test: texture_from_pixmap support 
Checks indicate that it's impossible to start compiz on your system ! My video card is an ati x1900 with 256mb of  graphics ram. My processor is a core 2 duo. Thanks in advance. I have everything installed. But it wont start.

---

### Post by michael37 on 2007-07-25
> **shaan.mi said:**
> Hi, when i enter compiz --replace & in the terminal it gives me an error saying this : shaan@shaan-desktop:~$ Fatal: Failed test: texture_from_pixmap support 
Checks indicate that it's impossible to start compiz on your system ! My video card is an ati x1900 with 256mb of  graphics ram. My processor is a core 2 duo. Thanks in advance. I have everything installed. But it wont start.

There are many reasons for this error message, most of them related to graphics drivers and their options.  Are you using ATI binary driver?  Have you read through FAQs for the xorg.conf details before getting compiz worknig?

My favorite faq is [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl).  It's pretty much the only one that works well for ATI cards.

---

### Post by shaan.mi on 2007-07-25
My video card is an ati x1900. all what I did for drivers was to enable the ati accelerated driver in restricted drivers manager. I dont know what "xorg.conf" is. Can you help me out?

---

### Post by shaan.mi on 2007-07-25
i have xorg  installed but the terminal still gives  me the  same error!

---

### Post by michael37 on 2007-07-25
> **shaan.mi said:**
> i have xorg  installed but the terminal still gives  me the  same error!

xorg.conf is the master configuration for your X server.  You can't get compiz running properly if you don't get Xgl running first!

So, where is xorg.conf?  In /etc/X11/xorg.conf.  Open a terminal and run command
```
grep fglrx /etc/X11/xorg.conf
```

Your output should be:
```
        Driver          "fglrx"
```

Then, run command 
```
ps -ef | grep X | grep -v grep
```

Your output should contain words Xgl and Xorg.  Here is how mine looks:
```

root      4974  4970  1 19:54 ?        00:02:37 /usr/bin/Xgl :1 -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer -dpi 100 -nolisten tcp -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt7
root      4988  4974  0 19:54 tty7     00:00:08 /usr/bin/Xorg -br vt7 -auth /tmp/.Xgl-auth-2zQJ3w -nolisten tcp :94 -terminate

```

Keep in mind that all Linux commands are case sensitive.

---

### Post by shaan.mi on 2007-07-25
Here is mine, is this good or bad

shaan@shaan-desktop:~$ ps -ef | grep X | grep -v grep
root      5453  5452  0 20:02 tty7     00:00:10 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

---

### Post by michael37 on 2007-07-26
> **shaan.mi said:**
> Here is mine, is this good or bad

shaan@shaan-desktop:~$ ps -ef | grep X | grep -v grep
root      5453  5452  0 20:02 tty7     00:00:10 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Bad.  You don't have Xgl working.

Please retry the instructions in the Xgl document: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

I recommend using Method B, follow careful directions for ATI video cards (they are DIFFERENT from instructions for Nvidia and Intel cards).

Also, did the grep fglrx give you expected output?

---

