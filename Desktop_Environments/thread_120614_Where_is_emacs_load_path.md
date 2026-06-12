---
title: "Where is emacs load path?"
date: 2006-01-22
forum: Desktop Environments
---

### Post by opiston on 2006-01-22
Hi all,
I downloaded python-mode.el which can help emacs recognize .py (python) files.

Here is the installation guide:
> 
;; To install, just drop this file into a directory on your load-path and
;; byte-compile it.  To set up Emacs to automatically edit files ending in
;; ".py" using python-mode add the following to your ~/.emacs file (GNU
;; Emacs) or ~/.xemacs/init.el file (XEmacs):
;;    (setq auto-mode-alist (cons '("\\.py$" . python-mode) auto-mode-alist))
;;    (setq interpreter-mode-alist (cons '("python" . python-mode)
;;                                       interpreter-mode-alist))
;;    (autoload 'python-mode "python-mode" "Python editing mode." t)
;;
;; In XEmacs syntax highlighting should be enabled automatically.  In GNU
;; Emacs you may have to add these lines to your ~/.emacs file:
;;    (global-font-lock-mode t)
;;    (setq font-lock-maximum-decoration t)


It told me to put the file on the load path and byte-compile it.
The way I byte-compile:
I open a emacs.
Type in M-x byte-compile.
Type in the path of the file.

However, I don't know where the load-path is.

Another question:
The installation guide told me to put some lines in /.emacs.
I don't see a /.emacs file anywhere in the system.
Is it referring to /etc/emacs/site-start.el? Or do I just create a file called .emacs in my home directory?

Any help will be appreciated.

Best Regards.
Opiston.

---

### Post by art on 2006-01-23
It should be, I guess
/usr/share/emacs/21.4/lisp
As for .emacs, it should be in your home directory. Check out this website [http://www.dotemacs.de/](http://www.dotemacs.de/), they have a lot about customizing your emacs.

---

### Post by opiston on 2006-01-23
Hi art,
Thanks for your help.
I finally got it to work.

Here is what I did to get python-mode to work.
I put python-mode.el into /usr/share/emacs/21.4/lisp.
Then I byte-compile the file using emacs: "M-x byte-compile", then type the filename

Put the following lines in .emacs:
> 
(setq auto-mode-alist (cons '("\\.py$" . python-mode) auto-mode-alist))
(setq interpreter-mode-alist (cons '("python" . python-mode)
				   interpreter-mode-alist))
(autoload 'python-mode "python-mode" "Python editing mode." t)

(global-font-lock-mode t)
(setq font-lock-maximum-decoration t)

You can find these commands in python-mode.el.

Then python-mode should be activated after you open .py files.

However, when I close .py files, sometimes it gives me two warnings:
> 
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset


but sometimes it doesn't, so I am not sure what's going on.

Best Regards
Opiston

---

