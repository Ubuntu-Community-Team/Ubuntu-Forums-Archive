---
title: "Steam - 'C:\windows\temp\GLF3f6f.tmp' error"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2007-05-10
When I try to open Steaminstall.exe in Fiesty and the latest  release of wine from automatix I get the following error

The file 'C:\windows\temp\GLF3f6f.tmp' could not be opened' Please check that you disk is not full and that you have have access to the destination directory. Acess denied.

Do I need to open it in terminal as Sudo or something?

---

### Post by rai4shu2 on 2007-05-10
Looks kind of like this bug:

[http://bugs.winehq.org/show_bug.cgi?id=8164](http://bugs.winehq.org/show_bug.cgi?id=8164)

---

### Post by foundation on 2007-05-10
So.. what's happening with the bug ? Is there a workaround or do we have to wait until the next Wine release (Is it out ?) ?

---

### Post by rai4shu2 on 2007-05-10
The patch was committed after the most recent release, so you'll likely have to wait till at least 0.9.37.

---

### Post by DiJEH on 2007-05-10
How frustrating :/

Thank you for the help. Do you have any idea when it'll come out?

---

### Post by rai4shu2 on 2007-05-10
If they stick to their 2-week updates, probably some time tomorrow.

---

### Post by buttons on 2007-05-10
You could always downgrade and then install it...

Just open synaptic, find wine, highlight it, and press Ctrl+E (or choose Force Version from the menu), and select one earlier than 0.9.36.

---

### Post by Saphira on 2007-05-10
Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com)   [http://ubuntuguide.org](http://ubuntuguide.org)   [http://doc.gwos.org](http://doc.gwos.org) for better help. 

Automatix is known for breaking systems and you'll find that you really don't need it. It may also make upgrading your system later difficult.  With Feisty most of the stuff you'll use automatix to install is already a one click install either via add/remove applications or by referral to one of the above sources.

---

### Post by foundation on 2007-05-11
Buttons, I installed Wine .33 and Steam is installing now, thanks.

Sapihra, is Automatix really that bad ?

A question, is there a way I can easily browse to the Valve/Steam folder ? It's just I don't want to re-download the big .GCF files so I was hoping to just copy them across . .

---

### Post by buttons on 2007-05-11
> **foundation said:**
> Buttons, I installed Wine .33 and Steam is installing now, thanks.

Sapihra, is Automatix really that bad ?

A question, is there a way I can easily browse to the Valve/Steam folder ? It's just I don't want to re-download the big .GCF files so I was hoping to just copy them across . .

Should be in your ~/.wine/drive_c/Program\ Files/Steam/ folder.  If you're using nautilus, press ctrl+h to show hidden files/folders, and browse to .wine

In this case, the version of wine in the automatix repos is identical to the one in wine's own.  He's simply stating that anything not in official repositories has the potential to be broken, but that should be implicit anyway.  Also, when you do a distribution upgrade it's not always the case that there exist packages for the new one, leading to incompatibilities with third-party packages.

Once again, though, this is wine and that's not going to be a problem.  This was a relatively harmless regression that will be corrected.

---

### Post by foundation on 2007-05-11
Ah ok, well I'll avoid Automatix when possible (Most of the time it seems) and I found the folder, thanks again.

How do I hide the panels ?

[[IMG]http://img513.imageshack.us/img513/268/steamxb6.th.png[/IMG]](http://img513.imageshack.us/my.php?image=steamxb6.png)

---

### Post by jimminy_kriket on 2007-05-11
Try setting up wine to emulate a virtual desktop using winecfg.

[x] Emulate a virtual desktop 
Desktop size: 1024  x  748

---

### Post by buttons on 2007-05-11
It should do fullscreen if beryl is disabled.  Setting up a virtual window is a bit of a hack.

---

