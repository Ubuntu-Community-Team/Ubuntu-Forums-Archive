---
title: "Gnome Lock Screen"
date: 2013-05-05
forum: Desktop Environments
---

### Post by sccjono on 2013-05-05
[COLOR=#000000]Hello all, I'm still new to Linux in general so please excuse my ignorance. I have taken the plunge and installed 12.04 LTS 64bit on my laptop and for the most part I am more than happy.

However I have tried to switch over to Gnome and although most things are working OK, I am struggling to switch to the new lock screen. As far as I know I have chosen GDM over LightDM but I still get the original lock screen. I don't know if it is relevant but I also do not have an option to choose to shutdown the system from my user dropdown menu. I have to log out fist and then choose shutdown. Am I perhaps missing some packages?

Thank you,

[/COLOR]

---

### Post by Frogs Hair on 2013-05-05
If you are in the Gnome Shell install the Tweak Tool if not already and the Gnome Shell extensions. The extensions are enabled in the Tweak Tool / Advanced Settings. The alternative status menu extension displays the shutdown menu. I have not used 12.04 in a while, so I don't know if the procedure for installing extensions has changed. You may want check what current procedure is.

---

### Post by sccjono on 2013-05-07
Thank you very much for the tip about the shell extensions, that worked a treat, I now have the correct menu options.

Can anyone else help with regard to the lock screen?

Jon

---

### Post by Frogs Hair on 2013-05-07
Could you describe the problem more clearly , below is what I think of when you write screen lock .

---

### Post by sccjono on 2013-05-07
Perhaps I should call it the "unlock screen". I was told that Gnome now has the unlock screen [described here]("https://help.gnome.org/misc/release-notes/3.6/users-lock-screen.html.en_GB"). But mine is still showing one that looks the same as the Unity shell one. Somebody suggested that I needed to issue the following command to switch from LightDM to GDM but that has not helped.

```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo dpkg-reconfigure gdm[/FONT][/COLOR]
```

Jon

---

### Post by Frogs Hair on 2013-05-07
My dialog box uses what ever theme is applied (light GDM) . Try the command and restart if you are using GDM.

---

### Post by sccjono on 2013-05-07
Try what command? The one I posted? If so I have and it changes nothing.

Jon

---

### Post by Frogs Hair on 2013-05-07
> [COLOR=#000000] but that has not helped[/COLOR] Excuse me, If that doesn't work I have no suggestions, but you may be interested in the Gnome flavor if you are committed to Gnome . support for the latest release is only 9 months. [http://cdimage.ubuntu.com/ubuntu-gnome/releases/13.04/release/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/13.04/release/)

12.04 Remix [http://www.webupd8.org/2012/04/ubuntu-gnome-shell-remix-1204-available.html](http://www.webupd8.org/2012/04/ubuntu-gnome-shell-remix-1204-available.html)

---

### Post by markbl on 2013-05-07
FYI, I have a stock Ubuntu 13.04 64bit install (not Ubuntu GNOME) with gnome 3 ppa added and gnome-shell installed. I selected gdm after "dpkg-reconfigure gdm" and I do get that new gdm lock screen (screen timeout time in system systems).

---

### Post by Frogs Hair on 2013-05-07
The PPA may be the difference because they tend to be more complete and up to date than the version in the repository/software center.

---

### Post by sccjono on 2013-05-09
Could somebody please explain this Gnome PPA?

Can I install 13.04 on top of this without wiping my data etc?

Jon

---

### Post by markbl on 2013-05-09
> **sccjono said:**
> Could somebody please explain this Gnome PPA?
You will note I called it the "GNOME 3 PPA". You could have punched that into Google and the top link will tell you all you need to know.

> 
Can I install 13.04 on top of this without wiping my data etc?


A PPA is something you add to your 13.04 installation. Does not affect your data. You can remove it using ppa-purge.

---

### Post by sccjono on 2013-05-09
Yeah sorry I suppose I should have, but I assumed that it was a command I needed to know. Like I said I'm new to Linux in general and although I love it, the learning curve is steep.

I mean't could 13.04 install on top of my 12.04LTS.

So I took your advice and I did a lot of Googleing and I am now running 13.04 with all my problems fixed and even a few spurious weirdness things fixed too. Thank you all for your help. These fora are a goldmine.

Jon

---

