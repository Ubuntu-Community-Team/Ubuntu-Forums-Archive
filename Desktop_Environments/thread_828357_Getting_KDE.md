---
title: "Getting KDE"
date: 2008-06-13
forum: Desktop Environments
---

### Post by bmcase on 2008-06-13
I am trying to put KDE4 on my laptop using synaptic; but I'm getting 404Error messages for 153 out of 200 packages. Worked fine for my PC; but 3 days of nada for the laptop. Has it been removed? Do I have to choose between an even older version and the new Beta?

---

### Post by soccerboy on 2008-06-13
what command are you using to install it?
kubuntu-desktop or kde4

It should work.  The version in the repos is current.  404 is a file not found so try to issue sudo apt-get update

---

### Post by bmcase on 2008-06-13
I clicked on KDE4 in Synaptic Package Manager. But it keeps telling me that 153 of the 200 files needed are 404. I know that is a "fnf" error. And after 3 days in a row, I don't think that the files needed are on the server that synaptic thinks they are on. I'll try searching for "kubuntu desktop". What else should I try?

Thanks...

---

### Post by soccerboy on 2008-06-13
It seems like the KDE4 packages are not all on there yet.  They may be in the process of updating the packages in prepping for the .1 release.

---

### Post by soccerboy on 2008-06-13
by the way the other package is kubuntu-desktop which transforms your install to load kde by default as if you actually installed kubuntu from the cd.

---

### Post by xeth_delta on 2008-06-13
> **bmcase said:**
> I am trying to put KDE4 on my laptop using synaptic; but I'm getting 404Error messages for 153 out of 200 packages. Worked fine for my PC; but 3 days of nada for the laptop. Has it been removed? Do I have to choose between an even older version and the new Beta?

Try using a different set of repository mirrors. The ones you are using might be down.

---

### Post by bmcase on 2008-06-13
Ok, seem to have better luck with that one. What about the partial install of kde4? I don't have a clue as to which 47 of the 200 got installed; so I don't know what to try to remove. Just hope they don't cause any trouble..?
Thanks...

---

### Post by soccerboy on 2008-06-13
If you got a 404 error then none of them should have been installed.  apt first downloads all packages then installs in one fell swoop.

---

### Post by eluminx on 2008-06-14
I don't mean to jack the thread but, say for example i wanted to install kde4.1 is there anyway of keeping the various apps that get installed seperate from my gnome desktop?  What i mean is if i install kde and i load a gnome session, all the kde apps appear in my gnome session menus.  Is there anyway to make the two seperate without having to install the whole system again?

---

