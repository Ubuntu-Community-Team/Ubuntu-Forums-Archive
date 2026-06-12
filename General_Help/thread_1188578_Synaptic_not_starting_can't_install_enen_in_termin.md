---
title: "Synaptic not starting can't install enen in terminal"
date: 2009-06-15
forum: General Help
---

### Post by pceluvempathy on 2009-06-15
I'm running ubuntu Hardy on an old dell desktop and its had this problem for a while now but iu never decided to address it:
every time i try and enter the update manager or synaptic or even install through the terminal i get 
this error message 
E: Type 'eb' is not known on line 2 in sources list /etc/apt/sources.list.d/winehq.list

help would be greatly appreciated 

-Tony-

---

### Post by abhilashm86 on 2009-06-15
maybe there as an error in sources.list file, type this in terminal,
```

sudo gedit /etc/apt/sources.list


```

and please check line 2 and find whats error, sudo because you are editing a resource file stuff,
if you din't understand, post your file information...........

---

### Post by oldos2er on 2009-06-15
> **pceluvempathy said:**
> I'm running ubuntu Hardy on an old dell desktop and its had this problem for a while now but iu never decided to address it:
every time i try and enter the update manager or synaptic or even install through the terminal i get 
this error message 
E: Type 'eb' is not known on line 2 in sources list /etc/apt/sources.list.d/winehq.list


 Probably missing a "d" in front of the "eb". Run **gksu gedit /etc/apt/sources.list.d/winehq.list** in a terminal, fix the typo, save and exit, then run **sudo apt-get update**

---

### Post by pceluvempathy on 2009-06-15
awesome problem solved thx [URL="http://ubuntuforums.org/member.php?u=338320"]oldos2er[COLOR=Black]    XD[/COLOR]
[/URL]

---

