---
title: "Nomad Jukebox Zen"
date: 2005-10-02
forum: Desktop Environments
---

### Post by carlos1 on 2005-10-02
I'm trying to connect my Nomad Jukebox Zen and access it under Kubuntu.
I've tried everything I could find on Sourceforge, but most of them won't let me "make" after I get past the "configure", and the one that did (kionjb) gives me an error after launching, and doesn't open anything. 
Does anyone have experince with connecting their Nomad in KDE or specifically Kubuntu?

---

### Post by mlomker on 2005-10-02
I compiled the program and [created a .deb]("209.98.64.146/mlomker/libnjb-2.2.3_2.2.3-1_i386.deb") file for you.  I don't know that it'll work any better than yours did but it wasn't difficult to do, so you're welcome to try it.

**sudo dpkg -i libnjb-2.2.3_2.2.3-1_i386.deb** to install it.

---

### Post by carlos1 on 2005-10-04
Cheers - your .deb file worked and I have libnjb now. 
The problem I'm having now is trying to install any of the GUI apps - nomadsync, njbnavigator or kionjb. The first two don't make it past "./configure" and the last does, but after make and make install, when I launch I get an error loading it in konqueror. 
Do you know if there is a .deb file or a repository that might have this, allowing me to avoid the dependency issues which seem to be the problem?

---

### Post by shakin on 2005-10-04
Someone posted a deb on this thread: [http://www.ubuntuforums.org/showthread.php?t=42515](http://www.ubuntuforums.org/showthread.php?t=42515)

The first post links to a KZenExplorer deb and down a few posts there is a nomadsync deb.

---

### Post by carlos1 on 2005-10-04
Thanks - I tried both of these, but after installing they both say then can't access or find "libnjb.so.4". 
Is this something I can just find and install? I think it's supposed to be in the package I installed but it's not finding that particular file.

---

### Post by mlomker on 2005-10-04
Try:

```

sudo updatedb
locate libnjb.so.4

```

You might have to add the path to the /etc/ld.so.conf file and then run **ldconfig**.  Let me know if it finds it and we'll take a look.

---

### Post by carlos1 on 2005-10-05
Thanks - I tried this but the problem is I don't have libnjb.so.4 in /usr/local/lib or in /usr/lib.
I have libnjb.so.5 in /usr/local/lib, but it seems I need libnjb.so.4.
Is it siimply a matter of finding libnjb.so.4 and putting it in the file? I searched online for it but all I can find are RPMs.

---

### Post by mlomker on 2005-10-05
I checked and that's actually an older version of the file, so we should just try creating a symbolic link to the newer one.

Try this:

```

cd /usr/local/lib
sudo ln -s libnjb.so.5.0.0 libnjb.so.4

```

---

### Post by joshuai on 2005-10-05
[QUOTE=mlomker]I checked and that's actually an older version of the file, so we should just try creating a symbolic link to the newer one.
Try this:
```

cd /usr/local/lib
sudo ln -s libnjb.so.5.0.0 libnjb.so.4

```[/QUOTE]
Please excuse my noob-ness here.  So are you saying that if I have a newer version of a package installed, I can use a symbolic link to basically fool the system into using it?  I just installed both, would it have overwritten the libnjb 5?

---

### Post by mlomker on 2005-10-05
[QUOTE=joshuai]Please excuse my noob-ness here.  So are you saying that if I have a newer version of a package installed, I can use a symbolic link to basically fool the system into using it?  [/QUOTE]

That's right.  The package itself actually installed some symbolic links as well--that's one of the ways that linux handles being backward-compatible.  The filename changes but they point  to the same 'real' file.

---

### Post by joshuai on 2005-10-05
Interesting.  Thank you!

---

