---
title: "Emerald?"
date: 2009-09-20
forum: Desktop Environments
---

### Post by chrispche on 2009-09-20
Is there a basic theme package I can download that has some emerald themes in it? Rather than downloading individual ones?

---

### Post by WatTwo on 2009-09-20
Well, theres many of them, 

Try looking on "gnome-look.org"

That's where i have gotten mine

---

### Post by chrispche on 2009-09-20
Yeah I know about them. I just wondered if there was a package or something available with a collection of them.

---

### Post by benerivo on 2009-09-20
If you have git-core installed, then pasting this commmand in to a terminal should create a folder full of emerald themes...```
git clone git://anongit.opencompositing.org/fusion/decorators/emerald-themes
```

---

### Post by theZoid on 2009-09-20
> **benerivo said:**
> If you have git-core installed, then pasting this commmand in to a terminal should create a folder full of emerald themes...```
git clone git://anongit.opencompositing.org/fusion/decorators/emerald-themes
```

Sorry for this question, but what is 'git-core' ?  thanks

---

### Post by benerivo on 2009-09-20
git-core is briefly described [here]("http://packages.ubuntu.com/jaunty/git-core"). Git is most often used as a way to manage and download the very latest version of a software package.

---

### Post by chrispche on 2009-09-21
> **benerivo said:**
> If you have git-core installed, then pasting this commmand in to a terminal should create a folder full of emerald themes...```
git clone git://anongit.opencompositing.org/fusion/decorators/emerald-themes
```

Thanks. One question is there a way to add the themes all together? Rather than adding them individually.

---

### Post by benerivo on 2009-09-22
There's not a straightforward way. The emerald themes are all just archives that have a .emerald extension. When adding one through the emerald theme manager it is extracted in to its own folder in /home/ben/.emerald/themes (i think). There will be a way to write a script to take many themes and extract them in to individual folders, but i don't know if such a script already exists.

---

