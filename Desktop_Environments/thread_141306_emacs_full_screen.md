---
title: "emacs full screen?"
date: 2006-03-08
forum: Desktop Environments
---

### Post by evaristegalois on 2006-03-08
I just installed emacs and am running into the following difficulty: How do I get Emacs to take up as much of the screen as possible (ideally full screen)? Right now I can see the gnome desktop both on top and bottom of my emacs screen which is not appealing and also means that when I press Alt-v, for example, I go to the gnome menu instead of getting the result for M-v in emacs. --evaristegalois

---

### Post by evaristegalois on 2006-03-08
Let me clarify: I know that in Terminal Mode I can go to full screen and get rid of the gnome desktop in the background--but I don't seem to be able to get rid of the Terminal's menu line on top of the screen. (Alt-v goes to ``view'', for example.)

---

### Post by evaristegalois on 2006-03-08
here is me answering my own question: in terminal mode (or inside the ``add launcher'') write 

gnome-terminal --command="emacs" --full-screen --hide-menubar

Looks beautiful, even better than in Windows, although for some reason the side-bar (to go up and down in the buffer) is not working properly (why?).

I also only have 8 colours to choose from for foreground and background -- I'll see what I can do to add more.

---

### Post by kaliumfredrik on 2008-01-27
Alternatively, emacs can be started in full screen mode by applying the -fs flag i.e. by issuing:

emacs -fs

Would be great to have a command for toggling full screen mode from within Emacs.

---

### Post by GSBoomer on 2008-02-05
I'm new-ish to running emacs, but find it extremely useful for some of the work I'm doing. I too would like to run it in a fullscreen mode, but when I start it with emacs -fs then then text all along the left margin.

Is there are way to get the text centered in the frame without opening two other frames and resizing them to the the preferred frame in the center?

---

### Post by stuarts on 2008-02-05
You can put the following in your .emacs file to control the size of the fringe on the left and right:
```
(set-fringe-mode 20)
```
Play with the value to find a size that works for you.

---

### Post by GSBoomer on 2008-02-06
Excellent! I figured,  since you can do anything in lisp, that there would be an easy way.

---

### Post by Aleph42 on 2008-02-26
personally, here is what I have in my .emacs to get rid of all the nuisance:

```
(setq inhibit-splash-screen t) ;; no splash screen

(progn
  (if (fboundp 'tool-bar-mode) (tool-bar-mode -1))  ;; no toolbar
  (menu-bar-mode -1) ;;no menubar
  (scroll-bar-mode -1) ;; no scroll bar
  )
```

Much better!

by the way, does someone know what to add to .emacs to get it to resize when the terminal window (in gnome-terminal) is resized?

---

