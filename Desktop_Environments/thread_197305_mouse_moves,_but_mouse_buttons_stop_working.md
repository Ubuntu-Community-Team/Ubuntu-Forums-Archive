---
title: "mouse moves, but mouse buttons stop working"
date: 2006-06-15
forum: Desktop Environments
---

### Post by novalis112 on 2006-06-15
Greetings!

I've tinkered with Linux since way back in the mid nineties but when I heard the great reviews about the latest Ubuntu and the "Live CD" I figured it was time to put aside the "I need an OS, not a hobby" mindset and give it a shot!

Needless to say I was quite pleased.  Ran it for a good three days and then I came in today and the desktop was no longer responding.  The graphics are updating (ie. I have an RDP session open and I can see things changing on the remote machine) but I can't interact with them!  I can see the mouse moving on the screen, but it has no effect on the windows.  I can "Ctrl-Alt-F1" to a tty and execute commands there, and the keyboard does interact with gnome (ie. I can interact with windows via the keyboard shortcuts) so it seems like a mid-level mouse issue.  Just to be clear, graphical elements don't highlight as they should when I mouse over them, so it's not purely a button event issue.

Any help would be greatly appreciated.  This is already more "hobby" then I had hoped for, but I guess it just goes to show that *nothing* is free, right? ;)

Peace.

---

### Post by tiger338 on 2006-06-15
I have exactly the same problem as you. I had to reboot by pressing ALT + F2 and opening terminal and typing reboot command.

I want to write more in detail about this problem.

My system is DELL precision 360 with 1GB RAM.
I have been using Ubuntu 6.06 for two months since Flight4.
I installed famous XGL and compiz.

I did not have this problem until today after I updated kernel upto 2.6.15.25-686.

Just like you, I open RDP window and firefox. Suddenly mouse click does not work.

Any help will be appriciated.

---

### Post by mandible on 2006-06-16
I think with my system this happens when my screensaver locks the screen.  When I try to come back in I can't access anything on screen anymore and this only happens when I have a remote desktop application open to a windows box.  I have to reset my gnome panel everytime and usually end up rebooting.

---

### Post by drfox on 2006-06-16
I have the same problem. If I can use the keyboard to close my RDP session, I still have to Control-Alt-Backspace to reboot Gnome. The freezing doesn't happen if I disable the screensaver, but I often step away from my desk at work.

Larry

---

### Post by novalis112 on 2006-06-22
Well, I have now found several threads regarding what appears to be this same issue, and no answers.  On the upside, this problem seems to have stopped happening to me lately.  On the downside, it seems that Ubuntu is in fact still a hobby and not an OS, so I will not be recommending that my company switch away from XP.  Sigh...  So close.  It sure is a great hobby though!  Rock on guys.  I'll check back in a few years down the road again to see how things are coming along :)

---

### Post by penno on 2007-02-22
for whatever it's worth - I have the same problem. 6.06. Could well be related to rdesktop accessing a windoze box, but I haven't confirmed this. Sometimes the mouse buttons will just start to work, other times I couldn't be bothered waiting and use ctrl-alt-backspace to restart X.

---

### Post by karlhm76 on 2007-03-15
I have the exact same problem with 6.10 edgy. I run bluetooth keyboard and mouse. If I use USB for both keyboard and mouse I have no problems.

Occasionally both the keyboard and the mouse buttons stop responding. The mouse pointer still moves though. In those cases I usually reboot.

Sometimes when the mouse buttons stop working I can press the middle mouse button and it all comes back up. In those cases the keyboard is still working, I think this is a different problem, although maybe related. I think this is tied into the bluetooth side of things. The mouse buttons will stop working after the keyboard goes to sleep and wakes up again.

It is all sooo frustrating and it happens consistently. I never had the problem when I ran Suse 10.1, but then my bluetooth mouse scroll wheel didn't work under Suse.

Has anyone got any information about this?

---

### Post by patscott on 2007-03-23
Same problem, no ideas...

---

### Post by je1117 on 2007-10-29
Yikes, looks like an old issue here! Except after performing some updates for Gutsy just a few minutes ago, I am now experiencing the problem everyone is having here. Some other changes I have noticed since the update: whenever I boot up to the log in screen it shuts off my monitor as if the power saving mode comes on. Have no idea if that helps...

So my mouse moves just fine, but for the life of me I can't get the buttons to register. I am using a wireless mouse and keyboard, and as you can see, can get the keyboard to work just fine. The mouse moves, but doesn't detect links or icons (cursor changing faces), just moves around... which is great and neat and everything, but it's making my ubuntu experience a tad irritating. It is hard for me to navigate around for solutions, but hopefully something has been worked out and I don't know about it? Any help at all would be greatly appreciated...

---

### Post by natehatewindows on 2007-10-30
almost same problem here....except its only my external usb mouse and my track pad works fine as long as my mouse is not plugged in.....

---

