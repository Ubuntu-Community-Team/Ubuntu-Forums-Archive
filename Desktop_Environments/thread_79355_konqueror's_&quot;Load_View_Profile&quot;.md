---
title: "konqueror's &quot;Load View Profile&quot;"
date: 2005-10-20
forum: Desktop Environments
---

### Post by stepore on 2005-10-20
Where is the "Load View Profile" in konqueror's Settings menu? I see a "Save View Profile" under Settings, but no "Load View Profile". What gives? I know it was there in Warty.

Even the khelpcenter says this about konqueror:
"To modify a view profile (say, the Web Browsing profile), load the profile with Settings->Load View Profile->Web Browsing, and change the Konqueror settings to whatever you want." My konqueror doesn't have it. anyone else?

What's up?

cheers.

---

### Post by shakin on 2005-10-20
Works fine for me, although given Konq's profile bugs I'm not surprised whenever I hear about it not working for someone. I'm on KDE 3.5 Beta 2, so you might want to consider upgrading if you're on 3.4.

Anyway, Konq won't correctly load a profile when passed one on the command line (eg. setting a shortcut to open konq in web browser mode won't properly resize the window, but selecting the web browser profile from the menu will).

I recommend using only one knoq profile. If you really want to use it as a web browser then use something like Krusader for your file manager. If you want to use the konq file manager then use Firefox for your browser.

---

### Post by stepore on 2005-10-20
[QUOTE=shakin]Works fine for me, although given Konq's profile bugs I'm not surprised whenever I hear about it not working for someone. I'm on KDE 3.5 Beta 2, so you might want to consider upgrading if you're on 3.4.[/QUOTE]
I got it working by copying a backup of konqueror.rc from Hoary and replacing the konq-kubuntu.rc file in ~/.kde/blablabla.

Since you're here can i ask you something i've always wanted to figure out, but never have, yet. I'm using kde 3.4.3 (of course!) it's what comes with K/Ubuntu. How the hell do you upgrade just kde and not the entire distro. I've tried compiling from source (years ago) and never got it to work. How did you manage?

cheers,
johnny

---

### Post by rigga on 2005-10-21
Just press F9 when you launch konq and then save that setting as the filemanager profile.  F9 turns on the sidebar, not sure why this has been disabled by default, I think konq is a great filemanager, everything you need in one app.

---

### Post by shakin on 2005-10-21
[QUOTE=stepore]I got it working by copying a backup of konqueror.rc from Hoary and replacing the konq-kubuntu.rc file in ~/.kde/blablabla.

Since you're here can i ask you something i've always wanted to figure out, but never have, yet. I'm using kde 3.4.3 (of course!) it's what comes with K/Ubuntu. How the hell do you upgrade just kde and not the entire distro. I've tried compiling from source (years ago) and never got it to work. How did you manage?

cheers,
johnny[/QUOTE]


Kubuntu.org has provided repositories for KDE 3.5 beta 1 and beta 2. Beta 2 has a major artsd bug, so if you don't want to mess around with downgrading artsd to the beta 1 version you should just install beta 1 and don't upgrade until a newer beta or the final version comes out.

Here are the repositories from my sources.list:
```

# kde 3.5 beta 1
deb http://kubuntu.org/kde35beta1 breezy main

# kde 3.5 beta 2
deb http://kubuntu.org/packages/kde35beta2 breezy main

```

---

### Post by shakin on 2005-10-21
[QUOTE=rigga]I think konq is a great filemanager, everything you need in one app.[/QUOTE]

I thought Konq was the best file manager ever until I took the time to learn Krusader. Krusader's dual panes takes a bit of getting used to, but as a web developer it's really useful to be able to create a shortcut that sets one pane to my development directory and another using fish:// to my live site. I have separate Krusader shortcuts for all my usual work items. Each pane can also have its own tabs.

The best part is that using Krusader frees up Konq as a web browser, allowing me to finally switch from Firefox.

---

