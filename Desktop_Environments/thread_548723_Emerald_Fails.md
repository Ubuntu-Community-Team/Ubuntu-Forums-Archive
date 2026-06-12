---
title: "Emerald Fails"
date: 2007-09-11
forum: Desktop Environments
---

### Post by SioDissolve on 2007-09-11
Another Linux Noob here to ask a question. I am having trouble with Beryl/Emerals. Beryl runs fine but I loose all window borders, buttons, and the ability to move windows. I am also unable to switch themes in emerald. Any ideas?

---

### Post by Happy_Man on 2007-09-11
What happens if, while running Beryl, you open a terminal and enter ```
emerald --replace
```?

---

### Post by ryno519 on 2007-09-11
> **SioDissolve said:**
> Another Linux Noob here to ask a question. I am having trouble with Beryl/Emerals. Beryl runs fine but I loose all window borders, buttons, and the ability to move windows. I am also unable to switch themes in emerald. Any ideas?

That happened to me when I first installed beryl.

When I ran beryl I would use the command

```
beryl
```

to run it. Turns out that doesn't actually invoke the window decorator and theme manager. Try the following. If you don't have beryl-manager installed, use

```
sudo apt-get install beryl-manager
```

and then run the following command

```
beryl-manager &
```

---

### Post by SioDissolve on 2007-09-12
I have the latest copy of beryl manager installed. Beryl isnt the problem its emerald.

---

### Post by Happy_Man on 2007-09-12
As I asked before: what happens if you put in ```
emerald --replace
``` when Beryl is running?

---

### Post by SioDissolve on 2007-09-13
absolutely nothing

---

### Post by Happy_Man on 2007-09-13
Does the terminal say anything?

---

### Post by SioDissolve on 2007-09-14
nope... it remains blank... I can enter text into it.

---

### Post by SioDissolve on 2007-09-14
i just noticed i am also unable to run terminal after i run beryl

---

### Post by Junkuhn on 2007-09-23
I have kinda the same problem. I installed CompizFusion and it rus great! I installed *Emerald* and *Emerald Themes* from Synaptic and it installls without any problems. 

I added a launcher to my Kiba-Dock and no problems there either. My problems is that when I open Emerald and choose a theme, nothing happens. There's no [I]"aply"[/] button so I take it that it should just switc theme when I select one like in the standard theme menu.

What am I doing wrong?

---

### Post by Happy_Man on 2007-09-23
Compiz Fusion is generally set to use the GTK Window Decorator by default. If you want Emerald, you have to start it with this command: ```
compiz --replace -c emerald &
```

---

### Post by shishirmk on 2007-09-23
guys compiz-fusion and beryl are still in their beta phase. they depend heavily on your graphics card and its charcteristics.. so dont install them wait for gutsy gibbon i heard its gonna ship a stable beryl!!

---

### Post by Junkuhn on 2007-09-23
> **Happy_Man said:**
> Compiz Fusion is generally set to use the GTK Window Decorator by default. If you want Emerald, you have to start it with this command: ```
compiz --replace -c emerald &
```

This worked for me.

Thanks :)

---

### Post by olavjunior on 2007-10-11
Well, this messed up my computer. How to reverse it??

---

### Post by Happy_Man on 2007-10-12
What happened? How did it mess up?

---

### Post by olavjunior on 2007-10-12
Well, I'm actually not sure if this was what caused it, cause I was trying out the "screens & graphics"-settings at around the same time. But as you can see from my attached image, my borders gets messed up when I move windows around.

I've removed Emerald, re-configured the x-file, but the problem's still there. So I'm looking forward to the final release of Gutsy, so I can reinstall everything

EDIT: Now I've reinstalled Gutsy from the final source. I really thought this wold set an end to my problem, since I didn't have this problem before I started messing with screens & graphics and emerald. But no, I was wrong! A fresh install didn't change anything at all! Maybe I'll just start a new thread

EDIT: SOLVED! Started ccsm and disabled windows decorations and re-enabled them. That did the trick :)

---

