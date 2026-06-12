---
title: "Compiz Fusion Questions"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-06-22
Got it working thanks to this [how-to]("http://ubuntuforums.org/showthread.php?t=481615"). I have some questions, and although I realize its still in beta, I'm sure some other people are wondering the same things...

How do I use my emerald themes?
Can I remove the cube caps, like in beryl?
Whats a "git", and how do I install plugins? [[gitweb]("http://gitweb.opencompositing.org/")]
How did they make it so friggin' cool?

---

### Post by smartboyathome on 2007-06-22
To use emerald: type emerald --replace in a terminal

You cannot remove cube caps yet, and can only put a picture on the top cube cap

GIT is just another name for Compiz Fusion, and you should already have the plugins installed

They worked on it and improved it.

---

### Post by superyounan1 on 2007-06-22
> **smartboyathome said:**
> To use emerald: type emerald --replace in a terminal

You cannot remove cube caps yet, and can only put a picture on the top cube cap

GIT is just another name for Compiz Fusion, and you should already have the plugins installed

They worked on it and improved it.

thanks for replying. I tried emerald --replace before, but it just killed my window borders, it outputs this many times:
```
(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)

(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)

(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)
```

then i have to kill emerald and restart compiz

---

### Post by evilc on 2007-06-23
Hope you don't mind me adding my problem ( same as yours). tried adding emerald and got this,

$ emerald -replace
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Also how to get compiz fuzion manager on panel?

tia

---

### Post by superyounan1 on 2007-06-23
> **evilc said:**
> Hope you don't mind me adding my problem ( same as yours). tried adding emerald and got this,

$ emerald -replace
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Also how to get compiz fuzion manager on panel?

tia

in Gnome its in system>preferences>CompizConfig Settings Manager
if you want you can right-click on it then choose "add to panel" or "add to desktop"

otherwise just make a launcher with the command "ccsm" and put it in the panel

---

### Post by evilc on 2007-06-24
Superyounan1 thanks for that but I was looking for something like the Beryl button, I have d/l the compiztrayicon (looks the same as beryl) but when installed no icon just a flash on the screen when installed on re-running it say's it's installed?.

---

### Post by llamakc on 2007-06-24
> **smartboyathome said:**
> 

GIT is just another name for Compiz Fusion, and you should already have the plugins installed




No, GIT is similar to CVS. It's version control for the source code. Many projects use GIT.  [http://git.or.cz/](http://git.or.cz/)

---

### Post by gkiller on 2007-06-24
> **superyounan1 said:**
> thanks for replying. I tried emerald --replace before, but it just killed my window borders, it outputs this many times:
```
(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)

(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)

(emerald:19324): Wnck-WARNING **: Unhandled action type (nil)
```

then i have to kill emerald and restart compiz

You can ignore the Wnck-Warning. Everybody gets it because of an older library in Feisty.

To get emerald running, be sure that you have installed the newest version from Treviños repo. The easiest way is to go into synaptic, and remove everything that is related with beryl and emerald.

After that, install emerald again: "sudo apt-get install emerald emerald-themes" (with Trevino-repo active of course)

---

### Post by walkerk on 2007-06-24
start compiz fusion w/ emerald as the window decorator..
```
compiz --replace -c emerald
```

if this gives you errors post them up..

---

### Post by superyounan1 on 2007-06-25
> **walkerk said:**
> start compiz fusion w/ emerald as the window decorator..
```
compiz --replace -c emerald
```

if this gives you errors post them up..

yeah, that command didnt work until I removed beryl. Thanks

---

### Post by ivesjd on 2007-06-25
When I add either "compiz --replace and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

---

### Post by superyounan1 on 2007-06-25
> **ivesjd said:**
> When I add either "compiz --replace and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

you're not the only person with this problem, I haven't come across the solution though. Luckily i didnt have such a problem having it start on boot

---

### Post by superyounan1 on 2007-06-25
I came across a few other questions with compiz fusion:

- is there a way to use compiz themes such as the ones found on beryl-themes.org? I do however have emerald running well, I'm just curious

- The screen doesn't go dark when it's supposed to, such as when you hit the quit button and the logout-shutdown-restart etc options come up. It also doesnt work when using the Add-helper plugin, which is actually somethign I was looking forward to using. Other windows in the background do get dark though, but not the entire desktop.

- I fell asleep watching tv shows on my computer, when I woke up the computer was unusably slow with 100% cpu usage. I was running vlc, this doesnt happen in my regular (non-xgl) session.

anyone else having these?

---

