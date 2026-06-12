---
title: "terminal/emacs does not recognize Home &amp; End keys"
date: 2006-07-30
forum: Desktop Environments
---

### Post by mpx on 2006-07-30
I've Kubuntu 6.06. When I login from a different computer via SSH, and launch emacs from the terminal (without x-server), emacs does not recognize Home and End keys. However if I login directly on the kubuntu computer and launch emacs, (this brings up X-version of emacs) the Home and End keys are recognized. Both computers have identical keyboards (Micrsoft Natural Keyboard Pro).

Running the following on the remote terminal
$env | grep TERM
TERM=screen
TERMCAP=SC|screen|VT 100/ANSI X3.64 virtual terminal:\
COLORTERM=
----

Could the problem due to the fact that terminal is being recongized as VT100? Please help.

---

### Post by lukew on 2007-01-06
> **mpx said:**
> I've Kubuntu 6.06. When I login from a different computer via SSH, and launch emacs from the terminal (without x-server), emacs does not recognize Home and End keys. However if I login directly on the kubuntu computer and launch emacs, (this brings up X-version of emacs) the Home and End keys are recognized. Both computers have identical keyboards (Micrsoft Natural Keyboard Pro).

Running the following on the remote terminal
$env | grep TERM
TERM=screen
TERMCAP=SC|screen|VT 100/ANSI X3.64 virtual terminal:\
COLORTERM=
----

Could the problem due to the fact that terminal is being recongized as VT100? Please help.


There is no home and end key in emacs.


Beginning of buffer
Esc C-<

End of Buffer
Esc C->

Or you can redefine your keys.


(global-set-key [HOME]       'beginning-of-buffer)
(global-set-key [END]        'end-of-buffer)



I hope this helps.

Quick question though. Does dragging and droping in emacs work for you? It does not for me and I can not find and reference of anyone else not having it working. GNU suggests it should just work for files and text. 

Cheers 

Luke

---

