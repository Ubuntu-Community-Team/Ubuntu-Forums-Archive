---
title: "Emacs start screen doesn't respond"
date: 2009-03-09
forum: General Help
---

### Post by blastradius on 2009-03-09
I've installed Intrepid and used Synaptic to install emacs22-gtk, the problem is when I boot Emacs the initail screen is 'frozen', if I press a key it just beeps at me and if I click on the screen it displays a letter!

I can kill the buffer and it then drops me into the normal screen which seems to work fine.

My .emacs file (I copied from someone else) :-




(setq default-frame-alist (append (list
'(width . 120) ; Width set to 81 characters
'(height . 65)) ; Height set to 60 lines
default-frame-alist)) (fmakunbound 'c-mode)
(makunbound 'c-mode-map)
(fmakunbound 'c++-mode)
(makunbound 'c++-mode-map)
(makunbound 'c-style-alist)

(autoload 'c++-mode "cc-mode" "C++ Editing Mode" t)


(set-face-background 'region "green") ; Set region background color
(set-background-color "black") ; Set emacs bg color 
(global-font-lock-mode 1)
(setq font-lock-maximum-decoration t)

; Make Emacs use "newline-and-indent" when you hit the Enter key so
; that you don't need to keep using TAB to align yourself when coding.
(global-set-key "\C-m" 'newline-and-indent)

(global-set-key [f1] 'copy-region-as-kill) ; copy
(global-set-key [f2] 'kill-region) ; Cut
(global-set-key [f3] 'yank) ; Paste

(global-set-key [f5] 'compile)
(global-set-key [f6] 'buffer-menu)
(global-set-key [f7] 'dired-other-window)

(global-set-key [f12] 'shell)

(require 'paren) (show-paren-mode t) 



(global-set-key [f8] 'auto-fill-mode)


(load "cc-mode")
(require 'cc-mode)

---

