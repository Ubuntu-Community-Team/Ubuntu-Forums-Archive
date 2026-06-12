---
title: "Emacs: no syntax highlighting"
date: 2009-03-17
forum: General Help
---

### Post by Uruclef on 2009-03-17
Hi everyone! I have Emacs installed on my Ubuntu 8.10, but syntax highlighting is simply not working. In various "modes" (ex. C++-mode) auto-identation and other features work, but syntax highlighting doesn't. With the same .emacs, on Debian syntax highlighting works correctly. 

Thank you!

---

### Post by unutbu on 2009-03-17
Please post your .emacs.
If there is private stuff in there, be sure to cut.

I'll try yours, ediff it with mine, and see if I can find the problem.

---

### Post by Uruclef on 2009-03-17
Thank you, but I don't think the .emacs is the real problem, since it works fine in Debian. The problem remains even if I'm not using a customized .emacs at all. Anyhow, here it is:

```

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(inhibit-startup-screen t)
 '(speedbar-frame-parameters (quote ((minibuffer) (width . 20) (border-width . 0) (menu-bar-lines . 0) (tool-bar-lines . 0) (unsplittable . t) (set-background-color "black")))))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(background "blue")
 '(font-lock-builtin-face ((((class color) (background dark)) (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "MediumAquamarine"))))
 '(font-lock-constant-face ((((class color) (background dark)) (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "green2"))))
 '(font-lock-function-name-face ((t (:foreground "SkyBlue"))))
 '(font-lock-keyword-face ((t (:bold t :foreground "CornflowerBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "LimeGreen"))))
 '(font-lock-type-face ((t (:foreground "#9290ff"))))
 '(font-lock-variable-name-face ((t (:foreground "PaleGreen"))))
 '(font-lock-warning-face ((((class color) (background dark)) (:foreground "yellow" :background "red"))))
 '(highlight ((t (:background "CornflowerBlue"))))
 '(list-mode-item-selected ((t (:background "gold"))))
 '(makefile-space-face ((t (:background "wheat"))))
 '(mode-line ((t (:background "Navy"))))
 '(paren-match ((t (:background "darkseagreen4"))))
 '(region ((t (:background "DarkSlateBlue"))))
 '(show-paren-match ((t (:foreground "black" :background "wheat"))))
 '(show-paren-mismatch ((((class color)) (:foreground "white" :background "red"))))
 '(speedbar-button-face ((((class color) (background dark)) (:foreground "green4"))))
 '(speedbar-directory-face ((((class color) (background dark)) (:foreground "khaki"))))
 '(speedbar-file-face ((((class color) (background dark)) (:foreground "cyan"))))
 '(speedbar-tag-face ((((class color) (background dark)) (:foreground "Springgreen"))))
 '(vhdl-speedbar-architecture-selected-face ((((class color) (background dark)) (:underline t :foreground "Blue"))))
 '(vhdl-speedbar-entity-face ((((class color) (background dark)) (:foreground "darkGreen"))))
 '(vhdl-speedbar-entity-selected-face ((((class color) (background dark)) (:underline t :foreground "darkGreen"))))
 '(vhdl-speedbar-package-face ((((class color) (background dark)) (:foreground "black"))))
 '(vhdl-speedbar-package-selected-face ((((class color) (background dark)) (:underline t :foreground "black"))))
 '(widget-field ((((class grayscale color) (background light)) (:background "DarkBlue")))))

```

---

### Post by jjmerelo on 2009-03-18
Same problem here. Neither emacs nor xemacs higlight anything. Did you find a solution?

---

### Post by Uruclef on 2009-03-18
No, not yet.. :( Is this a known Ubuntu bug at least?

---

### Post by Uruclef on 2009-03-18
Ok, I just found out that this bug is present in emacs22 but NOT in emacs21. emacs21 works just fine.

---

### Post by unutbu on 2009-03-19
You might also want to try emacs-snapshot. It has syntax highlighting, and also support for TrueType fonts. If you use Intrepid, it is in the official repositories. If you use pre-Intrepid Ubuntu, there are instructions (and a screenshot) here
[http://peadrop.com/blog/2007/01/06/pretty-emacs/](http://peadrop.com/blog/2007/01/06/pretty-emacs/)
to install it from Alexandre Vassalotti's ppa repository.
Alexandre Vassalotti is the Ubuntu package maintainer for emacs.

---

### Post by jjmerelo on 2009-03-19
Almost, but not quite. Quite beautiful, by the way. I tried hi-lock-mode and it looks _very_ colored now. Maybe it's not set by default, and it was before.

---

