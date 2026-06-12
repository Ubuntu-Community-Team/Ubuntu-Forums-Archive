---
title: "[SOLVED] help configuring emacs"
date: 2008-12-18
forum: General Help
---

### Post by Despot Despondency on 2008-12-18
Hi, I'm pretty new to emacs and I'm still trying to configure it. I'm trying to figure out how to get skeletons to work.

At the moment I am getting the following error upon loading emacs

```

("emacs")
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 00debian-vars...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...done
Loading debian-ispell...done
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...done
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...done
Loading /etc/emacs/site-start.d/50psvn.el (source)...done


An error has occurred while loading `/home/gbrady/.emacs':

Invalid function: ~/.abbrev_defs

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

load-with-code-conversion: End of file during parsing: /home/gbrady/.abbrev_defs


```


My .emacs file looks like this

```

(setq abbrev-file-name ("/home/gbrady/.abbrev_defs"))
(read-abbrev-file abbrev-file-name t)
(setq dabbrev-case-replace nil)  ; Preserve case when expanding
(setq abbrev-mode t)

```

And then my abbreviation file is called abbrev_defs, which has the following

```

(define-abbrev-table 'cc-mode-abbrev-table '(
    ("foriter" "" test-skeleton 0)

(define-skeleton test-skeleton
  "Inserts link_to"
  "Link text: "
  "<%= link_to('" str "', :action => '" _ "') %>")

```

I'm not exactly sure how to sort this error out. I assume it the due to the first line of my emacs file.

---

### Post by iponeverything on 2008-12-18
```
(setq abbrev-file-name "/home/gbrady/.abbrev_defs")
(read-abbrev-file abbrev-file-name t)
(setq dabbrev-case-replace nil)  ; Preserve case when expanding
(setq abbrev-mode t)
```

(I ((didn't) try it to make it sure worked though))

---

### Post by Despot Despondency on 2008-12-18
Hey, that seemed to work. Thanks!

---

