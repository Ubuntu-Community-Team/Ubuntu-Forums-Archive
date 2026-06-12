---
title: "Cairo-dock opengl doesn't start"
date: 2010-01-03
forum: Desktop Environments
---

### Post by rahilm on 2010-01-03
when i run cairo-dock in non opengl mode , it works fine. But when i open it in opengl mode, it hangs to the maintenance mode.

when i run
```
cairo-dock -o
```

It gives the output
```
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1 Mesa 7.6
OpenGL vendor: Tungsten Graphics, Inc
OpenGL renderer: Mesa DRI Intel(R) 946GZ GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
labels : 1;1
cairo_dock_move_resize_dock ()
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:195)  
  Cairo-Dock has crashed (sig 11).
It will be restarted now (cairo-dock -o -m).
Feel free to report this bug on cairo-dock.org to help improving the dock !
iNbConfigDialogs <- 1
debut de boucle bloquante ...
```

---

### Post by fabounet on 2010-01-04
not totally sure, but it may be your drivers that crash the dock.
(Intel drivers are still in development)

to be sure, you can try with another theme, or even with the default theme by moving ~/.config/cairo-dock/current_theme.

also, try with indirect rendering (cairo-dock -oi)

---

### Post by rahilm on 2010-01-04
Nothing

---

### Post by fabounet on 2010-01-05
so, you should report this bug to the Intel drivers dev and X.org devs, with the maximum amount of details, it could help.

---

### Post by rahilm on 2010-01-08
Problem update:
Cairo dock opengl works in the Live-CD..
what do i do now??

---

### Post by llawwehttam on 2010-01-08
If you are using the open source drivers without 3d acceleration it is often impossible to launch the cairodock in open Gl.

Personally I think Avant is far nicer that cairo so if I were you I'd give it a go.

---

### Post by rahilm on 2010-01-08
> **llawwehttam said:**
> If you are using the open source drivers without 3d acceleration it is often impossible to launch the cairodock in open Gl.

Personally I think Avant is far nicer that cairo so if I were you I'd give it a go.

I already use AWN. Now that cairo has improved  a lot. I thought i'd give it a go

---

### Post by llawwehttam on 2010-01-08
> **rahilm said:**
> I already use AWN. Now that cairo has improved  a lot. I thought i'd give it a go


Hmm I tried cairo a few months back and hated it. It was far to unorganised for my liking. How has it improved?
I might give it a shot.

---

### Post by rahilm on 2010-01-08
can somebody get to cairo-dock.org ...firefox displays an error when i enter that address

---

### Post by rahilm on 2010-01-08
> **llawwehttam said:**
> Hmm I tried cairo a few months back and hated it. It was far to unorganised for my liking. How has it improved?
I might give it a shot.
no. i meant i used cairo-dock wayyyyy back when it was 1.0

---

### Post by rahilm on 2010-01-08
another problem:
i cannot connect to cairo-dock.org .. so there is no clock or dustbin theme..
cairo-dock is getting on my nerves..but i won't give up

---

### Post by fabounet on 2010-01-08
> Cairo dock opengl works in the Live-CD..
so it's a matter of installing the correct drivers


the site is temporarily down 
to get the themes :
```
cairo-dock -S http://themes.cairo-dock.vef.fr
```
or install the BZR version.

---

### Post by rahilm on 2010-01-08
> **fabounet said:**
> so it's a matter of installing the correct drivers


the site is temporarily down 
to get the themes :
```
cairo-dock -S http://themes.vef.fr
```or install the BZR version.

actually, its a matter of not messing with your xorg.conf. This is a lose-lose situation for me. I edited the xorg.conf and now, i am stuck with a single resolution but cairo-dock is working well.

hey thnx 4 the link.

and do i have to run it everytime? can it download them somewhere so i can have peace of mind?

---

### Post by fabounet on 2010-01-08
when you install a theme it is stored on your hardrive, and then is local.
until you try it, it is distant (on the server).

you can just set this command at startup, so that you don't have to type it, or switch to the Launchpad version ;)

---

### Post by rahilm on 2010-01-09
hey..thnx 4 the help guys. but now i think cairo-dock doesn't suit my needs. in order to get it work i have to change my xorg.conf file and the new X almost hangs my system. I'll do that only to show off in front of my friends (fans of 7 and its effects).
I am switching to GNOME do dock. it doesn't have much configurability but it gets the job done.

just out of curiousity, what is this BZR version and the launchpad version??

---

### Post by fabounet on 2010-01-09
you could just launch it with cairo-dock -c then.

BZR is the development version.

---

