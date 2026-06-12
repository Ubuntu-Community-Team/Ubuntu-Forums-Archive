---
title: "[SOLVED] Some Apps don't follow Theme"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by arigram on 2007-12-09
I have a dark theme for my Ubuntu 7.10 desktop and although most of the applications and dialogs work well, some don't follow the rest looking like some default GTK+ scheme.
For example:
Synaptic looks like this:
[IMG]http://i184.photobucket.com/albums/x247/arigram/Screenshot-SynapticPackageManager.png[/IMG]

instead of looking like GnomeBaker does:
[IMG]http://i184.photobucket.com/albums/x247/arigram/Screenshot-GnomeBaker.png[/IMG]

Why is that and what can I do to fix it?

---

### Post by qamelian on 2007-12-09
Apps that behave like this are either not GNome/GTK apps or they are being run as another user. In you example, Synaptic is being run as the superuser and is therefore inheriting the default them of the superuser. This can be fixed by doing the following in a terminal:

```
sudo ln -s ~/.themes /root/.themes
```

This will link roots .themes folder to your own and allow apps run with sudo to use your chosen theme.

---

### Post by arigram on 2007-12-09
Thank you Qamelian!
Your answer not only came in speed of light but also did the trick!

I think the Ubuntu team if they are renewing the Theme for 8.04 they should have this "fixed" by default to eliminate any lapses in aesthetics and retain the smoothness of the user experience.

---

### Post by qamelian on 2007-12-09
> **arigram said:**
> Thank you Qamelian!
Your answer not only came in speed of light but also did the trick!

I think the Ubuntu team if they are renewing the Theme for 8.04 they should have this "fixed" by default to eliminate any lapses in aesthetics and retain the smoothness of the user experience.
Actually, some users prefer this differentiation because it provides an immediate visual cue that you are running an app as the super-user rather than as a normal user. Also, this "fix" really only works properly if you are the only user on the PC. If a second user has sudo privileges and is using a different theme than yours, any apps they run under sudo will not match their chosen theme.

---

### Post by pointfivezero on 2007-12-10
> **qamelian said:**
> Actually, some users prefer this differentiation because it provides an immediate visual cue that you are running an app as the super-user rather than as a normal user. Also, this "fix" really only works properly if you are the only user on the PC. If a second user has sudo privileges and is using a different theme than yours, any apps they run under sudo will not match their chosen theme.

Indeed. On my system, the root user has a deep red for selection backgrounds and mouseover highlights (an option for KDE style: polyester) to distinguish it from other user interface elements.

My $0.02

---

### Post by qamelian on 2007-12-10
> **pointfivezero said:**
> Indeed. On my system, the root user has a deep red for selection backgrounds and mouseover highlights (an option for KDE style: polyester) to distinguish it from other user interface elements.

My $0.02

It's a good practise. Many tragedies have occurred because users have forgotten they were working as root / super-user. Personally, I always like to have that little nudge. I've been a Linux user long enough to know that there is no such thing as too careful!

---

### Post by arigram on 2007-12-10
Asking for my password is more than enough for me!
After all, its far easier to do something damaging with the terminal than with the GUI.

I think there should be a visual indication of the "super-user" status on GUI applications, maybe via GTK+ or Compiz, for example, maybe a red line around the Window Decoration or a differently colored Window Title, or something similar.
Going back to a vastly different looking GUI when using some common administrative applications such as the Synaptic derived ones (Update, Add new programs, etc) breaks the whole immersion with the system and makes the GUI look unpolished, especially to a new user or onlooker.
Consider also that most applications even most Administrative ones don't break the aesthetics and follow the user theme.

Anyway, that's beyond the point of the thread.
Thank you for your help.

---

### Post by usien on 2007-12-24
slightly off topic but arigram can you please post the link for the black theme?
it looks great!
:)

---

### Post by arigram on 2008-01-03
> **usien said:**
> slightly off topic but arigram can you please post the link for the black theme?
it looks great!
:)

The theme is called Neutronium.
You will excuse me for not posting a link because Gnome-Look.org has a few variations of it and I thought you would like to try them all and I can't seem to register a link with the website's search results.

I hope you get my reply as it is pretty easy to miss a post in this forum as I did originally with yours.

Salam Alekum!

---

