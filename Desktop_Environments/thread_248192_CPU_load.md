---
title: "CPU load"
date: 2006-08-31
forum: Desktop Environments
---

### Post by bearcat on 2006-08-31
Have something confusing going on today that I need a bit of help with.

For the first time since I've been using Ubuntu, today my CPU seems to be permanently stuck at 100% capacity load whether anything's running or not. I've checked the system monitor and there don't seem to be any abnormal processes running in the background; in fact, the last time I checked the system monitor the *only* process listed as being in a running state was the system monitor itself. My actual application *speed* doesn't seem to be that much slower than normal, however; it is a bit off, but not even close to the crawl I'd normally get if I tried to run too many programs at once.

I've also tried rebooting a couple of times, and that doesn't make a difference.

One weird thing did happen *yesterday* which may or may not be connected. My machine is a dual boot, and I was in Windows for a while to do something, and then I shut down and rebooted into Ubuntu -- but for some reason, right after I typed in my username and password, the Ubuntu bootup process very briefly flashed back to the Windows shutdown screen before launching my Ubuntu desktop. But the CPU load wasn't abnormal after that happened; it's only been doing this today.

Any help would be appreciated; let me know if you need more information than I've provided.

*ETA: I did not install, uninstall or upgrade any packages between yesterday and today.*

---

### Post by tribaal on 2006-08-31
I've heard of a bug in gnome monitor (I think).
What load does the "top" command show?
Just paste it's output in here if you're unsure (although top's output is dynamic...).

- trib'

---

### Post by bearcat on 2006-08-31
top is giving me load numbers that seem more normal, varying from about 40-90% depending on what's actually happening at any given time.

Could a bug in gnome-monitor only start showing up today even though it hasn't been upgraded since yesterday when it seemed to be working properly?

---

### Post by tribaal on 2006-08-31
Hum that would sound kind of weird, I agree.
Well if your Ubuntu behaves normally (reactive, "snappy" and no crashes) I guess it's just some kind of display bug... Hopefully it will be fixed.

Also, you might want to look through [launchpad]("https://launchpad.net/"), maybe someone filled in a similar bug description already?

- trib'

---

### Post by bearcat on 2006-09-01
Got it sorted out, thanks...turned out to be the gnome-cups memory leak bug. Halted that process and everything's now back to normal.

---

### Post by Kurt` on 2006-09-01
A cool alternative to 'top' is htop.

# sudo apt-get install htop

then to start it:

# htop

---

