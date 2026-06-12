---
title: "emacs init file"
date: 2009-01-05
forum: General Help
---

### Post by evaristegalois on 2009-01-05
I want Emacs to insert softbreaks after column-fill. auto-fill will do this, but it will insert hardbreaks instead of softbreaks. visual-line-mode will do it, but not after column-fill, only just before it you hit the right side of your window. longlines-mode seems to do it alright, but I can only call it when I am in a buffer, not automatically from the Emacs init file. (setq-default longlines-mode t) in .emacs didn't do it. Any suggestions?

---

### Post by jpkotta on 2009-07-31
This should be pretty close:
```

(add-hook 'find-file-hook
          (lambda ()
            (longlines-mode 1)
            ))

```

I hear Emacs 23.1 has a replacement for longlines-mode.

---

