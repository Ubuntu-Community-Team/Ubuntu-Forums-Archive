---
title: "Where's my gnome-panel..."
date: 2009-04-26
forum: General Help
---

### Post by dwdude on 2009-04-26
So I'll start from the top.

Ubuntu 8.04 is the version.

I followed this guide:
[http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml)

And everything was working fine. Rebooting the computer and everything worked okay.

So then, I log into aMSN and try to change my picture. It automatically logged me out. After sitting there in some confusion, I found out that if you have compiz effects enabled and try to change your picture, you get logged out... So I disable compiz effects and change my picture. Problem solved.

BUT WAIT.

Apparently, awn replies heavily on compiz.

I didn't know this and then turned my computer off for the night. Turning it bck on reveals a message, saying "Warning: Screen not composited"  and such. So here I am, stuck with a dock, a wallpaper, and a cursor. No right click, no icons, nothing. I added the menu to the dock which shows everything on the menu, but even if I try running a program, nothing comes up. I'm not exactly sure how to get my desktop back.


So my question is, how do I get my desktop back? I cant get to any menus unless I log out and use the failsafe gnome session, and I don't know how to edit the xclients (which is what is default).

If you need any other information, ask. Thanks in advance...

---

### Post by dwdude on 2009-04-26
Fixed it myself.

I went to the failsafe gnome session, went to ~/.gnome2/session and deleted it. Then I right clicked the desktop, added a launcher for "gnome-panel". ctrl + alt + backspace, chose the xclients script session and I had my desktop back. I used the created gnome-panel to go to system > preferences > appearance, enabled compiz. Then I just put the gnome-panel at the top and made it autohide + transparent.

I found out if I did this except going to sessions and removed the gnome-panel from the current session, my desktop would be gone again.

This wasn't the case before, but now it is... Problem solved, but now I'm curious as to why that is. Oh well.

---

