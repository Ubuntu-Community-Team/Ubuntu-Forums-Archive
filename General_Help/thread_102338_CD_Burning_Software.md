---
title: "CD Burning Software"
date: 2005-12-11
forum: General Help
---

### Post by JoshHendo on 2005-12-11
Is there any cd burning software for ubuntu (and works :P). I tried roxio via wine, though it didn't work (from my experience with wine, I wasn't expecting a program like that to work). Thanks :)

-Josh

---

### Post by kairu0 on 2005-12-11
It requires a lot of kde dependencies to get it installed, but k3b is the best in my opinion (even in gnome.)

---

### Post by utterlyjaded on 2005-12-11
[QUOTE=JoshHendo]Is there any cd burning software for ubuntu (and works :P). I tried roxio via wine, though it didn't work (from my experience with wine, I wasn't expecting a program like that to work). Thanks :)

-Josh[/QUOTE]


  Umm, there's gnomebaker, k3b, and nerolinux, they all work but work diffrently.  There are many others but I believe these 3 will cover everything you need, I reccamend k3b because it will do mostly everything and it has a nice GUI, If you need help with them just ask or search em up here in the forums.  Also enabling DMA on your drive/drives might be mandatory, I dunno.  :p

---

### Post by Adrian on 2005-12-11
You can also burn CD's using Nautilus.

---

### Post by 4linux on 2005-12-11
I have been using gnomebaker with no problems. 

-Pat

---

### Post by soulestream on 2005-12-11
I was always a fan of k3b, but i have been using gnomebaker and have been really happy.Plus you dont have to install half of kde to get it work, like with k3b.;) 

soule

---

### Post by taurus on 2005-12-11
And don't forget graveman too...  :)

---

### Post by JimmyBEng on 2005-12-11
[QUOTE=taurus]And don't forget graveman too...  :)[/QUOTE]

yeah, graveman has worked well for me.

---

### Post by kingsidy on 2005-12-11
I like k3b but found nerolinux burns less coasters

---

### Post by -DarkMind- on 2005-12-11
GnomeBaker for gnome

k3b for kde

:)

---

### Post by JoshHendo on 2005-12-12
I tried installing gnome baker and nerolinux. I have never managed to get 1 .deb file to be installed :P. I tried following the instructions on [http://ubuntuforums.org/archive/index.php/t-6365.html](http://ubuntuforums.org/archive/index.php/t-6365.html) , though it came up a error. The files were in my home file :)

-Josh

---

### Post by jeffreyvergara.NET on 2005-12-12
the only thing I like with K3B is that it support burning VCD directly from an .mpeg file. If gnomebaker will have this feature, defenitely I'll use gnomebaker, but for now, I'll stick with k3b.
And also I use amarok for playing mp3's and there a burn option that uses k3b.

---

### Post by Gray. on 2005-12-12
JoshHendo: just edit your /etc/apt/sources.list and remove all single #'s (leave ##'s) then save it and do:
```
sudo apt-get update && sudo apt-get install gnomebaker
``` GnomeBaker will install to Applications > Sound & Video > GnomeBaker

---

### Post by akiro.yamamoto on 2005-12-12
Or for a GUI way just use Synaptic.
Just ensure that you select Universe and Multi-verse under the repositories setting. Search for gnome baker...install...done. :smile:

---

### Post by patrickfromspain on 2005-12-12
I use k3b... gnomebaker doesn't work for me.

---

### Post by TmP on 2005-12-12
Is there a CD-DVD burning application for gnome, that supports multisessions, overburning, and is stable?

I wouldn't advise using Gnome's built in recorder - it messed up a few cd's of mine and didn't care to inform me about errors.

I'm using Gnome baker, but without multissesions and ability to recognise the size of inserted cd, it's barely usefull. It also freezes 1 in 10 times.

Is there a Nero for linux? Where can I get it? Is it free?

---

### Post by NotJustANewbie on 2005-12-12
I've never used gnomebaker... Since I've moved to Gnome from KDE, I still like K3B (even with all the clunky KDE dependecies) because it has soooo many cool features. :cool:  But then again, I use amaroK too for my music so I would have to apt-get the KDE dependencies on that too. amaroK in my opinion is far the best audio player... bar none.

---

