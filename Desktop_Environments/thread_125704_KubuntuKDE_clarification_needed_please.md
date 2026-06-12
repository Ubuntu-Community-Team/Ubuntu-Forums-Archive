---
title: "Kubuntu/KDE clarification needed please"
date: 2006-02-04
forum: Desktop Environments
---

### Post by seakiwi on 2006-02-04
It seems that just when I think I'm getting my head around all this, something crops up to render me totally confused again :( 

Can someone please clarify a couple of things for me.

I am running Kubuntu Breezy 5.10 installed as a clean install from a Kubuntu install CD. Current version of KDE is 3.5.0 - I have not upgraded KDE since installing Kubuntu. I was under the impression that Kubuntu was Ubuntu with the "full" KDE install as opposed to Gnome. However I was just browsing through upgradeable/not installed packages in Synaptic (I prefer Synaptic over Adept) and I see that there are a heap of KDE related bits and pieces that are not actually installed, including KDE-base. Now I was also under the impression that KDE-base was the minimal package required to run the KDE desktop, so if that's the case how come it's showing as not installed even though I'm obviously using the KDE desktop? Is there any advantage to me installing it now? There are so many KDE packages listed that I now no longer have a clue what is what - I thought I had the **full** KDE package but apparently that's not the case at all. If someone could enlighten me about this I'd appreciate it.

My second question relates to sudo, which is apparently something else I've misinterpreted. Prior to installing Kubuntu I did a lot of reading of tutorials etc and printed out a stack of basic instructions for things such as installing packages etc. Included somewhere amongst all that was the instruction to use *sudo -s * for doing things from konsole that required sudo. Is that correct or not? I've got my head around the sudo apt-get stuff now but there are still times where I'm not entirely sure that I'm using sudo correctly. I now see kdesu mentioned a lot and I have no clue now which one I should use for which situations. I do like the sudo concept - I like that it protects me from my limited linux knowledge and my inherent ability to screw things up! But if I'm using it incorrectly I guess in some situations that could be equally as "hazardous" as using root would be. I have read several tutorials on sudo too, but I'm still not "getting it".

Can someone please clarify all this for me? Many thanks!

---

### Post by Qrk on 2006-02-04
Don't worry about KDE-base, its a meta-package. That means it doesn't actually do anything, it just has the basic parts of KDE as dependencies. Its provided as a convience, basically for a GNOME user who wants to be able to run a KDE app without installing the other parts of KDE. The other KDE packages that aren't installed are probably add ons and accessability packs... you don't need them if you don't want them.

---

### Post by seakiwi on 2006-02-04
[QUOTE=Qrk]Don't worry about KDE-base, its a meta-package. That means it doesn't actually do anything, it just has the basic parts of KDE as dependencies. Its provided as a convience, basically for a GNOME user who wants to be able to run a KDE app without installing the other parts of KDE. The other KDE packages that aren't installed are probably add ons and accessability packs... you don't need them if you don't want them.[/QUOTE]

OK, so my next question is ... 

I'd like to upgrade KDE to the latest v.3.5.1 - so which package (looking within Synaptic) am I upgrading? Or is the lastest upgrade not yet available via Synaptic? I just ran a check for updates but nothing that looked remotely KDE'ish showed up. If I look at "not installed" packages with Synaptic - the package named *kde* is still showing as *not* being installed. I'm still not getting this :???:  When people use the generic term *KDE* in their posts it's becoming increasingly obvious that they may not all be referring to exactly the same thing! Exactly **which** KDE package comes as the default package with a Kubuntu clean install? 

I am totally lost here now ... :confused:

---

### Post by Qrk on 2006-02-04
The package listed as KDE in synaptic is a metapackage as well. Rest assured you have KDE... its just called kubuntu-desktop. This is why they use metapackages in the first place. The idea is that instead of selecting every package individually, you just use one. If you look at the KDE package and the kubuntu-desktop package you will find that kubuntu-desktop includes all of the real parts of the package "KDE" (or just about all of them) Just remember the package "KDE" itself doesn't do anything. 

Others mention KDE because it is the name of the desktop, not because of the package.

For KDE 3.5.1, there isn't an easy upgrade. Your best off sticking with the KDE provided.

But if you still want to upgrade, do:

```
sudo kate /etc/apt/sources.list
```

Then add thist line to the bottom of the file:

```
deb http://kubuntu.org/packages/kde351 breezy main
```

and back to the terminal for a:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by seakiwi on 2006-02-04
Ah, ok - NOW I get it! Many thanks for that  :)

If I do decide to upgrade as per your instructions, is this a "safe" upgrade as in I'm not likely to strike any glitches, or would I be better to hold off for a week or two until any bugs are ironed out?

This may, of course be my "Windows thinking" at work, but it's best to check these thing. At this point I don't want to break anything. 

Thanks again!

---

### Post by Qrk on 2006-02-04
Unless there is something specific you don't like about KDE 3.4.3, or if you really like a new feature of KDE 3.5.1 you don't need to upgrade. KDE 3.5 was an evolutionary release.

But it should be fairly safe to upgrade because the packages are official kubuntu ones. 

If you don't upgrade, KDE 3.5 will be provided in the next release of Kubuntu, which is due in April.

---

### Post by aysiu on 2006-02-04
```
sudo kwrite
``` seems to be more reliable than ```
sudo kate
```

---

### Post by FlakJacket on 2006-02-05
I remember once i was told while trying to build from source that i had two versions of glib and that i needed to uninstall the older one.  I went in adept and hit uninstall and the it started show packages it was uninstalling including kubuntu-desktop and adept.  I was like "holy cow!" and shut adept but the damage was already done. Nothing was functional in the gui and without adept it woulda been hella hard to get everything back so I ended up formatting my Kubuntu partition and reinstalling. This was lessened by the fact the install was only a few days old but the lesson I learned was _don't uninstall system packages unlesss you know exactly what will be uninstalled and what will be affected_. Speaking of compiling from source does anyone have a tutorial for doing it and what packages you need?  I sourta know from some tutorials but i'm still a bit shaky.

Flak

---

