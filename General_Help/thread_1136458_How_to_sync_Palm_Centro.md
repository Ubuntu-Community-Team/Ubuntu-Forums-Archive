---
title: "How to sync Palm Centro"
date: 2009-04-25
forum: General Help
---

### Post by matdombrock on 2009-04-25
I have a palm centro and I'm getting tired of having to boot into windows to hotsync and install new apps. Thats about the only reason I use windows.

IS there any way I can either run hotsync in Ubuntu or is there another program I can use?

Thanks bro's!:P

p.s. I don't think virtual box will work, I've heard it cant recognize USB devices.

---

### Post by defishguy on 2009-04-25
There are a couple of ways to do it.  The easiest, and most "Palm" like way is to use JPilot.

> sudo apt-get install jpilot

There is a thread that has other users Centro/JPilot experiences that might be worth a read [_HERE_]("http://ubuntuforums.org/showthread.php?t=750741").

You could also sync with Evolution if you use that as your email client. This is analogous to syncing the Centro with Outlook in Windows.  IMHO it's also kind of buggy although I haven't tried it in Jaunty.

Start Evolution.  Configure your email account.  Once your finished pull down the edit menu and seclect "Synchronization Options".  A wizard will start and all you need to do is answer the questions.

If you have problems with Evolution talking to your Centro try opening up a terminal and typing:

> sudo modprobe visor 

It'll look like nothing happened but it did.  Try repeating the process for getting Evolution to work.

Good luck!

---

