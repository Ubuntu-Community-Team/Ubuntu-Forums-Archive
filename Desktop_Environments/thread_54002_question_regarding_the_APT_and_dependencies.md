---
title: "question regarding the APT and dependencies"
date: 2005-08-03
forum: Desktop Environments
---

### Post by ^NoX on 2005-08-03
when you install some package, it downloads it`s depenendencies.
but what happens when you remove that package? its dependencies are still there.

when i was using debian, they had several tools for cleaning the un-needed dependencies that the APT left behind.
what tool do i have here in ubuntu?

thanx alot. :)

---

### Post by jyank on 2005-08-03
i belive what you're looking for is synaptic :)

run it by typing 

```
sudo synaptic
```

---

### Post by ^NoX on 2005-08-03
[QUOTE=jyank]i belive what you're looking for is synaptic :)

run it by typing 

```
sudo synaptic
```[/QUOTE]

i don`t think you understood what my problem is...
synaptic is a nice tool for choosing and searching for packages in GUI.
what i want - is some tool that will search for dependencies that downloaded and no longer being used by any software, and remove it.

thanx for your suggestion, anyway :)

---

### Post by jyank on 2005-08-03
Ah, yes, misunderstood

---

### Post by ^NoX on 2005-08-03
[QUOTE=jyank]Ah, yes, misunderstood[/QUOTE]
  :smile: thanx anyway man :)

---

### Post by woedend on 2005-08-03
[QUOTE=^NoX]:smile: thanx anyway man :)[/QUOTE]
 unless you are very limited on space i wouldn't worry about it.  I know that doesn't answer your actual question, but the problem remains that if you installed something else that had those same dependencies, perhaps(Actually, probably) unknowingly, it dies too.  Not sure if theres a tool that checks every package for dependencies and gives the leftovers...though that is a good idea...

---

### Post by Ramses on 2005-08-03
Look for deborphan. It finds non-used libraries.

---

### Post by ^NoX on 2005-08-03
[QUOTE=woedend]unless you are very limited on space i wouldn't worry about it.  I know that doesn't answer your actual question, but the problem remains that if you installed something else that had those same dependencies, perhaps(Actually, probably) unknowingly, it dies too.  Not sure if theres a tool that checks every package for dependencies and gives the leftovers...though that is a good idea...[/QUOTE]

well, im not limited on diskspace, but i love optimization - thanx anyway

---

### Post by ^NoX on 2005-08-03
[QUOTE=Ramses]Look for deboprhan. It finds non-used libraries.[/QUOTE]

thanx :) and welcome to ubuntuforums

---

### Post by Caboto on 2005-08-03
aptitude remembers what package brings which dependencies and will uninstall all of them, whenever you remove that package.
It hasn't a GUI, which makes it a little bit harder to work with. There's a nice How-To for it [here](http://ubuntuforums.org/showthread.php?t=37736).

---

### Post by ^NoX on 2005-08-04
btw, i found out about another program called orphaner - something realy good

---

### Post by Spudgun on 2005-08-05
Yeah, that comes with the package 'deborphan'.

---

