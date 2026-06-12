---
title: "Help removing Gnome from Kubuntu"
date: 2005-05-25
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-05-25
Hey. Sorry if this has been posted. I have searched and haven't found anything that is relevant. Ok well I wanted to test out Gnome (I installed Kubuntu to begin with so I had to download Gnome and some of its apps) but have decided to stick with KDE. I now want to uninstall Gnome and its apps but don't know how to uninstall all of the Gnome stuff together. I don't wanna go and look through everything in Kynaptic/Synaptic. Any help or link would be much appreciated. Thanks.

---

### Post by Burgundavia on 2005-05-25
Find all the things that ubuntu-desktop depends on, and remove those.

Corey

---

### Post by lilandra on 2005-05-26
how d'you do that?
i mean, if i just uninstall ubuntu-desktop that's all that it uninstalls
is there an apt-get command i'm missing?

---

### Post by bored2k on 2005-05-26
[QUOTE=lilandra]how d'you do that?
i mean, if i just uninstall ubuntu-desktop that's all that it uninstalls
is there an apt-get command i'm missing?[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://www.ubuntuforums.org/showthread.php?t=24403&highlight=debfoster)
Debfoster is your friend.

---

### Post by lilandra on 2005-05-26
thank you!!!

---

### Post by tread on 2005-05-26
A simpler method (as I have been repeatedly told by a friend .. now if only I could get myself to read the documentation :)) is to use aptitude to install packages instead of kynaptic/synaptic/apt-get. It supposedly keeps a history of installed packages, and you can roll back installations .. get rid of whatever you installed plus the dependencies that got installed automatically.

And if you do go this path, please please write a short howto use aptitude article :)

---

### Post by lilandra on 2005-05-26
[QUOTE=tread]A simpler method (as I have been repeatedly told by a friend .. now if only I could get myself to read the documentation :)) is to use aptitude to install packages instead of kynaptic/synaptic/apt-get. It supposedly keeps a history of installed packages, and you can roll back installations .. get rid of whatever you installed plus the dependencies that got installed automatically.

And if you do go this path, please please write a short howto use aptitude article :)[/QUOTE]
 b-b-b-b-b-but i LOVE apt-get

hmm...is aptitude command line?
or is it that funky in terminal display with frames?

---

### Post by bored2k on 2005-05-26
[QUOTE=lilandra]b-b-b-b-b-but i LOVE apt-get

hmm...is aptitude command line?
or is it that funky in terminal display with frames?[/QUOTE]
 You already have it, just type aptitude or man aptitude.

---

### Post by lilandra on 2005-05-26
[QUOTE=bored2k]You already have it, just type aptitude or man aptitude.[/QUOTE]
 oh i know i have it! i just don't know if i want to use it :)

---

### Post by Jonathan2007 on 2005-05-26
[QUOTE=Burgundavia]Find all the things that ubuntu-desktop depends on, and remove those.

Corey[/QUOTE]
Well since I started out with Kubuntu I never had Ubuntu-desktop installed. And I just installed Gnome and not Ubuntu-desktop so it says it can't find Ubuntu-desktop (and rightly so I guess) when I try to apt-get uninstall it.

[QUOTE=tread]A simpler method (as I have been repeatedly told by a friend .. now if only I could get myself to read the documentation :)) is to use aptitude to install packages instead of kynaptic/synaptic/apt-get. It supposedly keeps a history of installed packages, and you can roll back installations .. get rid of whatever you installed plus the dependencies that got installed automatically.

And if you do go this path, please please write a short howto use aptitude article :)[/QUOTE]
That would be good except I have already installed Gnome so I guess it is too late to use aptitude to help solve this problem.

Anyone else have any ideas?

---

### Post by lilandra on 2005-05-27
[QUOTE=Jonathan2007]Well since I started out with Kubuntu I never had Ubuntu-desktop installed. And I just installed Gnome and not Ubuntu-desktop so it says it can't find Ubuntu-desktop (and rightly so I guess) when I try to apt-get uninstall it.


That would be good except I have already installed Gnome so I guess it is too late to use aptitude to help solve this problem.

Anyone else have any ideas?[/QUOTE]
 well i used debfoster
don't know if it'll help you
someone gaveme the link in this thread to a how-to on the forums

---

### Post by Jonathan2007 on 2005-05-27
Yeah I saw that about debfoster but I am still pretty much a linux newb and if there was another easier way I would rather choose that.

---

### Post by lilandra on 2005-05-28
oh well it wasn't all that hard

you want to get rid of gnome right?
well you could install debfoster and look at the outputs to the various command and maybe see if you feel up to it
but, if you want to uninstall gnome, that's gdm
and i'm not sure what it will take with it...but then there's the whole list of orphans that debfoster will give you
i can't say for sure what's safe...but....hmmm...you can go thru the prompts to make a keeper list...and cancel before it removes anything...just to see?

---

