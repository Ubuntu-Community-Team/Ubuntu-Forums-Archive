---
title: "how to delete movie player"
date: 2009-06-11
forum: General Help
---

### Post by jeff1199900 on 2009-06-11
i am relitevly new to ubuntu, i have jaunty jakalope, and the movie player keeps on crashing and not showing the movie when i try to play it](*,). i am wondering if someone could help me delete it so that i dont have to worry about it. i have tried synaptip and gone through add/remove pregrams and i cannot find either. thank you for your help.

---

### Post by Soul-Sing on 2009-06-11
whats the name of the player
How did you installed it, and from wich source?

---

### Post by colau on 2009-06-11
> **jeff1199900 said:**
> i am relitevly new to ubuntu, i have jaunty jakalope, and the movie player keeps on crashing and not showing the movie when i try to play it](*,). i am wondering if someone could help me delete it so that i dont have to worry about it. i have tried synaptip and gone through add/remove pregrams and i cannot find either. thank you for your help.
```

sudo aptitude remove <packagename>

```
Which player do you want to remove?
System>Administration>Synaptic Package Manager search

---

### Post by lovinglinux on 2009-06-11
You don't need to remove it. It won't hurt your system if you leave it there.

I recommend that you read [this tutorial](http://ubuntuforums.org/showthread.php?t=766683). It always solve most of my problems related to media playback.

I also recommend installing [smplayer](apt:smplayer) [apt-get], which is the best frontend for mplayer in my opinion.

---

### Post by colau on 2009-06-11
> **jeff1199900 said:**
> i am relitevly new to ubuntu, i have jaunty jakalope, and the movie player keeps on crashing and not showing the movie when i try to play it](*,). i am wondering if someone could help me delete it so that i dont have to worry about it. i have tried synaptip and gone through add/remove pregrams and i cannot find either. thank you for your help.
To remove Movie Player
```

sudo aptitude remove totem

```

---

### Post by BlazeFire247 on 2009-06-11
> **colau said:**
> [Which player do you want to remove?
System>Administration>Synaptic Package Manager search

I think he meant by the built-in music player on Ubuntu (Totem Music Player). It's found at Add/Remove on Sound & Video.

---

### Post by Soul-Sing on 2009-06-12
Removing totem is better not done, you "remove" the ubuntu desktop.
As earlier said: do not use it.

---

