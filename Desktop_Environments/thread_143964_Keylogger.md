---
title: "Keylogger"
date: 2006-03-13
forum: Desktop Environments
---

### Post by drgilberto on 2006-03-13
Hi,

I have a linux computer (ubuntu 5.10) attached to the university network.  The only network daemon running is a ssh daemon.  I use the computer for some browsing, I run the newest Firefox for that.

Now, the networking people told me that took the computer of the network, because they said the computer was infected with a 'keylogging' malware program.:(  :confused: 

Does anybody know how this can happen to a Ubuntu machine.  It is unlikely, but of course not impossible, that somebody somehow got my password and broke in, but I really doubt that.

[COLOR="Red"][B]Does anybody know which keylogging virus are run on Ubuntu. 

HOW CAN I DETECT SUCH A PROGRAM ON MY COMPUTER?:confused: 
[/B][/COLOR]
Thanks for helping.

---

### Post by kaamos on 2006-03-13
Sounds very unlikely.. I'd put my money on that they thought sshd connections or something else was the malware. However you could try to look at the log file /var/log/auth.log for anything suspicious.

If you are feeling unsure, you could disable the ssh daemon, disconnect the box from the network and boot in recovery mode and use "passwd" to change your password.

---

### Post by stuporglue on 2006-03-13
> Now, the networking people told me that took the computer of the network, because they said the computer was infected with a 'keylogging' malware program. 

It might be fun to ask the networking people which program it was, or how they detected it. At my school it used to be very entertaining to even work with OSX on the network. 

Them: "Go to the start button"
Me: "I don't have one"
Them: "uhhhhhh"

That was about 3 years ago. Luckily it's much better now. Most of the support people have at least heard of Linux, and they're more understanding of it. 

You might want to install clamav and run a scan on your system. Then when you call them, you can tell them "I ran an updated anti-virus scan, and my system is clean now".

---

### Post by drgilberto on 2006-03-13
Thanks for your emails.  I am pretty confinced that we actually got a false alarm from the IT people.  Of course false alarms occur, and it takes a lot of effort to figure out what is going on.  I couldn't believe my Ubuntu was infected, but I wanted to make sure there are not tons of other people having similar problems.

---

