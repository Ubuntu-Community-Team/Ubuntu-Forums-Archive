---
title: "Pin to desktop"
date: 2009-01-12
forum: General Help
---

### Post by alex777 on 2009-01-12
Hello everybody! I need some help.

Is there a way to pin a window to the desktop in Linux? 

I have a list of tasks in Calc. And I want the window of Calc to be always before my eyes, so that it sort of reminds me of my tasks. The window must be «stuck» to the desktop, and when I click the Show Desktop Button (I use this button very often) the window shouldn't be minimized, but must always remain visible. The feature «Alway on Top» is definitely not what I want - I need the opposite, sort of «always on bottom». The window must behave as if it were part of the desktop wallpaper. Is it possible in Linux?

By the way, I've tried different «sticky notes» applications - the «glue» is unfortunately too weak: when I press the Show Desktop Button all notes disappear from the desktop - they are just minimized :-( The best solution would be to glue the window of Calc to the desktop.

I'm using the latest Ubuntu.

Thanks in advance!

---

### Post by albinootje on 2009-01-12
> **alex777 said:**
>  Is there a way to pin a window to the desktop in Linux? 

I have a list of tasks in Calc. And I want the window of Calc to be always before my eyes, so that it sort of reminds me of my tasks.

Afair years ago I've seen different themes in various windowmanagers, where the always-on-top was one of the options.

I think it all comes down to using a windowmanager + theme which supports this.

See here for more ideas/options :
[http://brainstorm.ubuntu.com/idea/16855/](http://brainstorm.ubuntu.com/idea/16855/)

---

### Post by alex777 on 2009-01-12
> I think it all comes down to using a windowmanager + theme which supports this.

Can you recommend any window managers and themes to try?

---

### Post by albinootje on 2009-01-12
> **alex777 said:**
> Can you recommend any window managers and themes to try?

It's been years ago that I saw that, and I just searched and could not find any interesting results so far. 

I can try searching again later but hopefully someone else can answer your question.

---

### Post by albinootje on 2009-01-12
> **alex777 said:**
> Can you recommend any window managers and themes to try?

Is this what your looking for ?

[http://ceitl.zanestate.edu/blog/archives/2007/05/usability-5-ways-linux-trumps-windows/](http://ceitl.zanestate.edu/blog/archives/2007/05/usability-5-ways-linux-trumps-windows/)

"always on top", or do you want a "stick to desktop in the background" ?

---

### Post by mcduck on 2009-01-12
You can get pretty close to that if you are using Desktop Effects. Just take a look at the "Window Rules"-plugin..

The only limitation would be that "Show Desktop" still does what it's supposed to, and hides _all_ applications. Even defining the window as "non minimizable" is not able to change that.

******

Edit: I just found a solution to that one as well, In Compiz general settings disable "Hide Skip Taskbar Windows". This means that if you configure the program to skip taskbar (with the Window Rules-plugin) it'll be considered as part of desktop and won't get hidden if you use the Show Desktop-button.

So, here's what you need to do:
1. In General settings, disable "Hide Skip Taskbar windows"
2. In Window Rules, add your program to "Skip Taskbar" & "Below"-groups. (and "Sticky", if you want it to appear on every desktop.)
3. Actually since the window won't show in taskbar you don't want to minimize it. It would just disappear into nothing. So add it into the "Non minimizable windows"-group as well to avoid that problem..

Now the program window will always stay behind other windows, and will not be hidden by "Show Desktop". The only loss is that it won't show in the taskbar any more.

---

### Post by albinootje on 2009-01-12
> **mcduck said:**
> You can get pretty close to that if you are using Desktop Effects. Just take a look at the "Window Rules"-plugin..

The only limitation would be that "Show Desktop" still does what it's supposed to, and hides _all_ applications. Even defining the window as "non minimizable" is not able to change that.

The OP can also use "Virtual Desktops", and have that one app sticky in another Virtual Desktop.
Then it's a matter of one mouse-click to see you tasks.

Ah... It's called "Workspace" in Ubuntu. See the previous webpage link I've referred to.

---

### Post by mcduck on 2009-01-12
> **albinootje said:**
> The OP can also use "Virtual Desktops", and have that one app sticky in another Virtual Desktop.
Then it's a matter of one mouse-click to see you tasks.

Ah... It's called "Workspace" in Ubuntu. See the previous webpage link I've referred to.

Yeah, I know all those trick in the link, and they get pretty close to what alex777 asked for, but not quite there.

The only problem would be the Show Desktop-button, but I found a way to solve that with Compiz (see the above post).

(What I'd do myself is just keep the program open on another desktop and use keyboard shortcuts to switch between them. But since being able to make the computer work the way I want it to was the biggest reason why I started using Linux in the first place, I think it's only fair to help others to do the same.. Windows and Mac users are forced to using their computers the way some corporate guy decided, we at least are free to make our own decisions.)

---

### Post by alex777 on 2009-01-13
Thank you, **mcduck**. It works. That's exactly what I wanted. You're a genius! I've never configured Compiz, so I wouldn't have done such a trick myself.

> What I'd do myself is just keep the program open on another desktop and use keyboard shortcuts to switch between them.

I could do this, but the point is I want my task list to appear before my eyes from time to time unintentionally as a reminder, otherwise I sometimes forget about it. And since I often press the Show Desktop Button anyway... voila, please remember your tasks, Alex! ;)

Many thanks!

---

### Post by VastOne on 2009-01-15
> **mcduck said:**
> 

(What I'd do myself is just keep the program open on another desktop and use keyboard shortcuts to switch between them. But since being able to make the computer work the way I want it to was the biggest reason why I started using Linux in the first place, I think it's only fair to help others to do the same.. Windows and Mac users are forced to using their computers the way some corporate guy decided, we at least are free to make our own decisions.)

Brilliant and so perfectly said...

Bravo Mr McDuck Bravo

Take a well earned bow....

---

### Post by webgod on 2009-07-12
> **mcduck said:**
> 

(...)

So, here's what you need to do:
1. In General settings, disable "Hide Skip Taskbar windows"
2. In Window Rules, add your program to "Skip Taskbar" & "Below"-groups. (and "Sticky", if you want it to appear on every desktop.)
3. Actually since the window won't show in taskbar you don't want to minimize it. It would just disappear into nothing. So add it into the "Non minimizable windows"-group as well to avoid that problem..

Now the program window will always stay behind other windows, and will not be hidden by "Show Desktop". The only loss is that it won't show in the taskbar any more.

Thank you so much!

That's exactly what I was looking for.

---

