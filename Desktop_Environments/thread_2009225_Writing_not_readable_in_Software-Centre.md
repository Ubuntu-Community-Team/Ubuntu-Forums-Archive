---
title: "Writing not readable in Software-Centre"
date: 2012-06-24
forum: Desktop Environments
---

### Post by kabukiM0n0 on 2012-06-24
First off apologies if this is the wrong sub-forum.

I'm using Ambience-brokenblue theme in gnome fallback for Ubuntu 12.04 and I have one minor issue with this theme, I wanted to know if there was a fix. 
When I open the software center up, you cannot read the text, as it appears in very light grey and the window in white. 
This is the only application in which it occurs.

---

### Post by Frogs Hair on 2012-06-24
I have that theme and problem also. I think the problem is with the theme. You can contact the theme creator at Gnome Look. You will need an account to leave a message. 

I only use the theme so  GTK applications match the E17 theme when I use that DE. I don't use the software center in E17, so I didn't notice the problem until I saw your post.

People who use a package manager other than the Ubuntu software center often over look this application when creating themes.

---

### Post by vasa1 on 2012-06-24
There's [a workaround]("http://ubuntuforums.org/showthread.php?t=1913590") but it needs to be redone each time the USC is updated. The workaround involves editing this file:
/usr/share/software-center/ui/gtk3/css/softwarecenter.css

For starters, just change only the hex values in the first two lines from:
```
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;

```to whatever you want.

I made both of them #000000 and this is what USC looks to me (affected no doubt by other tweaks I've done to my UI):

---

### Post by vasa1 on 2012-06-24
Just noticed that the comments section is adversely affected in that the names of the authors of comments isn't visible [s]:( so I'm going back to the default.[/s] but #888888 works at least for me.

---

### Post by kabukiM0n0 on 2012-06-24
Smashing! at least it's a temporary fix. It's no biggie having to retype it in every time it updates. I don't really use it much anyway. 

I shall mark it as solved :popcorn:

I'll add the color codes I applied from the other thread in here, You can read perfectly with them, also the comments.
Saves anyone needing help having to find the other thread.

@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #B4A66F

---

