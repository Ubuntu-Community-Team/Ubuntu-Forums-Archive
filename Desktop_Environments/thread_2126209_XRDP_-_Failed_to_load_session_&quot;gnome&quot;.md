---
title: "XRDP - Failed to load session &quot;gnome&quot;"
date: 2013-03-16
forum: Desktop Environments
---

### Post by victorhooi on 2013-03-16
Hi,

I've installed a Ubuntu 13.04 desktop, and added Gnome 3 by following:

[http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html](http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html)

I've also installed xrdp and now I'm trying to connect to my desktop from another box using FreeRDP.

I can login to Gnome-shell fine from the local session. Xrdp however, doesn't seem to work.

My ~/.xsession contains:

```
exec gnome-session --session=gnome
```

(I've also tried with just exec gnome-session).

I can get a Xrdp graphical login screen, however, when I try to login, I get:

```
Failed to load session "gnome"
```

and a "Log out" button.

I checked /var/log/xrdp-sesman.log, and I didn't really see much useful:

```
[20130317-01:06:54] [INFO ] scp thread on sck 7 started successfully
[20130317-01:06:54] [INFO ] ++ created session (access granted): username victorhooi, ip 192.168.4.6:59389 - socket: 7
[20130317-01:06:54] [INFO ] starting Xvnc session...
[20130317-01:06:55] [INFO ] starting xrdp-sessvc - xpid=5495 - wmpid=5494
[20130317-01:06:58] [INFO ] ++ terminated session:  username victorhooi, display :11.0, session_pid 5493, ip 192.168.4.6:59389 - socket: 7
[20130317-01:11:58] [INFO ] scp thread on sck 7 started successfully
[20130317-01:11:59] [INFO ] ++ created session (access granted): username victorhooi, ip 192.168.4.6:60005 - socket: 7
[20130317-01:11:59] [INFO ] starting Xvnc session...
[20130317-01:11:59] [INFO ] starting xrdp-sessvc - xpid=5594 - wmpid=5593
```

The LogLevel is set to DEBUG in /etc/xrdp/sesman.ini, so I was hoping it'd log more.

Does Xrdp log more somewhere else as well?

Any idea on what might be causing this issue? (I note that Winswitch also seems to give a similar error when I try to start a gnome-shell session).

Cheers,
Victor

---

### Post by WasMeHere on 2013-03-16
I don't use gnome but Lubuntu with xubuntu-desktop, and then it connects with the xfce desktop when running ***xrdp*** and connecting with ***rdesktop*** from another Ubuntu computer. See the attached dump of the rdesktop window.

*Edit*: I should add that I'm running 12.04. Your problem might be that 13.04 is not ready yet for xrdp. By the way, what system are you running at the other end?

---

### Post by gordintoronto on 2013-03-16
There's actually a special forum for people helping to test the unreleased version of Ubuntu.

---

