---
title: "Ugly fonts in some apps under KDE"
date: 2006-08-23
forum: Desktop Environments
---

### Post by mycelo on 2006-08-23
I'm having this since I first installed KDE packages over my Ubuntu 6.06. Everything is OK under Gnome. But on KDE, some applications like Synaptic, though readable, present "washed out" fonts, like they were anti-aliased in a wrong way. Firefox fonts in webpages are also messed up, but not as bad.

The font-smoothing/antialiasing option is enabled (by default) in KDE control panel, and I upgraded KDE to its very latest version which didn't solved this problem. Changing Synaptic fonts to bold seem to amend the issue, but that doesn't sound like a good solution. I also didn't find any clear solution in this forum.

Any suggestions, please?

mycelo

[EDIT] That happens when apps are called with sudo.

[EDIT] See my last post for solution.

---

### Post by gunksta on 2006-08-23
> **mycelo said:**
> I'm having this since I first installed KDE packages over my Ubuntu 6.06. Everything is OK under Gnome. But on KDE, some applications like Synaptic, though readable, present "washed out" fonts, like they were anti-aliased in a wrong way. Firefox fonts in webpages are also messed up, but not as bad.

The font-smoothing/antialiasing option is enabled (by default) in KDE control panel, and I upgraded KDE to its very latest version which didn't solved this problem. Changing Synaptic fonts to bold seem to amend the issue, but that doesn't sound like a good solution. I also didn't find any clear solution in this forum.

Any suggestions, please?

mycelo

It sounds like you are using the default QT-GTK theme while in KDE. There is a section for GTK theming in the KDE control panel. It includes Font settings. Tweak those to improve things.

--andy

---

### Post by mycelo on 2006-08-24
I applied Human theme and Sans Serif 10 for GTK applications, but my fonts still look the same (read: ugly). ](*,) Also it seems that I can't smooth fonts for GTK things.

Could you be a bit more specific, please? :-D

mycelo

---

### Post by der_joachim on 2006-08-24
If you have a decent Nvidia video card and have configured the official drivers, try adding the following few lines in the "Device" section:
```

	Option   	"UseEdidDpi"   "FALSE"
	Option   	"DPI"   "96 x 96"

```

These will improve your fonts greatly. Note: I do not have a fancy TFT, and these settings may be CRT-only. Just experiment a bit.

---

### Post by mycelo on 2006-08-24
Sounds like a good solution, I'll try.

mycelo

---

### Post by mycelo on 2006-08-25
Still nothing.
And the problem seems restricted to Adept and Synaptic.
Even Galeon look nice.
Oh well.

mycelo

---

### Post by mycelo on 2006-08-27
I have some news.
I realized that I get ugly fonts in apps that I run as root.
So, my more direct question is, how can I smooth fonts for root in KDE?

mycelo

[EDIT] I figured it out by myself. I called "sudo kcontrol" and re-applied the font smoothing.

---

### Post by jonrkc on 2006-10-18
Thanks for posting the solution you found!  It will probably help a lot of people.  I'm scared to make the most recent update, as it is so large and I see users complaining right and left about things that are broken after it.  But someday I'll have to...   :(

Several times I've wondered what was making an app behave funny and realized I was running it as root.  (NOTE: I almost never log in as root, but sometimes it's a lot more convenient to do sudo -s than to type sudo before a dozen commands.)  Of course root's configuration has nothing to do with the regular user's.  It happened just yesterday--again--in fact.  

Oh, well.

---

### Post by mycelo on 2006-10-18
Surprises me how simple this issue was, and even so, the support staff failed to answer. Fortunately I could figure it out by myself.

Ubuntu really needs something like M$' knowledge base, forums are way too much messy to store problem/solution pairs.

---

