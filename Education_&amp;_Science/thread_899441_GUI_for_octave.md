---
title: "GUI for octave??"
date: 2008-08-24
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2008-08-24
Is there a GUI for octave.
I downloaded octaveplot from the repos, the explanation given there said that it was the GUI for octave. How do i start it. If someone can tell me if there is any GUI for octave(note i don't want to download qtoctave-the kde version for octave)

---

### Post by rye_ on 2008-08-24
hi,

I think you may mean octplot?
if so, it's not a gui but an alternative to gnuplot for drawing graphs (I think gnuplot is much better btw)

As for the need for a gui, I don't see one.
terminal and a text editor should suite your needs fine.  Look at scilab, it's gui implementation makes it no better that octave.

---

### Post by janne_ph on 2008-08-24
Hi. I mostly use octave with the terminal, but I've tried the GUI qtoctave and it works fine. From what I've heard there is a couple of different GUIs, but I have only tested one.

---

### Post by Xnst on 2008-08-27
Hi,

to activate octplot you type
```

>: toggle_octplot

```
then you will have the octplot plot output instead.

As for a GUI: I do not know if this goes under GUI but I mostly run octave in emacs using matlab.el  (in the emacs-goodies package) and
think it is perfect.

Just add the following in the .emacs (see head of matlab.el)

```


;; octave stuff. Uses matlab.el

(setq auto-mode-alist (remq '("\\.m\\'" . objc-mode) auto-mode-alist))

(autoload 'matlab-mode "matlab" "Enter MATLAB mode." t)
(setq auto-mode-alist (cons '("\\.m\\'" . matlab-mode) auto-mode-alist))
(autoload 'matlab-shell "matlab" "Interactive MATLAB mode." t)

( setq matlab-shell-command "octave"
	 shell-command-echoes nil)
(setq matlab-shell-command-switches '("--traditional"))
(setq matlab-shell-buffer-name "octave")
(defalias 'octave-shell 'matlab-shell)


```

As an example, there is the C-c C-s key combination to save and run a m-file, really useful. 

Okay, I know! Not all people like emacs, but if you do - this solution is just magic.

---

