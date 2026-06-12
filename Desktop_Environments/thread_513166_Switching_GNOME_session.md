---
title: "Switching GNOME session"
date: 2007-07-30
forum: Desktop Environments
---

### Post by plodonium on 2007-07-30
Hello.

I'd thought I'd experiment with using Openbox as the WM for GNOME. Rather than altering my existing setup, I created a new session in gnome-session-properties. The problem is it's not appearing in GDM, and there is no option to select a session when GNOME starts.

Looking at the man page for gnome-session, it says that the session should appear in ~/.gnome2/session (which it does), and that the CurrentSession key in ~/.gnome2/session-options selects it. So I tried putting CurrentSession=Openbox in there, but nothing happened.

The same man page also says that gnome-session can take the session name to use on the command line, and I vaguely remember that it's possible to edit the commands the login manager runs to start sessions, but I can't remember where this is stored. Actually, I've just realised that the man page for GDM will probably tell me, but I'd rather get GNOME to select it's session, rather than hacking this, anyway.

Any help appreciated.

Cheers,
Plodonium.

---

### Post by Majlo on 2007-07-30
Hi 

I think this howto could help you
[http://ubuntuforums.org/showthread.php?t=192106&highlight=Openbox](http://ubuntuforums.org/showthread.php?t=192106&highlight=Openbox)

---

### Post by urukrama on 2007-07-31
Are you using Ubuntu Feisty (7.04)?

If so, download the latest version of Openbox [here]("http://icculus.org/openbox/releases/openbox_3.4.3-0ubuntu1_i386.deb"), and you will have a two openbox sessions in GDM: one for pure openbox (called 'Openbox'), the other for Gnome with Openbox (called 'Gnome/Openbox'). For more information, see [here]("http://icculus.org/openbox/index.php/Help:GNOME/Openbox").

---

