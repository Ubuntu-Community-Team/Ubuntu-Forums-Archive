---
title: "issue with Chrome-Remote-desktop and wayland display server"
date: 2017-10-25
forum: Desktop Environments
---

### Post by kunalv-shah on 2017-10-25
Hi All,

I recently switched from 16.04 to 17.10. I was using Chrome-Remote-Desktop to connect to my Ubuntu desktop from my mac. I wanted to do the same with 17.10.  However, I  am having issues with it when I am logged in ubuntu 17.10. I don't have this issue if I login to ubuntu via xOrg. 

When I log in ubuntu 17.10 with wayland display server, I am not able to enable access to chrome-remote-desktop. Attached is the screenshot of the error.

 [IMG]https://photos.app.goo.gl/iRcDHt3Am60Ggnt62[/IMG]I tried to search for this error and in past versions, it used to be the permission issue. The user that starts chrome-remote-desktop was not part of chrome-remote-desktop group. However, that is not the case with my issue. My user is indeed part of chrome-remote-desktop.

Also I don't have any firewall rules set. 

So I am not sure what is wrong with this. Can you please let me know if you can help ? Also should I file bug report?

```


kunalshah@kunalshah-desktop:~$ groups kunalshah
kunalshah : kunalshah adm cdrom sudo dip plugdev lpadmin sambashare chrome-remote-desktop
kunalshah@kunalshah-desktop:~$ 




```

Thanks
Kunal Shah

---

### Post by TheFu on 2017-10-26
wayland doesn't support remote display.

> **Is Wayland network transparent / does it support remote rendering?**
 
No, that is outside the scope of Wayland. To support remote rendering you need to define a rendering API, which is something I've been very careful to avoid doing. The reason Wayland is so simple and feasible at all is that I'm sidestepping this big task and pushing it to the clients. It's an interesting challenge, a very big task and it's hard to get right, but essentially orthogonal to what Wayland tries to achieve.  
from [https://wayland.freedesktop.org/faq.html](https://wayland.freedesktop.org/faq.html)

Use X11.

Or am I miss understanding the issue?

---

### Post by daniel-schliemann on 2017-10-26
I believe it is caused by any incompatibility between Chrome Remote Desktop protocol "Chromoting" and the Wayland display server. "Chromoting" (terrible term :D) uses either RDP or VNC like stuff which doesn´t fully work together with Wayland. There are several different posts about VNC problems in Wayland on the net. I also gave the Chrome Help Forum a try today but nothing happened until now. [COLOR=#000000][FONT=&amp]¯\_(&#12484;)_/¯ [/FONT][/COLOR]I´m using 17.10 a few days and this was one of the first issue I was facing.

Hope this is gonna be fixed soon. I like Wayland. :)

Update: @TheFu -> nothing to add :)

---

### Post by kunalv-shah on 2017-10-26
Bummer - so if I use wayland - I cann't remote render X apps from my ubuntu. 


I read the FAQ posted by TheFu. It says VNC should work. However I have problems with VNC as well. It is not able to find desktop. especially when I am not in front of machine and it is reboot. Unless someone logs in from desktop, VNC does not work.

---

### Post by TheFu on 2017-10-27
Wayland is new and being network neutral isn't in their near-term goals.  If you want remote desktops, check out spice and **x2go**.  Both have slight issues, but might work for your needs.  x2go doesn't like any DE that demands direct HW access to the GPU, so lighter DEs are needed - LXDE, XFCE, Mate, or a pure, non-compositing WM.  I use openbox with my x2go sessions from around the world.

I stopped using VNC about 8 yrs ago - for NX-based solutions.

Of course, when I'm on the same LAN, **ssh -X** is amazing ... but Wayland doesn't support that.

Spice is a libvirt+KVM thing.  It has a goal of near-native remote desktop performance, but only works with VMs.  I found the keyboard mappings a little off - in important ways.  All my servers are on 14.04, so perhaps 16.04 has make Spice even better?  I know Redhat uses it for their oVirt enterprise clusters, so it should be pretty fantastic after 3 more yrs of development.

But your client is a Mac.  That puts some added complexity into the solution.  There is an x2go OSX client. I know the Windows and Linux clients are pretty great.  No idea about the Mac.  The only trick is to get ssh working between the client/server BEFORE installing x2go.  It isn't like anyone is foolish enough to use VNC without an ssh tunnel anyway.

---

### Post by kunalv-shah on 2017-10-28
I think I have a partial solution for this. I am using XQuartz as x server on my macbook. using it's xterm I can do ssh -X and it does x11forwarding. I tried launching xclock and it came up fine. so far so good. Now at least I can get a GUI applications on my Mac on demand as long as I am on my local network. 

One of the advantages of chrome-remote-desktop was that I was able to access my ubuntu machine from anywhere. My ISP blocks incoming traffic and does not allow me to open ssh tunnel over internet. That means with this partial work around, I will not be able to access my ubuntu desktop from internet. I guess I will just have to wait for chrome-remote-desktop to come up with solution. Thinking of filling a report with them too.

---

### Post by TheFu on 2017-10-28
Ouch on the ISP blocking inbound.  If you aren't paying extra for the "enterprise security", then I'd complain.

I was going to suggest x2go - but it requires inbound ssh.

Another option is to buy a VPS somewhere and start a reverse ssh session from your home.  Then you'd use the VPS IP to access your home.  $5/month isn't THAT bad.

Are you saying that choosing the xorg option - pre-login - doesn't work?  I would guess that it should, but I'm an LTS-only guy.  Actually most of my systems are on 14.04 still, with just 2 machines on 16.04 while it becomes stable.  I couldn't imagine running 17.xx, unless my HW was so new that it was the only way.

BTW, Macs run Ubuntu really great!  You could wipe OSX and put Ubuntu directly on it. ;)  There's even an Apple-specific sub-forum here.

Gotta go - teaching an ssh A-Z class this morning.  We are covering most easy to do things - ssh, sftp, scp, rsync, x2go, sshfs, and ssh-tunnel, along with how to secure ssh stuff. ;)

---

### Post by kunalv-shah on 2017-10-28
with xorg prelogin chrome remote desktop -sometimes it works, sometimes it does not. . I am not able to find a pattern or exact steps when it works or breaks  but I am sure there are some issues. Its not stable to say the least.

---

