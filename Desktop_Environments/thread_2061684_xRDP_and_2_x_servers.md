---
title: "xRDP and 2 x servers"
date: 2012-09-23
forum: Desktop Environments
---

### Post by MacOsX74 on 2012-09-23
Hi!

I have been trying to get this setup to work:

First X session with user 1 on tty7
Second X session  with user 2 on tty8

I would like to control user 1 remotly
and user 2 to run on screen which in this case is an projector.

I have tried wth xRDP.  I cant get it to work.
It works fine if I am in tty7 but if I switch ti tty8 the screen sort of freezes. I have pointer but I cant see if anything happens. When I switch back I see everything. All programs i clicked on has opened. So it dosent freezes, just that the screen dosent follow what I am doing.

Do I need to set it up in another manner?

---

### Post by conradin on 2012-09-23
I think you need to enable multiple displays. 
[http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals](http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals)

You can set up X11 forwarding on ssh which would be my remote user control method of choice. remote-desktop will be a lot of overhead though Im sure you can do it. 


why it sounds familiar to me:
[http://ubuntuforums.org/showthread.php?t=1557920](http://ubuntuforums.org/showthread.php?t=1557920)

---

### Post by MacOsX74 on 2012-09-24
If i understand so need I tell tty8 to run on screen 1 instead of screen 0 which would be default.

If thats right. Can I change so that tty7, the one i will control remotly, runs on screen 1 instead of screen 0

Would it be in xorg.conf I make the changes for that.

---

### Post by MacOsX74 on 2012-09-27
OK!

I have been testing with multiple x sessions but no matter what I do its always the same.
If I run startx -- :1 same user starts another x session on tty8. But when i try remote connection to tty7 the screen is black. But if I try tty8 everything works jusat fine.

How can I get Remote access to tty7 when I have tty8 on my screen.

---

### Post by conradin on 2012-09-30
You must put a space between the "--" and the ":2"

Otherwise if you want to do remote sessions, of a computer you are logged into, you could run ssh with X11 forwarding set up.
but again, that entails additional overhead.

---

### Post by MacOsX74 on 2012-09-30
> **conradin said:**
> You must put a space between the "--" and the ":2"

Otherwise if you want to do remote sessions, of a computer you are logged into, you could run ssh with X11 forwarding set up.
but again, that entails additional overhead.

I have a space between -- and :1. I get access but only to the session thats active on the connected screen. I want access to the session thats not active on the connected screen.

If I try to connect to an session that is not displayed on my screen I only get black screen on my remote machine.

---

