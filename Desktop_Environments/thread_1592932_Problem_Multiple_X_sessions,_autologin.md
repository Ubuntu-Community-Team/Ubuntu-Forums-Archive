---
title: "Problem: Multiple X sessions, autologin"
date: 2010-10-11
forum: Desktop Environments
---

### Post by Viciou§ on 2010-10-11
Hi!

I have a small problem regarding multiple X sessions.
I want 2 X sessions started automatically on boot with 2 different users auto logged in and 2 different sessions running.

On first X session i would like to have gnome running with user1
On second X session i would like to have xbmc running with user2
So far my computer logs user1 in to a gnome session via gdm on boot. But then I have to launch a tty, log in as user2 and then start xbmc in a new X session.

Could someone tell me/point me in the right direction as to how to make it work?
I would also love to have the second X session active after boot.

I am running Ubuntu 10.04 and sorry for my english.

---

### Post by Viciou§ on 2010-10-18
I have managed this by using mingetty to autologin the user2 user to tty1 and starting another x session with xbmc-standalone on tty8 (regular gnome via gdm on tty7).
So far so good...

However now when I switch from tty8 to tty7 and back to tty8 a second black mouse cursor appears in the center of the screen and doesn't go away.
**Edit: the black cursor doesn't move, it's more like a static image shown on top.**

The problem is only there when using xbmc-standalone, if I use gnome-session on tty8 as well there is only the "working" mouse cursor displayed.

Since xbmc-standalone runs in a fluxbox session(?) I was wondering if the cursor displayed is the default cursor image in fluxbox?
How do I get rid of this, it is really annoying to have a black cursor displayed in the middle of the screen when playing movies :-(

**Edit 2: Seems to be a problem only in xbmc, tried running fluxbox and it worked without the black cursor appearing.**

---

