---
title: "LightDM Ignores Compose Key"
date: 2012-07-22
forum: Desktop Environments
---

### Post by theexternvoid on 2012-07-22
I use a password that requires the use of the compose key. It's just more secure that way. Never had a problem with this on Mac OS for years.  After LightDM replaced GDM, it stopped working until I figured out to add XKBOPTIONS="compose:ralt" to /etc/default/keyboard. But then this week after some software updates came through the compose key stopped working in LightDM again, even with XKBOPTIONS="compose:ralt"!  This stinks because I can't login unless I switch back to GDM. I prefer LightDM. Anyone have an idea what's going on?

---

### Post by Paddy Landau on 2012-07-24
Interesting. I have just tried, and on my system it is still recognised (12.04 64-bit fully updated).

It is never recommended to use anything that you cannot easily type from a keyboard, so I strongly recommend that once you recover from this, you change your password to avoid using the compose key. Adding just a single character to your password will make it more secure (see [GRC's Password Haystack]("https://www.grc.com/haystack.htm"); take it with a pinch of salt, but you'll get the idea).

In the meantime, are your folders encrypted? If not, the fanciest password in the world is not going to protect your data! Simply boot into recovery mode and enter the following command to reset your password (replace [FONT=Lucida Console]theexternvoid[/FONT] with your user name):```
passwd theexternvoid
```If your folders are encrypted, try booting into recovery mode and signing into your user with this command:```
su theexternvoid
```If that works, you should be able to change your password with:```
passwd
```

---

### Post by Paddy Landau on 2012-07-24
I forgot about [a bug in the Recovery Mode in 12.04]("https://bugs.launchpad.net/ubuntu/+bug/996454").

As soon as you boot into Recovery Mode, before doing anything else, enter the following two commands:
```
mount --options remount,rw /
mount --all
```

---

### Post by theexternvoid on 2012-07-24
Thanks for the response and the recovery tips, but good news is that I already had it recovered.
 
Call me stubborn, but since I've been using compose key passwords on the Mac for years I'd love to keep doing so. Since it works for you, could you post or send me a copy of your keyboard config files? /etc/default/keyboard and I think there is also an xorg.conf.d directory somewhere out there.

---

### Post by Paddy Landau on 2012-07-25
> **theexternvoid said:**
> ... could you post or send me a copy of your keyboard config files? /etc/default/keyboard and I think there is also an xorg.conf.d directory somewhere out there.
Find the files attached.

[LIST]
[*]/etc/default/keyboard: [ATTACH]221767[/ATTACH]
[*]/usr/share/X11/xorg.conf.d: [ATTACH]221766[/ATTACH]
[/LIST]
 I have been revising Compose keys, and I remember that in  fact there are three different types. So, to be sure that I have  tested the right thing, please let me have an example of a character  that you have used.

For reference, here are some examples (I tested only the €); obviously, your keyboard may differ slightly from mine. The  compose key on my keyboard is AltGr; I presume it differs on the Mac  keyboard.

Note also that Compose+Shift gives a different result from Shift+Compose.

[LIST=1]
[*]Dead key:
[LIST]
[*]Press 4 to give 4
[*]Press Shift+4 to give $
[*]Press Compose+4 to give €
[*]Press Compose+Shift+4 to give ¼
[/LIST]
 
[*]Compose key:
[LIST]
[*]Press Shift+Compose, e, ' to give é
[*]Press Shift+Compose, Shift+E, ' to give É
[/LIST]
 
[*]Unicode key:
[LIST]
[*]Press Ctrl+Shift+U, 2, 1, 1, 6, space to give &#8470;
[/LIST]
 
[/LIST]

---

### Post by theexternvoid on 2012-07-25
First off thanks for trying to help. It's nice to see that the Ubuntu community has folks willing to help each other. Sometimes this system is frustrating, but overall I don't think I could ever go back to Mac OS after using Ubuntu. It's come a long way since I gave up on KDE 12 years ago! And of course Winblows was always off the table.

I figured out the problem. In order to get the compose key to work in LightDM, I hacked a keyboard layout file. Then I forgot, thought it was the X11 keyboard config instead. So user error.

Looking at the last modified time stamps, I see that there must have been a recent update to the keyboard layout package, probably overwrote my hack. Good news is that I found a keyboard layout that will get me the characters I need on an American keyboard. LightDM lets me choose a keyboard layout, and if I use default layouts then I don't neeed to worry about updates zapping my changes.

So in case anyone else has this same problem, hopefully they will find this thread and learn to never hack the keyboard layout files!

---

### Post by Paddy Landau on 2012-07-26
It's so easy to forget about those little changes! I always document what I've done and still I occasionally forget.

Anyway, it's great that you have managed to figure it out without a hack this time.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

