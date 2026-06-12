---
title: "Getting the Windows key to actually work (xfce4)"
date: 2008-05-01
forum: Desktop Environments
---

### Post by hihp on 2008-05-01
Hi,

I am pretty much new to using Linux in general or Ubuntu in specific (I am running Mythbuntu 7.10).

When on the desktop (if I understand that correctly, my Mythbuntu is running xfce4), I would like to be able to open the Applications menu using the Windows key. I already did a lot of search and am principally aware how it should work:

The two windows keys seem to produce the keycodes 115 and 116 (confirmed using xev). Therefore, the two calls of xmodmap:
```
xmodmap -e "keycode 115 = F13"
xmodmap -e "keycode 116 = F13"
```
assing the virtual key code (or whatever it's called under Linux) of "F13" to this.

If I call up Applications -> Settings -> Keyboard, make my own shortcut profile and have a command xfce4-popup-menu assigned the shortcut F13, everything works fine. This latter step I actually only had to do once, it sticks, as one would expect.

What does not stick is the mapping of the Windows keys, so I understand I need to run a bash script every time I start a session with this user. For that purpose, I wrote a script
```
#!/bin/bash
xmodmap -e "keycode 115 = F13"
xmodmap -e "keycode 116 = F13"
```
which I also made executeable. However, when I run it, the assignment does not happen.

What am I doing wrong?

(I already figured out that I can later use Applications -> Settings -> Sessions to have this script run on startup; the problem is that it does not do what I want.)

That is not all, however: if I use the aforementioned xmodmap calls, the Windows keys get assigned F13, but using them to call up the Applications menu only works if I open up Applications -> Settings -> Keyboard and close it again. I assume the reason is that the xfce shortcut manager needs to have his config made current or whatever.

So.. is my approach completely wrong or what should I do to get this working?

---

### Post by Bluekkis on 2008-05-01
xmodmap commands are auto executed from ~/.Xmodmap file every time you login. Just create .Xmodmap file in your home directory and add lines for key mappings there.

In your case .Xmodmap should look like this:
```
keycode 115 = F13
keycode 116 = F13
```

---

### Post by hihp on 2008-05-01
Strange. I had tried creating an .Xmodmap file in the past, but that didn't work. now it does.

Another problem: while it did work once in the past, right now xfce refuses to work with both windows keys set to the same key, so I made the second Windows key be F14 and added a secong shortcut. Now it works.

I assume nobody knows a way to have a second press on the windows key close the menu again?

---

