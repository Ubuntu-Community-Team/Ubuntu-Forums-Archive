---
title: "Emacs-snapshot, xft and scandinavian characters"
date: 2009-06-12
forum: General Help
---

### Post by glaze on 2009-06-12
When I enter scandinavian characters to Emacs, they are displayed only after I type something after them. Example: If I want to write: "käpy", I see 'ä' only after I've typed 'p'. Has anyone else this problem? These relevant lines are in my .emacs:
```

(prefer-coding-system
      'utf-8)
(set-language-environment 'UTF-8)
(set-default-coding-systems             'utf-8)
(setq file-name-coding-system           'utf-8)
(setq default-buffer-file-coding-system 'utf-8)
(setq coding-system-for-write           'utf-8)
(set-keyboard-coding-system             'utf-8)
(set-terminal-coding-system             'utf-8)
(set-clipboard-coding-system            'utf-8)
(set-selection-coding-system            'utf-8)

```
.Xresources has these lines:
```

Xft.hinting: 1
Emacs.font: Monospace-10

```

---

