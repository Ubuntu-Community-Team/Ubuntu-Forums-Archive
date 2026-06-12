---
title: "I need a means to install ubuntu-desktop without CD"
date: 2006-01-04
forum: General Help
---

### Post by Iandefor on 2006-01-04
As the title says. I can't install the metapackage ubuntu-desktop using the CD. It will install the base system, but it seems any packages beyond that are corrupted from the CD. So, is there a way to install ubuntu-desktop and all it's dependencies from a server install without the physical disc? One thought that has occured to me is that I could download and mount the installation .iso and install the packages from there, but I don't know how to get apt to 
read the packages from there.

---

### Post by Iandefor on 2006-01-04
Really, now. No one has any ideas?

---

### Post by Sef on 2006-01-04
Try this:

sudo apt-get install ubuntu-desktop

or if that does't work, try it without the sudo.


Note:  Please give time for someone to respond.  We are all volunteers.   Usually you can get an answer within a day or two, but sometimes it may take a few days to get an answer.

---

### Post by Iandefor on 2006-01-04
[QUOTE=Sef]Note:  Please give time for someone to respond.  We are all volunteers.   Usually you can get an answer within a day or two, but sometimes it may take a few days to get an answer.[/QUOTE] My experience with with technical support requests is that either someone answers pretty soon, or they languish for a good long time, and no one answers them. That's why I decided to give it a bump, which was really what my second post was.

---

### Post by codejunkie on 2006-01-04
[QUOTE=Iandefor]My experience with with technical support requests is that either someone answers pretty soon, or they languish for a good long time, and no one answers them. That's why I decided to give it a bump, which was really what my second post was.[/QUOTE]
Do a server install then edit the sources.list file with this 
```
nano /etc/apt/sources.list
```
comment out the line for the cd-rom save the file with ctrl+x then hit y and enter run sudo apt-get update then install ubuntu-desktop.

---

### Post by Iandefor on 2006-01-04
[QUOTE=codejunkie]Do a server install then edit the sources.list file with this 
```
nano /etc/apt/sources.list
```
comment out the line for the cd-rom save the file with ctrl+x then hit y and enter run sudo apt-get update then install ubuntu-desktop.[/QUOTE] What the heck? It's working.
Thanks! I wonder why I didn't know about this earlier?

---

### Post by domino on 2006-01-04
hi, when you do an *apt-get update then install ubuntu-desktop*, does it install the default kicker apps like it does with installing from DVD? The reason i asked is because I only need Gnmoe, essential applications, and services to be installed. I don't want any multimedia, productivity suites, gimp, ect. installed at all.

---

### Post by codejunkie on 2006-01-05
[QUOTE=domino]hi, when you do an *apt-get update then install ubuntu-desktop*, does it install the default kicker apps like it does with installing from DVD? The reason i asked is because I only need Gnmoe, essential applications, and services to be installed. I don't want any multimedia, productivity suites, gimp, ect. installed at all.[/QUOTE]
when you install ubuntu-desktop it will install the default set of programs that comes with ubuntu. try installing the package "gnome" it might be what your wanting it's just the default gnome desktop packages only.
edit:you have to enable the universe repos before you can install the package.

---

### Post by domino on 2006-01-05
Thanks for the comment cj. Sorry for the little derailment Iandefor.

---

### Post by Iandefor on 2006-01-05
Thanks for the comment cj. Sorry for the little derailment Iandefor  Perfectly alright.

@Codejunky: Thank you! I was certain I was screwed, and after I spent so much money on this computer (~$350 is a *lot* when you have almost no money)!
I had a few problems with the X server, but that turned out to be my own stupidity- I misread one of the resolutions, and X was really freaky, running at 1024x1168 on a monitor build for 1024x768 :-D. But when I fixed that, it was fine.

---

