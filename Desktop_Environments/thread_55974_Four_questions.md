---
title: "Four questions"
date: 2005-08-10
forum: Desktop Environments
---

### Post by racecat on 2005-08-10
if I can remember them all. As a relative linux newb, I've been trying several Linux dists. Ubuntu is the best supported  by far and as I prefer KDE, I've just switched to Kubuntu from Ubuntu.

Alright, here goes:

1 about every other time I open something that comes up under Konqueror, Konqueror crashes. I bring it up again, and it works fine.

2 In Ubuntu, I was able to install MSTTFONTS to supply missing fonts on my Roadrunner homepage (with Macromedia plug-in installed). I don't see this available on Kynaptic.

3 Every time I've run Firefox with KDE, the fonts on the address bar is way too small for my liking. Under Gnome and Windows, it seems larger and the font is different. Where can I change this?

4 This is not Kspecific, but we have an old Win 98 machine which has Works on it. We have lots of documents on it which were saved in, you guessed it, Works format. Are there any linux word processors and spreadsheet programs that will open them?

Hope this isn't an over load. I think I'll put my HD with Ubuntu back in and try to tackle loading KDE. Any words of wisdom about any gotchas would be helpful.

Thanks,
Bill

---

### Post by AndyAWS on 2005-08-10
I'll take a shot at #4...

Try OpenOffice Word Processor...it can convert some really old and obscure document formats.

Other possibles....AbiWord and KWord (part of KOffice)

---

### Post by racecat on 2005-08-10
Thanks.

Already tried OpenOffice. I'll try to get the others. Maybe tomorrow. Beddy-bye time.

G'night,
Bill

---

### Post by ltmon on 2005-08-10
For the MS TrueType fonts you need to enable the extra respositories.  [http://ubuntuguide.org](http://ubuntuguide.org) has the instructions.

Konqueror was unstable in the release of Kubuntu.  There are workarounds, but I would suggest to upgrade KDE would be the best solution.  Many people have upgraded to KDE 3.4.2 (from 3.4.0), which (AFAIK) gets rid of this problem.  Have a look at the KDE 3.4.2 threads in this forum if you want to do this.

L.

---

### Post by David R on 2005-08-11
To update from KDE 3.4.0 to KDE 3.4.2, You will need to add the following line to your repositories list in Synaptic :

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

---

### Post by Mishura on 2005-08-11
Yeah.  I recommend upgrading KDE for the Konqueror bugs.  I've noticed them too with 3.4.0 but the occurrence of bugs have decreased significantly with the upgrade.

I'll take a shot with Firefox fonts.  Install GTK-Qt theme engine and tell Kontrol Center (KControl) to make GTK apps use KDE/Qt fonts and themes.  This will make all your GTK-based apps like Firefox use the exact same font themes as your KDE apps.

---

### Post by racecat on 2005-08-11
We're smilin'. Enabled extra repositories. Put  "deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main" in /etc/apt/sources.list. Must have been the repository list in Synaptic referred to. Updated KDE to 3.4.2. Loaded MSTTCOREFONTS. Tried Abiword; it couldn't open the Works document either. When I tried to open Kword (after instaling it), I got:

bill@ubuntu2:~$ kword
koffice (lib kofficecore): ERROR: Couldn't find the native MimeType in kword's desktop file. Check your installation !
bill@ubuntu2:~$

Loaded all the dependancies listed. Any ideas?

Thanks for all the help.

Bill

---

### Post by racecat on 2005-08-11
Per this suggstion:

I'll take a shot with Firefox fonts. Install GTK-Qt theme engine and tell Kontrol Center (KControl) to make GTK apps use KDE/Qt fonts and themes. This will make all your GTK-based apps like Firefox use the exact same font themes as your KDE apps.

I installed gtk2-engines-gtk-qt with no listed dependencies. Could not find (in Kontrol Center) where to make GTK apps use anything.

Sorry.   ](*,) 

Bill

---

### Post by rosslaird on 2005-08-12
[QUOTE=racecat]Could not find (in Kontrol Center) where to make GTK apps use anything.
[/QUOTE]

It's under "Appearance & Themes" --> GTK Styles and Fonts

(if it's installed correctly)

---

