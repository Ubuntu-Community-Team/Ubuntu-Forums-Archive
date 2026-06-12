---
title: "Ubuntu Hangs"
date: 2006-09-22
forum: Desktop Environments
---

### Post by carboto on 2006-09-22
It shows that Linux/Ubuntu can and does hang ... was just browsing the internet, then boom. No choice, but hard reset was the way to go.

---

### Post by lagagnon on 2006-09-22
[-X Did you try in this order before a hard reset:

1) xkill?
2) Ctrl-Alt-BkSp to kill X?
3) Ctrl-Alt-F1 to give you a virtual terminal in which to kill X?

---

### Post by carboto on 2006-09-23
I tried Clt+Alt+Backspace, but it still didn't work.

I am not aware of xkill and the clt+alt+f1 stuffs. How do you kill x by going to virtual terminal?

---

### Post by jegerjensen on 2006-09-23
You are not alone, carboto.

Today, I was like you just browsing and suddenly there no response whatsoever from my dapper laptop.  I couldn't even move the mouse, and there was no response from ctrl-alt-F1, ctrl-alt-del.  

Actually it was not so sudden, as I did experience a temporary freeze a few minutes before the final meltdown.  Also, two days ago I noticed similar behaviour and decided to do a reboot.  

I suspect this has to do with the recent kernel update, my kernel:
$ uname -a
Linux ubuntulaptop 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

In /var/log/messages I notice problems with ata2 and ipw2200, do you have similar errors, carboto?  What kernel do you use?

Below is an excerpt from /var/log/messages

cheers
Øyvind

```

Sep 23 13:33:22 localhost kernel: [17183693.428000] ata2: PIO error
Sep 23 13:33:55 localhost kernel: [17183725.448000] ipw2200: Firmware error detected.  Restarting.
Sep 23 13:33:55 localhost kernel: [17183725.448000] ata2: PIO error
Sep 23 13:33:55 localhost kernel: [17183725.484000] ata2: PIO error
Sep 23 13:33:55 localhost kernel: [17183725.484000] ata2: no sense translation for error 0x20
Sep 23 13:33:55 localhost kernel: [17183725.484000] ata2: no sense translation for status: 0x51
Sep 23 13:34:25 localhost kernel: [17183755.828000] ipw2200: Firmware error detected.  Restarting.
Sep 23 13:34:25 localhost kernel: [17183756.056000] ata2: PIO error
Sep 23 13:34:25 localhost kernel: [17183756.056000] ata2: no sense translation for error 0x20
Sep 23 13:34:25 localhost kernel: [17183756.056000] ata2: no sense translation for status: 0x51
Sep 23 13:34:25 localhost kernel: [17183756.412000] ata2: PIO error
Sep 23 13:34:25 localhost kernel: [17183756.412000] ata2: no sense translation for error 0x20
Sep 23 13:34:25 localhost kernel: [17183756.412000] ata2: no sense translation for status: 0x51
Sep 23 13:34:28 localhost kernel: [17183758.400000] ipw2200: Firmware error detected.  Restarting.
Sep 23 13:34:28 localhost kernel: [17183758.428000] ata2: PIO error
Sep 23 13:34:28 localhost kernel: [17183758.428000] ata2: no sense translation for error 0x20
Sep 23 13:34:28 localhost kernel: [17183758.428000] ata2: no sense translation for status: 0x51
Sep 23 13:34:28 localhost kernel: [17183759.032000] ata2: PIO error
Sep 23 13:34:28 localhost kernel: [17183759.032000] ata2: no sense translation for error 0x20
Sep 23 13:34:28 localhost kernel: [17183759.032000] ata2: no sense translation for status: 0x51
Sep 23 13:34:28 localhost kernel: [17183759.040000] ata2: PIO error
Sep 23 13:34:28 localhost kernel: [17183759.040000] ata2: no sense translation for error 0x20
Sep 23 13:34:28 localhost kernel: [17183759.040000] ata2: no sense translation for status: 0x51
Sep 23 13:34:28 localhost kernel: [17183759.100000] sr 1:0:0:0: Device not ready.
Sep 23 13:34:28 localhost kernel: [17183759.108000] sr0: unsupported sector size 50331648.
Sep 23 13:34:29 localhost kernel: [17183759.464000] ata2: PIO error
Sep 23 13:34:29 localhost kernel: [17183759.464000] ata2: no sense translation for error 0x20
Sep 23 13:34:29 localhost kernel: [17183759.464000] ata2: no sense translation for status: 0x51
Sep 23 13:40:27 localhost syslogd 1.4.1#17ubuntu7: restart.
Sep 23 13:40:28 localhost kernel: Inspecting /boot/System.map-2.6.15-27-686
Sep 23 13:40:28 localhost kernel: Loaded 23236 symbols from /boot/System.map-2.6.15-27-686.
Sep 23 13:40:28 localhost kernel: Symbols match kernel version 2.6.15.

```

---

### Post by bristleburger on 2006-09-23
I also had a hard lock: control/alt/backspace had no effect and it was not possible to ssh in from another host either.

You will see from the attached syslog excerpt that the trouble started at 10:32 and appeared to have something to do with IRQ5. I rebooted at 11:59.

---

### Post by mstrat on 2006-09-23
Yup...I've got the same problem.  I have noticed that it is only when on the internet, the computer slows to a crawl and then...nothing.

I noticed it starting after an update...sounds like xp?

---

### Post by carboto on 2006-09-23
Well, it hangs again and ctl+alt+f1 or backspace can't help.

It's a fresh install of Ubuntu with all codecs and non-free software installed. I don't know what kernel version it is, but I haven't updated anything. So, I am sure that the kernel is untouched and not the cause of the problem.

My laptop is a IBM ThinkPad, running the 32 bit version of Ubuntu Dapper Drake.

---

### Post by mmfbaig on 2007-09-20
I am also facing same problem, I have recently installed Ubuntu and facing an un- expected problem of hanging issue. Ubuntu hangs only while using key board whether I am using Internet or not but it hangs and I have to restart by pressing power key. I have tried CTRL+ALT+DEL but keyboard & mouse stops responding.

---

