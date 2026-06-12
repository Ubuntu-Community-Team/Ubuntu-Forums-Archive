---
title: "Auto Logout Issue"
date: 2006-07-04
forum: Desktop Environments
---

### Post by wh0rd on 2006-07-04
I've switched over to Kubuntu when this happened before, but Kubuntu freezes all the time! So I'm back to Ubuntu. My issue is when I try to log in I automatically get loged out and it puts me right back at the login screen, prompting me for my user ID and Password. I've tried looking through the forums with no success. I've tried even to remove the .ICEauthority from the home directory as suggested in one post. If anyone could be kind enough to shed some light on this matter?

---

### Post by vigleik on 2006-07-04
There were some issues with autologin earlier. Did you make sure your computer is up to date? "sudo apt-get update" and "sudo apt-get upgrade" should take care of that. I guess ubuntu (as opposed to kubuntu) also comes with a button for doing this automatically. If you have an up to date system I'm not sure what you can do though. Autologin works for me in kde, but only after I installed some updates.

Vigleik

---

### Post by wh0rd on 2006-07-04
I wasn't even using Autologin, I was manually entering my user name and password. So I don't think that's the issue. Let me try to be more descriptive. I get the standard Ubuntu GUI login prompt, I log in and the sounds go off, then after the panels show up the screen turns dark, as if you were doing a CTRL+ALT+BACKSPACE and it goes back into the login prompt. So it looks as if xserver gets restarted. I didn't install anything new when this happened, I was simplying organizing some icons on my panel.

---

### Post by wh0rd on 2006-07-09
Well I've reinstalled Ubuntu. It worked okay for a couple of days and then this log in problem happened again. I need to start backing up. Every time I have my system the way I want it, this issue will put me back at zero. If anyone has any clue on whats going on, please don't hesitate to post.

---

### Post by wh0rd on 2006-08-17
k! After trial and error, couple of reinstalls. I found out that when I enable the panel's transparency in Ubuntu (Gnome) this logout issue occurs. So I've just left it a sold color and it seems to be okay.

---

### Post by veugelenw on 2007-10-25
I have the same issue at the moment .
No solution known?

---

