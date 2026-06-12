---
title: "Vlc"
date: 2006-01-19
forum: Desktop Environments
---

### Post by nocturn on 2006-01-19
I just installed VLC this morning (from universe).

I get the wxwidgets interface (very ugly though, no font aliasing), but the skins do not work.

What can I do to make it use a skin? or at least have it anti-aliased

---

### Post by vruum on 2006-01-19
there's a gnome-vlc package, that might help, I don't know if it's skinnable though

---

### Post by engla on 2006-01-19
I can't get wxwidgets to work (I think). I have managed to skin VLC, but there are problems:
1. The skins are ugly
2. Moving the window lags awfully
3. The interface is crippled.

I just want the standard vlc interface, but with the gnome look. Why is it not possible?

---

### Post by kaamos on 2006-01-19
I have a deb of vlc compiled with gtk2 and wmv9 support. I originally found it from Jons blog [here](http://nanocrew.net/2005/09/01/compiling-vlc/). Since the link there no longer works, I uploaded the deb here -> [http://www.niksula.hut.fi/~alaisi/ubuntu/](http://www.niksula.hut.fi/~alaisi/ubuntu/)

---

### Post by engla on 2006-01-19
[QUOTE=kaamos]I have a deb of vlc compiled with gtk2 and wmv9 support. I originally found it from Jons blog [here](http://nanocrew.net/2005/09/01/compiling-vlc/). Since the link there no longer works, I uploaded the deb here -> [http://www.niksula.hut.fi/~alaisi/ubuntu/](http://www.niksula.hut.fi/~alaisi/ubuntu/)[/QUOTE]
We really need a package for this kind of thing.. can it be made, easily? You see I need this for ppc, and I'm guessing your deb is for i386.

---

### Post by kaamos on 2006-01-19
Yes the deb is for i386. Sorry, forgot to mention that.

The blog entry has instructions to compile vlc on breezy, so I guess someone that has access to a ppc system could create a simple deb by using checkinstall. You could try this yourself by changing the last line in Jons instructions to
```
sudo apt-get install checkinstall
make ; sudo checkinstall
```

---

### Post by nocturn on 2006-01-19
Thanks Kaamos, I'll try that.

---

### Post by gunksta on 2006-01-19
IIRC from the mailing list, there was a mistake made in compiling VLC for Breezy.  Instead of using GTK2 with wxWidgets, they compiled it against GTK.  I'm oping this will be fixed for Dapper.

---

### Post by nocturn on 2006-01-19
[QUOTE=gunksta]IIRC from the mailing list, there was a mistake made in compiling VLC for Breezy.  Instead of using GTK2 with wxWidgets, they compiled it against GTK.  I'm oping this will be fixed for Dapper.[/QUOTE]

I think it already is.

---

### Post by engla on 2006-01-19
I solved this problem on my install: use Backports.

I installed vlc and wxvlc from Breezy-Backports (vlc 0.8.4 vs previous .1 or .2)

Now it works and it looks really nice! And no crashing with wxwidgets

---

### Post by nocturn on 2006-01-20
[QUOTE=engla]I solved this problem on my install: use Backports.

I installed vlc and wxvlc from Breezy-Backports (vlc 0.8.4 vs previous .1 or .2)

Now it works and it looks really nice! And no crashing with wxwidgets[/QUOTE]

I can't find it in backports... are you using i386?

---

### Post by engla on 2006-01-20
[QUOTE=nocturn]I can't find it in backports... are you using i386?[/QUOTE]
Nope, my system is ppc, and it was there for me... I'm not at that computer right now so I can't check the specifics though.

---

### Post by kjempe on 2006-02-01
Try installing an older version from this site:

[http://ftp.riken.jp/Linux/ubuntu/pool/universe/v/vlc/?C=D;O=A]("http://ftp.riken.jp/Linux/ubuntu/pool/universe/v/vlc/?C=D;O=A")

For me, the vlc, wxvlc and alsa-plugin packages were enough. Installing the packages produced dependency-complaints which you can simply ignore. Installing the three packages will work. To avoid getting the update-notification constantly, just block the versions of these three in Synaptic.

---

### Post by Perfect Storm on 2006-02-01
Compile it if you want it your way ;)

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

I've done that and it works like a charm, though also enable gtk2 flag.

---

### Post by SubWolf on 2006-05-07
VLC V0.8.5 came out yesterday with some fantastic improvements. If someone else doesn't come up with a good package for it I may have to have a go myself.

:)

---

### Post by Perfect Storm on 2006-05-08
ah, back to compiling since I've have 0.8.4a

---

