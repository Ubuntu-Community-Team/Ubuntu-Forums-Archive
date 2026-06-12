---
title: "Firestarter Set Up Q"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ULffuntu on 2005-10-24
Hi,

I'm having a problem configuring Firestarter. I can get the net ok with it off, but when it is on (Permissive) I can't connect to some sites. This "Sun-RPC portmap" Block comes up on 32997, etc..
Have no idea, TIA.

---

### Post by traherom on 2005-10-24
So... all out bound connections are by default allowed?

I haven't every actually been able to use the connection log in Firestarter, so I'm not sure if it tells you this, but was the connection inbound or outbound? An RPC is a remote procedure call, which is possible a Java applet or Javascript/AJAX thing calling home to get some more data. What's odd is that if that was the case, it should be allowed.

---

### Post by ULffuntu on 2005-10-24
It was an inbound block.

---

### Post by ULffuntu on 2005-10-24
Time: Oct 24 18:52:26 Source: 72.3.135.33 Destination: 192.168.0.100 In IF: eth0 Out IF:  Port: 33627 Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

---

### Post by thumbsoup on 2005-10-24
I am a newbie user myself, but I use Firestarter and I googled that source IP.  I found that one of the web sites for that IP has had its own forum discussion of this problem with Firestarter and Ubuntu.  I suggest setting a Policy in Firestarter for Inbound connections from that specific IP, and give it a likely range of ports and a name of your choosing. 

[http://anti-state.com/forum/index.php?board=5;action=display;threadid=13564;start=20#msg291225](http://anti-state.com/forum/index.php?board=5;action=display;threadid=13564;start=20#msg291225)

"Nope, that's not what was causing the problem. I know now for sure what was causing the problem: it was the Firestarter firewall that was causing the problem.

After I reinstalled the Firestarter firewall I was no longer able to connect to any of the above-mentioned websites with the 72.3.135.33 IP address. Apparently even when I go into the "All Processes" View in the System Monitor to make sure it is shut-down, it still remains active. But by using the "Stop Firewall" button within Firestarter it will allow me to access the above-said websites.

For whatever reason, Firestarter will not allow access to any of the above-said websites with the 72.3.135.33 IP address when it is active."

---

### Post by thumbsoup on 2005-10-24
Hmm, maybe I spoke too soon.  Over at JustLinux, someone suggested that this RPC call might be a scan for vulnerable Windows systems.  So would that be a spoofed source IP address, then? 

[http://justlinux.com/forum/showthread.php?threadid=137896](http://justlinux.com/forum/showthread.php?threadid=137896)

"My first reaction is that "sun-rpc portmapper" is an NFS thing. But there haven't really been a ton of vulnerabilities regarding NFS lately, so I'm not entirely sure why they'd be scanning to see if anyone had that in use.

But my second reaction is that RPC is a huge cause of bugs in Windows. It might be someone scanning to see if you're running a Windows machine that's vulnerable to one or more of these bugs."

---

