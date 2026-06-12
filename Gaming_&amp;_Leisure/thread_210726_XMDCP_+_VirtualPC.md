---
title: "XMDCP + VirtualPC"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by goofeedude on 2006-07-07
Hi,
I've been trying to get XDMCP working such that I can log into my VirtualPC Ubuntu installation from Windows XP using either Cygwin's Xwin or Xming. So I've got Ubuntu running beatifully in the virtual machine, accessing the net just fine, and I've enabled XDMCP in gdm.conf. I fire up Xwin in Windows XP with
> $ Xwin -query 192.168.X.XX
in cygwin. I get an X Window with the black X cursor, but I don't get a welcome screen or anything. Every minute or so, the window "refreshes" and nothing changes. Same thing with Xming :( .

I thought this might have to do with:
1. Network problems (firewall somewhere in the way? Even though I turned the local software firewall off.)
2. Xaccess disallowing the connection (I can't seem to find Xaccess for gdm?).
3. The fact that I am trying to XDMCP into this virtual machine from the host machine (Yet others have done it successfully.)

I have read of others getting it right, but I can't think of what else to do. I've been searching for a few hours, so any help would be greatly appreciated! If you have any ideas on what to try next, please post :)  Thanks for reading.

---

### Post by goofeedude on 2006-07-07
AI!
Sorry this is in "Gaming Central", this new theme is confusing! I misclicked. Maybe a mod could move this to the appropriate forum?

Apologies!

---

### Post by harisund on 2006-07-07
I am not sure I understand what a "VirtualPC Ubuntu installation". Could you elaborate? I have XDMCP running on my Ubuntu desktop, and I am able to access it using my Windows XP laptop cygwin using the -query option fine.

---

### Post by goofeedude on 2006-07-07
Meaning I have Microsoft Virtual PC 2004 running a virtual machine on which Ubuntu is installed. I first got the idea to run XMDCP (and enjoy the increase of speed) here:
[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004]("https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004")

At the bottom of the article it suggests what I am doing is possible. I hope to find some luck with it :) . 

Thanks for your reply!

---

### Post by harisund on 2006-07-08
My only belief might be that the Windows that is running behind (on which the VirtualPC is running) is blocking certain ports. 

Go to your Ubuntu installation and do a "sudo netstat -anu". This will list all open UDP ports on your machine. Ensure that port 177 is indeed open, as this is the XDMCP port. 

Next, make sure your Windows machne and Linux machine are on the same subnet. In your case, I think both should have an IP address of 192.168.0.* where the * is the only part that makes the IP unique. Check those two.

Finally, ensure that the Windows firewall is either off (temporarily) or allow Windows Firewall (on your Windows running cygwin) to open ports from say 6000 to 6005. 

The reason is this. When you do a "Xwin -query 192.168.*.*" your Cygwin contacts the server on port 177. The server then responds by contacting your cygwin on port 6000+DisplayWindow. The DisplayWindow is generally set to 0. 
This is why they need to be on the same subnet. And this is also why you need to ensure port 177 (UDP) is open on your LInux box and port 6000 (TCP) is open on your Windows box.

---

### Post by goofeedude on 2006-07-09
Thank you so much for your help. I have run the netstat command, and to the best of my knowledge, UDP port 177 is open. I can also ping ubuntu's address from the windows box, and it works. Both boxes (as it were) are in the same subnet. I have turned off the Windows firewall, and still nothing. I will post from Ubuntu in a minute and show you the output of the netstat command.

Edit:
Here is the output of the netstat command:
```

$ sudo netstat -anu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
udp        0      0 0.0.0.0:177             0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*

```
The address of this box is 192.168.2.39 and the Windows box is 192.168.2.5

Thanks for the help!

P.S. -Would it help you to see the output of what Xwin says when I run the command in Windows? Nothing there looks too bad to me, but maybe you would recognize a problem.

---

### Post by harisund on 2006-07-09
this looks bad :( .. yes, UDP 177 is open (which is XDMCP) and so is UDP 68 (which is for the DHCP client). 

I doubt posting the Cygwin output would be of any help. But perhaps you should, maybe someone more skilled than myself could help you out here. 

Do that, and in the meanwhile, 2 other questions. are you on wireless? If so, you might have to wait a while (it could be slow) and second, your GUI is indeed running on the Linux box, right? 

Sorry .. I don't seem to be of much help here... maybe the Cygwin output could help.

---

### Post by goofeedude on 2006-07-10
Thank you so much for your help and input. I am afraid it's a lost cause (lol). I even switched to KDM and set it up for XDMCP to see if that made any difference. Then I tried another Ubuntu box on my network (Xubuntu 6.06) and still no luck. I think there is a problem with my Cygwin and Xming installations. I even took down every firewall between me and the internet in an attempt to get *anything* at all. No luck.

Thanks for your help though :-)

---

### Post by harisund on 2006-07-10
I am strongly under the impression that the problem is with the Virtual PC. 

Your Xubuntu 6.06 box, is it running using Virtual PC too? 

Anyway I will list out everything I did to make by Ubuntu box (running GDM) accessible through XDMCP. 

1. Switch off firewall in Windows box. 
2. Ensure Cygwin/X is installed properly. I verified this by forwarding X through SSH from my Ubuntu box to my Windows box. Are you sure you have installed X correctly? 
3. Ensure XDMCP is enabled on the Linux box (the netstat command - 177 UDP port) by also checking the /etc/gdm/gdm.conf file
4. Ensure that GDM is running but no one has logged in in my Linux box(did you do this?) In other words, let the GDM login screen show, but do not log in into the local box. 
5. Open a Cygwin terminal (not X terminal) and type in XWin.exe -query 192.168.linux.box and wait a while. If not, close it and try it a couple of times. 

have you verified all the above? 
(.) GDM should be running on the Linux box and it should have an IP correctly (you should be able to ping it)
(.) XDMCP should be enabled
(.) Windows Firewall should be disabled
(.) Cygwin and all the X libraries should be installed correctly. 

I am sorry, cause I am probably saying the same thing over and over again, but the thing is, I have XDMCP working fine on my LAN and would hate to not have you working with it as well :(

---

### Post by goofeedude on 2006-07-10
The Xubuntu box is not a virtual pc, it's a real box :) .

Two things that may be wrong are-

I think I did have a local user logged on the box when I tried earlier.
Maybe the two X11 implementations I have installed in windows are not working properly? (Cygwin/X and Xming) If I am in cygwin, and run 'startx', I get an x terminal (no window manager, just a shell.) There is always some error about fonts when I start it, too. Do I need an X window manager on my cygwin install?

These things are certainly okay to go:
Windows firewall off.
Can ping 192.168.2.Xubuntu just fine
XDMCP enabled in gdm.conf


I am not sure how to forward X through SSH to check the validity of the installs...?

Thanks for your help, I think I'll keep playing with it and see what happens.

---

