---
title: "Good rescue CD - is Breezy live CD good?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by agger on 2005-12-22
Yesterday, I had to help a friend whose Windows had gone bad recover some data before reinstalling.

So, I grabbed a Hoary live CD (and borrowed a Knoppix 3.7 from the IT department at work, just in case) and booted his computer.

The live CD didn't mount the hard drive by default, though, and I couldn't just recall how to do it, so I grabbed the Knoppix. This time the harddisk was mounted - but when inserting the USB key for copying data, Knoppix automounted it with read only access :-(

Is the Breezy live CD better as a quick and dirty "rescue operation" than the hoary one? 

Ideally, one would want to boot into (a preferrably lightweight) Linux with all drives mounted, maximum read/write access (if supported, that is, no write permission on NTFS drives) and as root or with password-free sudo.
If the Breezy CD doesn't do that, does anybody know which Linux distro would be best for that - DSL (Damn Small Linux), possibly?

---

### Post by codejunkie on 2005-12-22
[QUOTE=agger]Yesterday, I had to help a friend whose Windows had gone bad recover some data before reinstalling.

So, I grabbed a Hoary live CD (and borrowed a Knoppix 3.7 from the IT department at work, just in case) and booted his computer.

The live CD didn't mount the hard drive by default, though, and I couldn't just recall how to do it, so I grabbed the Knoppix. This time the harddisk was mounted - but when inserting the USB key for copying data, Knoppix automounted it with read only access :-(

Is the Breezy live CD better as a quick and dirty "rescue operation" than the hoary one? 

Ideally, one would want to boot into (a preferrably lightweight) Linux with all drives mounted, maximum read/write access (if supported, that is, no write permission on NTFS drives) and as root or with password-free sudo.
If the Breezy CD doesn't do that, does anybody know which Linux distro would be best for that - DSL (Damn Small Linux), possibly?[/QUOTE]
same as you still have to mount the partitions yourself but it may be a little better for newer hardware since it has the newer kernel.

---

### Post by anil_robo on 2005-12-22
can't we make a live cd ourselves? with all those options enabled?
if yes, how?

---

### Post by briguy on 2005-12-22
I use Knoppix for rescue work - it has utilities in place for just that.

---

### Post by agger on 2005-12-23
[QUOTE=briguy]I use Knoppix for rescue work - it has utilities in place for just that.[/QUOTE]

OK, but what version? Like I said, Knoppix 3.7 automounted the USB key as read-only which I wasn't very happy about ...

---

### Post by nb- on 2005-12-23
You might want to have a poke at Auditor

[http://www.remote-exploit.org/index.php/Auditor_main](http://www.remote-exploit.org/index.php/Auditor_main)

---

### Post by stevea1210 on 2005-12-23
If you are using knoppix, right click on the desktop icon for the drive, and there will be an option to remount as read/write.  I don't have  knoppix with me right now, so the verbiage may differ slightly.

I use knoppix and slax for live cd's.  I keep slax on a usb key and knoppix on cd.   One thing that is real nice about slax is it is very modular.  You can simply add new modules and reburn your iso to add / remove apps.

---

### Post by sham69 on 2006-03-03
Just booted up the 5.10 Live CD and it's great, but too much work for rescue CD..as the man said try SLAX. You can build your own Live disk with modules and it detects the partitions and mounts them at boot. Also has K3B, so you can burn data to CD if need be!! Also,  I added Lisa to get on your LAN and QTParted for partitioning . It's very handy!  :-D

---

### Post by aysiu on 2006-03-03
Ubuntu's live CD (Breezy or Hoary) is not designed to be rescue CD.
It *can* rescue your files; it's just not *designed* to rescue them.

Ubuntu's live CD has as its primary purpose to demo Ubuntu and give you a sense of whether it's worth installing or not.

Knoppix, however, is *designed* to help you recover stuff and has recovery tools built into it.

---

### Post by akiro.yamamoto on 2006-03-03
I would try SLAX. It is light weight and very modular. If your ever in a situation that you need to recover info from a system with limited resources, the ubuntu CD 
will be a pain.

---

### Post by cotcot on 2006-03-03
I have good experience with the Ubuntu live CD and Kanotix live CD (Debian based) and bad experience with SLAX (lack of hardware recognition.

---

### Post by akiro.yamamoto on 2006-03-03
so the best would be a modified / stripped down ubuntu Live Cd ?

---

### Post by ardchoille on 2006-03-03
I feel that [System Rescue CD]("http://www.sysresccd.org/Main_Page") is the best rescue CD around. There is also MEPIS and knoppix.

---

