---
title: "Sound, misc., etc."
date: 2006-01-05
forum: Desktop Environments
---

### Post by Razorback on 2006-01-05
I am getting my pc set up with Breezy 5.10.  I am wanting to  know what version of ALSA to download to ensure my onboard sound will work.  I have an old Compaq EP desktop with an AD 1881 AC97 sound chip.  The chipset is 82801AA and shows to be compatible.  Any help would be appreciated.  On another note, (noob question) is A/V and a firewall as important with Linux as with Windows?  And if so, what plug-ins would be the best to use? Thanks :)

---

### Post by bulldogzerofive on 2006-01-05
I am pretty sure you cannot just download and install another alsa and expect it to work.  If you post details of the problem you are having we can help you more.

A first step would be to open a command line, type "alsamixer" and check that nothing is muted.

As for security:

Some people will tell you you do not need to worry about security in Linux.  I do not think this is true... there are vulnerabilities in Linux and if people continue to ignore security it will eventually become an issue.  You need a firewall, you need to pay attention to the services you run, and you might as well run a virus scanner like clamAV to ensure that you are not unwittingly sending an infected file to some poor windows user (although at this time viruses are not a problem for linux).

As for a guide to secure your box, i find this page helpful:
[http://www.linuxsecurity.com/docs/LDP/Security-Quickstart-HOWTO/](http://www.linuxsecurity.com/docs/LDP/Security-Quickstart-HOWTO/)

In the meantime, i find guarddog to be a good firewall.

---

### Post by Razorback on 2006-01-06
Thanks for the reply.  Fixed my sound.  Went into multimedia setup and selected alsa.  I am really liking ubuntu! :)

---

