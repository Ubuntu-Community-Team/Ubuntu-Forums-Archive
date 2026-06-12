---
title: "FVWM does not use gtk themes in gtk applications :-("
date: 2006-06-20
forum: Desktop Environments
---

### Post by André on 2006-06-20
Hi everybody,

i am trying out FVWM. When i start any gtk applications they come up but it is like they ignore my gtk theme.

//edit:
By this i mean the gtk applications do not use the same theme i have chosen for my applications in Gnome.

Do you have any idea how to make them use it?

Greeting and thanks in advance
André

---

### Post by ThomasAdam on 2006-06-20
[QUOTE=André]Hi everybody,

i am trying out FVWM. When i start any gtk applications they come up but it is like they ignore my gtk theme.

Do you have any idea how to make them use it?

Greeting and thanks in advance
André[/QUOTE]

Ignore it?  What do you mean?   Note that FVWM has NOTHING to do with the rendering of your GTK apps -- that's GTK's problem.   You might want to check ~/.gtkrc-2.0 and/or use gtk-theme-switch to correct whatever your vague problem is.

-- Thomas Adam

---

### Post by André on 2006-06-21
Hi Thomas,

"ignores" means my gtk applications switch to the "Raleigh" theme. I found this nice theme "Ubuntu-Bluecurve" on gnome-look.org but when i start FVWM my gtk applications use a theme which looks pretty much like the "classical" theme (i hope it is called like this - i am using a german system where it is called "Klassisch").

Buttons, Menus, ... look like they use the "Raleigh" theme which was the default in earlier days afaik.

The theme works nice in Gnome. That's why i thought it may be a FVWM problem. It also works nice when i use the FVWM replace option but not when i start it directly from GDM.

Any idea? 

Greetings
André

---

### Post by André on 2006-06-23
Hi,

the problem still occurs. I tried to take a look at the gtk config files like .gtkrc, ... but i do not really get my error :-(

The themes should show up in FVWM when they show up in Gnome, shouldn´t they?

I really would appreciate any help.

Greetings
André

---

### Post by ThomasAdam on 2006-06-24
[QUOTE=André]Hi,

the problem still occurs. I tried to take a look at the gtk config files like .gtkrc, ... but i do not really get my error :-(

The themes should show up in FVWM when they show up in Gnome, shouldn´t they?[/quote]

In a manner of speaking.  Again, let me reiterate this for you, just so we're clear:  FVWM neither knows about nor cares about the rendering of an application's widgets.

As for fixing your question, because the GNOME developers still think the G in GTK stands for GNOME (morons), you probably need to run:

```
gnome-settings-daemon
```

Prior to starting any Gnome applications up.

-- Thomas Adam

---

### Post by André on 2006-06-25
Hi Thomas,

i changed the title of the post and some text in the first posting to make myself more clear.

I absolutely did not intend to blame anything for the problem. I am sorry if you had the feeling i did.

Altogether i can say that your tip works. Using the gnome-settings-deamon worked fine.

Thanks
André

---

