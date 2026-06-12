---
title: "font stopped for Brainparty in 18.04"
date: 2019-03-16
forum: Gaming &amp; Leisure
---

### Post by chopra on 2019-03-16
Hi All,
I upgraded to Ubuntu 18.04 a while ago, and since then, one of the minigames in the Brainparty game isn't displaying fonts properly. I get a bunch of wierd glyphs and question marks in boxes instead of sentences.

I noticed, in my /var/log/syslog file, there were the following messages:

Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: #011Entry deleted from font path.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: #011Entry deleted from font path.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: #011Entry deleted from font path.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: #011Entry deleted from font path.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
Satellite-E45-B /usr/lib/gdm3/gdm-x-session[1791]: #011Entry deleted from font path.

So, I installed them:
sudo apt-get install xfonts-75dpi
sudo apt-get install xfonts-100dpi
sudo apt-get install xfonts-cyrillic


afterwords, I got the following message in the log file:

Satellite-E45-B org.gnome.Evolution-alarm-notify.desktop[2287]: Fontconfig warning: Directory/file mtime in the future. New fonts may not be detected.

The problem still won't go away.  Not sure if it's related to the fonts or not.
Thanks, Chopra

---

### Post by thenailedone on 2019-03-16
Could you try running the below in terminal and then try again?

```
sudo fc-cache -f -v
```

If you are curious about the command above - [Link to online man-page]("https://man.cx/fc-cache").

---

### Post by chopra on 2019-03-18
Thanks for the tip. That didn't seem to help though.  The command said it suceeded, but the font is still gibberish.

---

### Post by Holger_Gehrke on 2019-03-23
If you're talking about the garbled or missing display of premises in the mini game 'symbolic logic', then it's not a font-problem. There's [a bug]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=922485") in the game. It's been fixed, but the patch only came out in February 2019, so it's not in the version that's in the list of packages for 18.04 in the repositories. There are new packages (brainparty_0.61+dfsg-5_amd64.deb and brainparty-data_0.61+dfsg-5_all.deb) but they are part of the next release, I think. I manually downloaded them from the repository, installed them through 'sudo apt install' and they do seem to work on my machine under XUbuntu 18.04.

Holger

---

### Post by chopra on 2019-03-25
Ah, yes, that's exactly what I was referring to. I thought it was odd that it was only that minigame, and only the premises, not the conclusions.
When you say you manually downloaded them from the repository, and then used sudo apt install, do you mean the repository linked to the message board that you linked to?
Thanks, Chopra

---

### Post by Holger_Gehrke on 2019-03-30
I meant the Ubuntu repositories. The repositories are just web-sites with a fixed structure that tools like apt or synaptic know and can navigate. You can browse a repository with a normal web browser, but finding packages that way is a bit of a chore. There's a search for packages at [https://packages.ubuntu.com](https://packages.ubuntu.com) that should lead to the right packages quite quickly, especially if you tell it to only show packages for the next release ('disco dingo').

Holger.

---

### Post by chopra on 2019-04-19
got it. thanks

---

