---
title: "Can't play audio CD's on Amorak"
date: 2006-07-31
forum: Desktop Environments
---

### Post by FooAtari on 2006-07-31
I am using Amarok on Gnome, great media player, but I cant play Audio CD's, the Play Audio CD option under the Actions menu is greyed out.

Had a hunt around here and google but can't seem to find an answer.

Can play CD's no problem via Rhythmbox, but it isn't as good Amarok.

Any suggestions?  Thanks

---

### Post by Paerez on 2006-07-31
Dumb question but, have you checked amarok's preferences to make sure that the cd drive is pointed to the right place?

---

### Post by FooAtari on 2006-07-31
Um, how? :)

Had a look but can't find that option

---

### Post by Paerez on 2006-07-31
I don't have amarok here at work sorry, so I can't try to find it. I was hoping there was something like mplayer where it has an option for specifying your cd device. Maybe under engines.

---

### Post by FooAtari on 2006-07-31
engines?

---

### Post by Paerez on 2006-07-31
Settings->Configure Amarok->Engine

ok I checked it out at home, and I have amarok using the Xine engine. Then I can open up gxine and set the cdrom device, but it defaults to /dev/cdrom, which works for me. Try the xine engine.

---

### Post by sleepkreep on 2006-07-31
You're going to have to wait for KDE4 for this one.  The problem is that Amarok uses the audiocd:/ kioslave to read CDs.  audiocd:/ is horribly slow and can't seek at all.  KDE4 will change all that.  The one benefit to using audiocd:/ is it doesn't matter which drive your CD is in.  The KDE Media manager will automatically figure that out for you.

---

### Post by FooAtari on 2006-08-01
Im actually use Gnome....  I might try "Listen, just Listen" that I read about here.

---

### Post by Paerez on 2006-08-01
Amarok is great for playing music because of its dynamic playlists, but if you're just listening to a cd, I would just use something simple like xmms or rhythmbox.

Listen is pretty cool too though.

---

