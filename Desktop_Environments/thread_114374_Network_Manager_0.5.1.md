---
title: "Network Manager 0.5.1"
date: 2006-01-08
forum: Desktop Environments
---

### Post by myke on 2006-01-08
The new version of Network Manager is available here:  [Network Manager]("http://www.gnome.org/projects/NetworkManager/").

It seems to have a lot of fixes over the one in the repositories which I believe is .4.   Two questions:   First, how do I install it once I've downloaded it directly as I'm assuming this newer version can't be added manually to the repositories (or am I wrong?)?   Second, how do I install it and add the applet to the top panel?   Ok ... that was more like 4 questions.   Right now I'm using gtkwifi which works pretty well but I'd like to see how NM works as well especially as I've read in the forums it will likely be included in Dapper Drake.

---

### Post by kwaanens on 2006-01-08
Use the one from the repositories instead. It works just peachy!

- Ketil

---

### Post by myke on 2006-01-08
I tried but I can't get the applet to show up so I uninstalled it.  The applet doesn't appear in this window when you go to 'add to panel' so I don't know how else to get it there.

---

### Post by kaamos on 2006-01-08
You run it from the terminal. I think the command was nm-applet.

---

### Post by kwaanens on 2006-01-08
That's right. Go to System > Preferences > Sessions > Start-up programs and add "nm-applet" to start it at login. If you put for instance 20 where 50 is, nm-applet will start earlier.

- Ketil

---

### Post by myke on 2006-01-08
I tried starting it from the terminal but nothing happens.  The applet doesn't start at all.


Back to my original question:  How would you install .5.1 if one wanted to install such a program?  The repositories are great but I don't want to be restricted to installing programs just that way.  I want to learn how to be able to install packages I download on my own as well.   I downloaded the tarball for .5.1 but don't know where to go from here.

---

### Post by myke on 2006-01-08
BTW == I've still got .4 from the repositories installed and I checked the system monitor and nm-applet is running.  However, the applet does not appear on either my top gnome panel or the bottom one so I have no access to it.   Any fix for this?

---

### Post by kwaanens on 2006-01-08
[QUOTE=myke]BTW == I've still got .4 from the repositories installed and I checked the system monitor and nm-applet is running.  However, the applet does not appear on either my top gnome panel or the bottom one so I have no access to it.   Any fix for this?[/QUOTE]

Is the system tray on the panel?
Did you get nm-applet from the repo at bootlab.org? (I had more or less the same problems with this, so I ditched it, and went with the official Ubuntu one instead)
If you start nm-applet from console, do you get any messages?

You could try removing network-manager completely (by use of Apt), then reinstall it, maybe there's something screwed up in your config.

---

### Post by myke on 2006-01-08
Hey, you were right.  The system tray is not on the top or bottom panel.  So, I logged out & logged back in as root (I've set root to be allowed thru gnome) and NM is there in the system tray.  I've apparantly removed the tray from my main user screen.  How do I get it back?   I checked in the 'add to panel' screen and didn't see it there.

---

### Post by kwaanens on 2006-01-08
On my system, when I right click the panel and click add to panel, it's the last one under utilities. (Using Norwegian language, so don't know what it's called in English)

- Ketil

---

### Post by myke on 2006-01-08
It's not under utilities within 'add to panel' nor anywhere else there that I can tell.   I still can't find it.


Edit:::::   I feel like an imbecile .. it is in the 'add to panel'.  It's just called "notification area".

---

### Post by kevin79 on 2006-01-08
Does anyone know if this verson (or 0.4) will work with wpa_supplicant to support WPA?

---

### Post by stardotstar on 2006-01-10
Edit:::: just saw your edit :)
[quote=myke]It's not under utilities within 'add to panel' nor anywhere else there that I can tell.   I still can't find it.


Edit:::::   I feel like an imbecile .. it is in the 'add to panel'.  It's just called "notification area".[/quote]

---

### Post by nocturn on 2006-01-10
Does the new version bring up connections at boot time (.4 only does this after login)?

That would make NM suitable for me...

---

