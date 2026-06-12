---
title: "Installing the Latest Compiz Packages via Repository"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2008-03-13
Hi,

I've been without Trevino's repositories for too long.  No gutsy repos from Trev has meant old versions of compiz for me.  I was actually using a later version of the config utility in feisty than I am now with gutsy.  Now, I think I'm ready to try another third party repo but I don't know where to find any.

Found a couple of Amaranth's, but one was for feisty and one for hardy.  Does anyone know of a reliable repository with the newer versions of compiz and compiz-config that I can run on gutsy?

Thanks

---

### Post by luisromangz on 2008-03-13
Yeah, check this webpage:

[http://kwatrow.nl/repo/](http://kwatrow.nl/repo/)

---

### Post by djrobthaman on 2008-03-13
Tried that already.  It didn't work for me.  [Posted about it here]("http://ubuntuforums.org/showthread.php?t=557287&page=4") but nobody replied, so I just deleted the repos and reinstalled the stock compiz packages.

That said, do you know what I could do to fix those issues I had?

---

### Post by luisromangz on 2008-03-14
I use that repo with no problems, you should try to install the fusion-icon package from this repo:

deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse

fusion-icon allows you to select the window manager easily, so you can go from metacity to compiz, or while using compiz, choose between emerald or gtk-window-decorator/kde-window-decorator, to see if that solve the window border problems.

---

### Post by Extremeshannon on 2008-03-14
Thanks this worked great

---

### Post by luisromangz on 2008-03-14
Nice to hear that ;)

---

### Post by djrobthaman on 2008-03-14
hmmm... So I took your advice and tried the repo again.  Essentially I did the same thing and just added the repo and installed all the necessary files.  The only difference was that this time there was an issue with a currently installed file (writing to a file that was in use or something), so I uninstalled the current version of compiz and then installed the new compiz.  Execute compiz --replace and emerald --replace and now I have a fully functioning 3d desktop.

Awesome.

Thanks a million

---

### Post by djrobthaman on 2008-03-15
Hello again,

This isn't a major issue, but it seems that since installing the new version of compiz there's been a bit of a hiccup with vlc.  When I play a movie with vlc and the window is not fullscreen none of the keyboard shortcuts work.  When I maximize it to fullscreen, however, all the keyboard controls work fine.  Have you encountered this?  Any suggestions on a workaround?

Thanks again

---

