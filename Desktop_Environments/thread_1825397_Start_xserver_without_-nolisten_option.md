---
title: "Start xserver without -nolisten option"
date: 2011-08-15
forum: Desktop Environments
---

### Post by maloo on 2011-08-15
Hi All,
I have the following problem with Xserver which I think can be solved by starting it without the -nolisten option:

Server - (say 192.168.1.1) has the X application installed
Client - (say 192.168.1.2) is a stock standard ubuntu 11.04 client machine with screen and xserver installed.

I need to be able to run the X application on the ubuntu client by exporting the display on the server as follows:
```
export DISPLAY=192.168.1.2:0.0
xeyes
```
I have run 'xhost +' on the ubuntu client to disable access control however I still get the error:
```
Error: Can't open display: 192.168.1.2:0.0
```

I believe this is because xserver is started with the -nolisten option:
```
ps -ef | grep listen
root      1020   989  1 18:21 tty7     00:00:27 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-V9E9KA/database -nolisten tcp vt7

```

Both server and client are not connected to the outside world and are in a trusted environment so security is not a concern (I realise doing the above is a serious security issue)

I cannot use ssh tunneling for the xserver traffic as the proprietory program relies on the DISPLAY variable been set to the correct client ip. (Would be great if I could though!!)

I have searched the /etc directory for the -nolisten option and have found the following file: /etc/X11/xinit/xserverrc. I removed the -nolisten tcp option however the xserver still starts with the -nolisten tcp option.

I have been looking through the xserver manuals however cant find too much relating to this.

Does anyone have any pointers as to how i could start the xserver without the -nolisten option??

Thanks 
Paul

---

### Post by gmargo on 2011-08-15
See if this thread applies (creates/modifies /etc/gdm/custom.conf):
[http://ubuntuforums.org/showthread.php?t=1642286](http://ubuntuforums.org/showthread.php?t=1642286)

---

### Post by maloo on 2011-08-15
Thanks gmargo exactly what I was looking for!
Clearly my google skills are sub-optimal:/

---

