---
title: "Nautilus won't start up, desktop icons disappear and won't work"
date: 2007-11-01
forum: Desktop Environments
---

### Post by Sam C on 2007-11-01
When I start up Edubuntu 7.10, the icons on the desktop, all two of them, are there. However I can't select them, click on them, or do anything with them. I also can't drag while clicking and draw a box to select things. 

When I open up a window, and then close it, the icons are gone.

But most importantly, the file browser won't open up at all. When you try to open it, it just says "Starting Home Folder"(or whatever it is) in the window list and then disappears.

I'm running Edubuntu 7.10 with GNOME on an IBM Thinkpad T23 with
256Mb RAM
Intel P3 1133Mhz
60GB HDD

As I was writing this, two file browser windows opened up, about an hour after I tried to start them. 
After changing workspaces, they stopped working, and I took a screenshot which is attached.
Any help would be appreciated

Update: The file browser windows now take less time to start up, but when you close them they are not responding, and you can wait or force them to quit. The icons reappear every now and then but are unresponsive. I'm thinking of going over to KDE.

---

### Post by runemaste644 on 2007-11-24
Do the icons disappear when you kill the file browser and/or come back when you start a new file browser? If so, it is just that killing nautilus kills your desktop, too. If they disappear when you move a window over the icons, then it is a redraw error that i call garbage screen.

---

### Post by Cryptic1911 on 2007-11-24
I have a similar issue.. If I'm opening and closing a bunch of stuff, eventually the icons will become unresponsive, and when I click them, their icon changes to an empty file icon. I cant open any folders either. 

I can work around it by doing a "sudo killall nautilus" which kills it, and it restarts, but it does get kinda annoying after a while.

---

### Post by kalahari875 on 2007-12-22
I think Beagle is the problem. I had installed Kevin Kubasik's Beagle packages and this started. If I try to run nautilus from a command prompt, the following appears:

```
nautilus: error while loading shared libraries: libbeagle.so.0: cannot open shared object file: No such file or directory

```

[http://ubuntuforums.org/showthread.php?p=3913517](http://ubuntuforums.org/showthread.php?p=3913517) talks about this too. I downgraded Beagle to the Gutsy version and now it's working again.

---

