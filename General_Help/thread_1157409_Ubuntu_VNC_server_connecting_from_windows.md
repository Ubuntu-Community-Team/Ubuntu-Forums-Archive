---
title: "Ubuntu VNC server connecting from windows"
date: 2009-05-12
forum: General Help
---

### Post by l3iodeez on 2009-05-12
I am trying to connect to a Ubuntu VNC server from windows over the internet. I am tunneling through SSH, since I only have port 22 open, and no physical access. I was able to install vnc and get it running, and when I connect using TightVNC on my Windows machine, it says "Connection Established" and then immediately after I get a pop up saying "Connection Closed" Please help!

---

### Post by pricetech on 2009-05-12
I don't normally recommend something other than what's asked about but:
I'm using NX Client from nomachine dot com to remote in to my Linux boxen and it works flawlessly.

Make sure SSH works first.  Install client, node, server on Linux box.  Install winders client on winders box.  Should just plain work.

Best of luck.

---

### Post by l3iodeez on 2009-05-13
SSH works fine, and I am pretty sure the port tunneling is set up correctly. I would like to make VNC work if I can just because I prefer not to install more software. I am able to log in to VNC locally on the network where the server lives, but not from the net. Right now, I do not have physical access to the server, only SSH. I am still getting the "connection closed" message immediately after connecting, I never see the password prompt. Any ideas?

---

### Post by kryptikos on 2009-05-13
Sounds like we need a little more debugging. When you start your ssh session to your box (I imagine you have X forwarding as well) add -vvv to it. It will pipe alot of information to the console and post it here (redacted for IPs etc)

ssh -vvv -X <target>

---

### Post by l3iodeez on 2009-05-13
> **kryptikos said:**
> Sounds like we need a little more debugging. When you start your ssh session to your box (I imagine you have X forwarding as well) add -vvv to it. It will pipe alot of information to the console and post it here (redacted for IPs etc)

ssh -vvv -X <target>

Sorry, Im a bit noobish on this stuff. I am using PuTTY to connect. I forwarded local port 4901 (arbitrary) to remote 5901 (VNC). 

When you say add -vvv when I start my SSH session what exactly does that mean when using PuTTY? Where do I put that flag? 

As for X forwarding, I did not have it enabled. I was able to find the option for it, but I am not sure how it should be set up. Do I need it? Do I need some kind of X viewer for windows?

---

### Post by kryptikos on 2009-05-13
No need to apologize. It's what makes Linux fun, leanring all the things you can make it do.  There are a few links out there where folks did exactly what you are looking to do...check them out: 

[How to setup ssh to tunnel VNC]("http://members.shaw.ca/nicholas.fong/vnc/")

[Forward VNC over ssh (opens as a PDF file)]("http://www.cals.cornell.edu/cals/cals-it/it-staff/network-admin/upload/Tunneling-VNC-over-SSH-pdf.pdf")

You shouldn't need to forward X. Forwarding X will be if you just want to attach and run one of your GUI apps from your Linux box. The HOWTO for forwarding X via Putty is [here]("http://www.math.umn.edu/systems_guide/putty_xwin32.html")...but on windows you'll need an emulator such as Xwin32, xming, or cygwinx. That's just something you can play with later. Those links above should set you out on the right path....

---

### Post by l3iodeez on 2009-05-15
I am all but certain that I have set everything up properly based on those guides, but I am still getting a "connection closed" message when I try to connect. Is there a way to give a verbose output from PuTTY? Any other advice?

---

