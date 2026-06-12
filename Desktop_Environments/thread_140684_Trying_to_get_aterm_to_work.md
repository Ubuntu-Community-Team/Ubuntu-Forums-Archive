---
title: "Trying to get aterm to work"
date: 2006-03-06
forum: Desktop Environments
---

### Post by arachn1d on 2006-03-06
Hey all

I'm trying to get aterm to work nicely. It's weird though, because I have created ~/.Xdefaults but it's not adopting any of the settings. I'm so lost on what to do, please help!

Thanks!


p.s can someone post some cool configs that include transparency? Thanks!

---

### Post by bluevoodoo1 on 2006-03-06
Here's the command I use...
```
aterm -tr -bg black -fg lightgrey -fn 7x14 -fb 7x14 +vb +sb -geometry 85x26+13+610
```

it includes transparency, you might not want my "geometry," but there it is!

---

### Post by arachn1d on 2006-03-06
Is there a way to make it so if I type aterm it just uses that command?

---

### Post by bluevoodoo1 on 2006-03-06
I'm not entirely sure. I have aterm on my menu with that command. I'm not sure how to only type aterm and get that...

---

### Post by arachn1d on 2006-03-06
[QUOTE=bluevoodoo1]I'm not entirely sure. I have aterm on my menu with that command. I'm not sure how to only type aterm and get that...[/QUOTE]
Well how do you do that?


-edit nevermind I figured it out.

Thanks!

(how do I change it so the transparency is lighter?)

---

### Post by guano on 2006-03-15
To get aterm using the same configurations always, edit (or create) a file called .Xdefaults, in your home directory. take a look in "man aterm" for more options. Here is my .Xdefaults:

```
#aterm settings
aterm*foreground: white
aterm*background: black
aterm*transparent: true
aterm*shading: 60
aterm*saveLines: 1000
aterm*tintingType: true
aterm*tinting: #c0c0c0
aterm*fading: 60
aterm*transpscrollbar: true
aterm*scrollBar: false
aterm*pointerColorBackground: black
aterm*loginShell: true
aterm*font:*-*-fixed-medium-r-normal--*-120-*-*-*-*-iso8859-1
aterm*boldFont:*-*-fixed-bold-r-normal--*-*-120-*-*-*-*-iso8859-1
aterm*geometry: 85x30+10-10
aterm*scrollKey: true
aterm*internalBorder: 2
```

---

### Post by bluevoodoo1 on 2006-03-15
[QUOTE=guano]To get aterm using the same configurations always, edit (or create) a file called .Xdefaults, in your home directory. take a look in "man aterm" for more options. Here is my .Xdefaults:

```
#aterm settings
aterm*foreground: white
aterm*background: black
aterm*transparent: true
aterm*shading: 60
aterm*saveLines: 1000
aterm*tintingType: true
aterm*tinting: #c0c0c0
aterm*fading: 60
aterm*transpscrollbar: true
aterm*scrollBar: false
aterm*pointerColorBackground: black
aterm*loginShell: true
aterm*font:*-*-fixed-medium-r-normal--*-120-*-*-*-*-iso8859-1
aterm*boldFont:*-*-fixed-bold-r-normal--*-*-120-*-*-*-*-iso8859-1
aterm*geometry: 85x30+10-10
aterm*scrollKey: true
aterm*internalBorder: 2
```[/QUOTE]

Wow that's great! Thank you!

---

