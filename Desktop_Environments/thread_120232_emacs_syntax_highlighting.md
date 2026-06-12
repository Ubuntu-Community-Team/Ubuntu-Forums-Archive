---
title: "emacs syntax highlighting"
date: 2006-01-21
forum: Desktop Environments
---

### Post by opiston on 2006-01-21
Hi all,
I just installed ubuntu on my computer. I use emacs as my editing tool, but I encountered a problem with emacs.

I selected options -> syntax highlighting (global font lock mode) to enable syntax highlighting.
I opened a .cc file and the highlightings are just fine.
However, when I open a .py file (python file), the codes are all in black text.

I figured my emacs does not have the necessary tool to detect a .py file. So, I downloaded a package "python-mode-1.0.tar.gz."
There are 4 files inside:

doctest-mode.el
pycomplete.el
pycomplete.py
python-mode.el

However, I don't know what to do with those files.
I tried puting the files inside of /etc/emacs/site-start.d, but it was still not working.

Can anyone tell me what I did wrong?

Best Regards
Opiston

---

### Post by lukew on 2007-01-04
> **opiston said:**
> Hi all,
I just installed ubuntu on my computer. I use emacs as my editing tool, but I encountered a problem with emacs.

I selected options -> syntax highlighting (global font lock mode) to enable syntax highlighting.
I opened a .cc file and the highlightings are just fine.
However, when I open a .py file (python file), the codes are all in black text.

I figured my emacs does not have the necessary tool to detect a .py file. So, I downloaded a package "python-mode-1.0.tar.gz."
There are 4 files inside:

doctest-mode.el
pycomplete.el
pycomplete.py
python-mode.el

However, I don't know what to do with those files.
I tried puting the files inside of /etc/emacs/site-start.d, but it was still not working.

Can anyone tell me what I did wrong?

Best Regards
Opiston

Either put the files in a dir in your emacs load-path or place the files in another dir and add that directory to your load-path.

I load everything fom ~/.custom_emacs/elisp/*

```

(add-to-list 'load-path (expand-file-name "~/.custom_emacs/elisp" ))

```

The files should then be loaded from somwhere in your custom emacs code.

The .emacs file located in ~/.emacs is lisp code. You can then load another el file by:

```
(load "lw-set-keys.el")

```


I hope this helps.

Luke

---

### Post by Spinelli on 2007-02-20
I am using Ubuntu Edgy. I just typed this at the command line.

```
sudo apt-get install python-mode
```

All of my .py files are automatically detected. I enabled font-lock-mode in Emacs by typing

```
M-x font-lock-mode
```
M-x means Alt+x.
Have fun!

---

