---
title: "vlc - gtk2 version"
date: 2005-11-20
forum: Deferred/Invalid Requests
---

### Post by maat on 2005-11-20
Hello!
There is in the dapper a [GTK2 version]("http://packages.ubuntu.com/dapper/graphics/vlc") of vlc, but the newest version works only partly on my breezy. Have you got any idea to do it working?

---

### Post by Mosey on 2005-12-12
[QUOTE=maat]Hello!
There is in the dapper a [GTK2 version]("http://packages.ubuntu.com/dapper/graphics/vlc") of vlc, but the newest version works only partly on my breezy. Have you got any idea to do it working?[/QUOTE]

I'm also quite interested in getting a GTK2 version of VLC running on my breezy machine...

Any ideas guys?

---

### Post by jdong on 2005-12-13
Alright, will give it a spin.

---

### Post by jdong on 2005-12-13
Does not build from source

libflac-dev too old in Breezy.

---

### Post by zbowling on 2005-12-24
I ran into this a while back and put a few posts on this on the vlc forum. VLC is fine, its just that wxWigets library was compiled with the gtk1 backend and not the gtk2 backend before the compile of VLC took place. If you grab the apt-source and rebuild changing the wxwidgets-config app it works. Its spell omething like. Its the app that tells the libraries and install paths. It staticly versioned in the build script and that app doesn't exist in any version of breezy i can get on, so it some what looks like it was built before the release of the current wxwidgets version was built and that app does exist in horay. I haven't checked testing yet.

---

### Post by zbowling on 2005-12-24
Ohh. libflac has to be built as well. It looks static in the binary in breezy/horay

---

### Post by Humanoid on 2005-12-25
Take it as a christmas present :)
[http://www.students.oamk.fi/~t3vasa02/ubuntu/vlc_0.8.4a-1_i386.deb]("http://www.students.oamk.fi/~t3vasa02/ubuntu/vlc_0.8.4a-1_i386.deb")

---

### Post by kaamos on 2005-12-25
Humanoid: Cheers. But..
> VLC media player 0.8.4a Janus
[00000240] main dialogs provider error: no dialogs provider module matched "any"
[00000239] skins2 interface error: No suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)
Couldn't gzopen /home/laisi/.vlc/skins2/default.vlt
[00000239] main interface error: no suitable access module for `/home/laisi/.vlc/skins2/default.vlt'
[00000239] skins2 interface error: Failed to open /home/laisi/.vlc/skins2/default.vlt for reading
[00000239] skins2 interface error: Failed to parse /home/laisi/.vlc/skins2/default.vlt
Couldn't gzopen share/skins2/default.vlt
[00000239] main interface error: no suitable access module for `share/skins2/default.vlt'
[00000239] skins2 interface error: Failed to open share/skins2/default.vlt for reading
[00000239] skins2 interface error: Failed to parse share/skins2/default.vlt
[00000239] skins2 interface: skin: VLC OSX Interface  author: BigBen
[00000250] main dialogs provider error: no dialogs provider module matched "any"
[00000239] skins2 interface error: No suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)
[00000251] main dialogs provider error: no dialogs provider module matched "any"
[00000239] skins2 interface error: No suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)
[00000252] main dialogs provider error: no dialogs provider module matched "any"

So it starts, but right click does not work, and neither do preferences. I'm running xubuntu on this machine, so don't know if this is due to some libraries missing.. Vlc from the repos (with gtk1) works fine though.
Mutta kiitti kuitenkin. :)

---

### Post by Humanoid on 2005-12-25
[QUOTE=kaamos]Humanoid: Cheers. But..

So it starts, but right click does not work, and neither do preferences. I'm running xubuntu on this machine, so don't know if this is due to some libraries missing.. Vlc from the repos (with gtk1) works fine though.
Mutta kiitti kuitenkin. :)[/QUOTE]

I'm running xubuntu too. Maybe it needs wxWidgets (wx-common etc.. don't remember the package names)?

---

