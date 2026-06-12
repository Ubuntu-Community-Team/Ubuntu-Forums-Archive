---
title: "Installing Screenshots:need guidence"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by amitabhishek on 2007-12-09
Hi friends,

I am just a bit more than a Linux newbie & I managed to customize my 7.04 desktop using mac4lin project (posted on this forum). However I am unable to install screenlets on my new desktop. 
I have a AMD X2, 1GB machine without a GFX card.  I would love to have screenlets hangin on my desktop. Is there anyway out? Step by step guidance, may be. I have done some googling on this subject but couldn't quite get it.

Also between GDM & GTK splash screen I get Ubuntu's default brown color for a fraction of second which is an eyesore. Is there any way to avoid it?

All suggestions will be greatly appreciated.

---

### Post by amitabhishek on 2007-12-09
Its screenlets not screenshots. My apologies.

---

### Post by kelbizzle on 2007-12-09
"install screenlets ubuntu gutsy" into google returned [this]("http://tombuntu.com/index.php/2007/12/03/os-x-like-widgets-with-screenlets-on-ubuntu-update/")

---

### Post by amitabhishek on 2007-12-09
Thx! but I can't enable compiz since I don't have a graphics card.

---

### Post by Ub1476 on 2007-12-09
Screenlets need compositing, Compiz is compositing.

Post the output of

```
lspci | grep VGA
```

For the brown login background, look [here]("http://ubuntuforums.org/showthread.php?t=634934&highlight=brown+login").

---

### Post by amitabhishek on 2007-12-09
amit@amit-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
amit@amit-desktop:~$ 


Thanks!

---

### Post by Ub1476 on 2007-12-09
Your graphic controller works with Compiz, but it is rather slow.. Look [here]("http://ubuntuforums.org/showthread.php?t=609295") for more info.

If Compiz causes to much trouble, I don't think [gDesklets]("http://en.wikipedia.org/wiki/GDesklets") needs 3d rendering, not sure though.

There are also [Conky]("http://ubuntuforums.org/showthread.php?t=281865") which is a light-weight system monitor.

Both of them are in repos. More updated versions on homepage though.

---

### Post by amitabhishek on 2007-12-09
How do I load desklets during startup?

---

### Post by Ub1476 on 2007-12-09
I think the command for gDesklets is either "gdesklet" or "gdesklets". Open alt+f2 and check by writing it in there (it should load). After you know which is the right command open System>Preferences>Sessions>Add>command.

---

### Post by amitabhishek on 2007-12-09
Thanks Buddy! You told me exactly what I was looking for. Desklets mat not be too fancy but it just do its job.

---

