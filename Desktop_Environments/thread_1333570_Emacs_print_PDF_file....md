---
title: "Emacs print PDF file..."
date: 2009-11-21
forum: Desktop Environments
---

### Post by Barriehie on 2009-11-21
Hello, I've been trying to get emacs to print to my PDF printer but it's resolutely trying to print to my HP.  I would like the PDF printer to be the default.  Does anyone have any suggestions for this issue???

Here's my .emacs and .emacs-custom.el

.emacs
```

(setq custom-file "~/.emacs-custom.el")
(load custom-file)

```

.emacs-custom.el
```

;;
;; .emacs-custom.el
;; 

;; Goto column function
(defun goto-column-number (number)
"Untabify, and go to a column number within the current line (1 is beginning
of the line)."
(interactive "nColumn number ( - 1 == C) ? ")
(beginning-of-line)
(untabify (point-min) (point-max))
(while (> number 1)
 (if (eolp)
     (insert ? )
   (forward-char))
 (setq number (1- number))))

;; Highlight the current line
;;(global-hl-line-mode 1)

;; column numbers
(setq column-number-mode t)

;; Resize window on load
(setq initial-frame-alist
      `((left . 50) (top . 95)
        (width . 100) (height . 36)))

;; for emacs to insert spaces instead of tab chars
(setq-default indent-tabs-mode nil);

;; Use a color theme
(require 'color-theme)
(setq color-theme-is-global t)
(color-theme-word-perfect)


;; Set the font
(set-default-font "-adobe-courier-bold-r-normal--14-100-100-100-m-90-iso8859-1")


;; Turn on the menu bar
(menu-bar-mode 1)


;; disable splash screen and startup message
(setq inhibit-startup-message t)


;;  Global font lock mode ON
(global-font-lock-mode t)


;; No zoning!!!
(zone-when-idle 0)


;; Make the cursor blink
(blink-cursor-mode 1)


;; Line numbering macro
(fset 'linenumbers
   (lambda (&optional arg) "Keyboard macro." (interactive "p") (kmacro-exec-ring-item (quote ([134217848 115 101 116 110 117 45 109 111 100 101 return] 0 "%d")) arg)))


;; Bind to key F2
(global-set-key [f2] 'linenumbers)


;; save the editor state
(desktop-save-mode 1)


;; Make emacs use the clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)


;; Use the Printing Package
(require 'printing)
(pr-update-menus)


;; set the PDF printer as default
(setq printer-name "PDF_file_generator")
(setq printer-name t)
(setq ps-printer-name "PDF_file_generator")
(setq ps-printer-name t)


;; Numbered Backups
(setq version-control t)
(setq backup-directory-alist '(("." . "/home/barrie/emacs/backups")))


(put 'upcase-region 'disabled nil)


;; Setup bookmarks file
(setq bookmark-default-file "~/.emacs.d/bookmarks" bookmark-save-flag 1)


(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(column-number-mode t)
 '(display-time-mode t)
 '(fringe-mode 0 nil (fringe))
 '(ps-printer-name nil)
 '(scroll-bar-mode (quote right))
 '(show-paren-mode t)
 '(speedbar-frame-parameters (quote ((minibuffer) (width . 20) (border-width . 0) (menu-bar-lines . 0) (tool-bar-lines . 0) (unsplittable . t) (set-background-color "black"))))
 '(transient-mark-mode t))
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

TIA,
Barrie

---

### Post by Barriehie on 2009-11-21
I kept digging and found this [post](http://ubuntuforums.org/showthread.php?t=725095).

Barrie

---

