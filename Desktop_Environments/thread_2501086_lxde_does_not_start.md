---
title: "lxde does not start"
date: 2024-09-22
forum: Desktop Environments
---

### Post by osakibill2 on 2024-09-22
[LIST]
[*]I installed lxde on Ubuntu Server 24.04 on Rasberry pi.
[*]It works when I open an external xterm to the pi.
[/LIST]
but on the console, lxde does not start.

From what I can tell is that x is starting since I get a blank screen with a blinking cursor. Ctrl-Alt-F4 gets me back to cmd line.

I found what I thought would be my perfect fix in the post: [COLOR=#000000][SOLVED] Failed to start session with LXDE on Ubuntu Server

I created the [/COLOR][COLOR=#000000]/etc/lightdm/lightdm.conf file but nothing changed,

file looks like this

[/COLOR][SeatDefaults]
autologin-user=
user-session=lxde

ls of directory

drwxr-xr-x   3 root root  4096 Sep 22 16:31 .
drwxr-xr-x 143 root root 12288 Sep 22 14:50 ..
-rw-r--r--   1 root root    50 Sep 22 16:31 lightdm.conf
drwxr-xr-x   2 root root  4096 Apr  8 15:44 lightdm.conf.d
-rw-r--r--   1 root root   466 Apr  8 15:44 users.conf


Am I missing something?

thanks Bill

---

### Post by ActionParsnip on 2024-09-23
Do you have lightdm installed? or did you select gdm when you installed LXDE ?

---

### Post by osakibill2 on 2024-09-24
Hi, thanks for responding...

here is the response from apt list

billm@raspberrypi:~$ apt list gdm3
Listing... Done
gdm3/noble 46.0-2ubuntu1 arm64
billm@raspberrypi:~$ apt list lightdm
Listing... Done
lightdm/noble,now 1.30.0-0ubuntu14 arm64 [installed,automatic]

So only lightdm is installed.

Perhaps adding a second environment will expose the option to select lxdm?
If I understand correctly, the display manager only appears after 2 or more environments are installed.

---

### Post by osakibill2 on 2024-09-24
Additional info...

So I installed a second environment, lxqt. But I got the same result.
So I deinstalled it and reinstalled lxdm. 

I am doing this over an ssh session. And upon reinstalling lxdm, I actually got a graphical option to select lightdm or lxdm, I selected lxdm, but didn't work and the main console kept going back and forth from regular shell login promt to blank screen with blinking cursor. Upon further investigation I found the following message printed multiple times...

From journalctl:    

Sep 24 11:25:57 raspberrypi systemd[1]: lxdm.service: Scheduled restart job, restart counter is at 10.Sep 24 11:25:57 raspberrypi systemd[1]: Started lxdm.service - LXDE Display Manager.
Sep 24 11:26:02 raspberrypi systemd[1]: lxdm.service: Main process exited, code=exited, status=1/FAILURE
Sep 24 11:26:02 raspberrypi systemd[1]: lxdm.service: Failed with result 'exit-code'.

And so now it is in a constant loop.



thanks,
Bill

---

### Post by ActionParsnip on 2024-09-24
> **osakibill2 said:**
> Additional info...

So I installed a second environment, lxqt. But I got the same result.
So I deinstalled it and reinstalled lxdm. 

I am doing this over an ssh session. And upon reinstalling lxdm, I actually got a graphical option to select lightdm or lxdm, I selected lxdm, but didn't work and the main console kept going back and forth from regular shell login promt to blank screen with blinking cursor. Upon further investigation I found the following message printed multiple times...

From journalctl:    

Sep 24 11:25:57 raspberrypi systemd[1]: lxdm.service: Scheduled restart job, restart counter is at 10.Sep 24 11:25:57 raspberrypi systemd[1]: Started lxdm.service - LXDE Display Manager.
Sep 24 11:26:02 raspberrypi systemd[1]: lxdm.service: Main process exited, code=exited, status=1/FAILURE
Sep 24 11:26:02 raspberrypi systemd[1]: lxdm.service: Failed with result 'exit-code'.

And so now it is in a constant loop.



thanks,
Bill

Could try installing gem and using that. When I've installed a GUI on a Pi I always take the default which is gdm (I use LXDE also)

---

### Post by osakibill2 on 2024-09-24
HI,

So I gave up and installed ubuntu-desktop. After a little problem with the login screen I got it running fine.
I am happy with it. Closing out this thread.

---

