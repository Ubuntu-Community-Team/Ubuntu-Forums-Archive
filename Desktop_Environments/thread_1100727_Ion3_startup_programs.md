---
title: "Ion3 startup programs"
date: 2009-03-19
forum: Desktop Environments
---

### Post by Samppa0 on 2009-03-19
Hi all,

I've been using (K)Ubuntu for a few years, and gotten enough of KDE's slowness (old laptop). I installed Ion3, which to my surprise I like mucho, but I'm experiencing a few quirks.

First of all, and more pressingly, I can't get sound to work properly. I've tried to find a command for starting a sound mixer, but the best I've achieved is occasional success with running kmix or kmixctrl. Not ideal, so I was hoping someone could give me heads up as to what I should do to get sound working properly. Using KDE sound works perfect.

Secondly, I don't has the internet until I run knetworkmanager. I've dodged the issue so far with a keyboard bind, but I'd like to have it start up automatically. I've tried adding knetworkmanager to my .profile file but in this instance the net manager is broken and does not work properly (the icon does appear though).


I'm the only one using the computer and will reinstall some time during the summer, so I'm not looking for an elegant solution (as you might have gathered). I just need any patched, hacked, half-broken solution so I don't have to bother with start up jobs every time I boot (and having no sound).

I hope you have a solution for me, help would be appreciated as I can't figure out what's wrong myself.

---

### Post by olejorgen on 2009-04-14
I don't think ion supports the fdo (or whatever) startup standard. The typical way is to put them in your ~/.xinitrc

```

knetworkmanager &
# other startup programs. (dont forget to start them in background with '&'

exec ion3

```

Then you choose run xinit script in the session selection before you log in.

You can make programs run from a lua file too.

```

os.execute("knetworkmanager &")
-- ...

```

Just ask if you have further trouble

PS: I'm not sure about the sound thing. It should work without starting some strange program. Or has that changed with pulseaudio?

---

