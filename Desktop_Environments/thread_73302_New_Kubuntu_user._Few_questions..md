---
title: "New Kubuntu user. Few questions."
date: 2005-10-08
forum: Desktop Environments
---

### Post by escobar on 2005-10-08
I recently switched to Kubuntu (Breezy rc) and I am trying to get a few things setup. One thing I am not able to do is edit any files because of the following error:

[I]bsanks@TREADSTONE:~$ sudo kate /etc/apt/sources.lst
Password:
kate: ERROR: Communication problem with kate, it probably crashed.
bsanks@TREADSTONE:~$[/I]

Kate seems to be the only text editor installed. I thought I could install kedit, but that cannot be found in the default repositories. Past that I'm stuck. I thought updating it may help but I have the latest version of Kate already. Or is this not even a problem with Kate?

Second question. Looking at the KUser tool, there appears to be user titled "nobody" with a home directory of /nonexistent. I'm hoping this is normal? Just wanted to be sure. Other than that, everything is going well. Thumbs up to the Ubuntu devs.

---

### Post by Leif on 2005-10-08
I'm not a kubuntu user, but I would be surprised if emacs/nano/vi were not installed. you can also try reinstalling kate

---

### Post by Seth on 2005-10-08
You can't use sudo with KDE apps. Instead use: ```
kdesu kate /etc/apt/sources.list
```

---

### Post by GeneralZod on 2005-10-09
kate doesn't work with sudo, but, oddly, kwrite does, at least one my system:

```

sudo kwrite

```

kwrite is lighter-weight than kate, too.

---

### Post by Hobbsee on 2005-10-09
you can use sudo with kde apps, it works just fine.

Use Kwrite as the text editor, and it works - Kate has never worked well for me either.

ie 
> sudo kwrite /etc/apt/sources.list

---

### Post by Freddy on 2005-10-09
> kate doesn't work with sudo, but, oddly, kwrite does, at least one my system
It does work with kdesu though.
```
kdesu kate
``` 
From a prompt or run command.   /// Freddan

---

### Post by escobar on 2005-10-09
"Kdesu" along with Kate did work for me. I would install Kwrite but I cannot find it in any of the Breezy repos.  I guess I would like kwrite back if it's a little more responsive than kate. Where would I get it though? Also,  "sudo" does work with some commands as well. No big problem, if one fails I just try the other. Anyone know the answer to my other question?

*Second question. Looking at the KUser tool, there appears to be user titled "nobody" with a home directory of /nonexistent. I'm hoping this is normal? Just wanted to be sure*

Thanks for all the help so far.

---

### Post by Freddy on 2005-10-09
You could also try kedit, alot slimmer then big Kate but more useably then kwrite. /// Freddan

---

### Post by Hobbsee on 2005-10-10
kedit is not in breezy by default, for some reason.

Kwrite is already there in the default kubuntu breezy install, it's just not in the menus for some silly reason.  :)

---

### Post by escobar on 2005-10-10
Anyone?

[I]Looking at the KUser tool, there appears to be user titled "nobody" with a home 
directory of /nonexistent. I'm hoping this is normal? Just wanted to be sure.[/I]

Also, I'm not really fond of Konquerer as a web browser. Anyway to disabled Konquerer's web abilities? Or if I use a replacement like Krusader, is it safe to remove Konquerer?

---

### Post by akcanadianeh on 2005-10-12
Konquerer is not only the KDE web browser, it's the file browser too, so you really shouldn't remove it...

---

### Post by shinygerbil on 2005-10-12
[QUOTE=escobar][I]Looking at the KUser tool, there appears to be user titled "nobody" with a home 
directory of /nonexistent. I'm hoping this is normal? Just wanted to be sure.[/I]
[/QUOTE]

There is on mine. I'm guessing it's normal.

---

