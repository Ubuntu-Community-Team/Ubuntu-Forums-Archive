---
title: "the mouse and ssh'ing emacs"
date: 2009-03-16
forum: Desktop Environments
---

### Post by jeffATwork on 2009-03-16
I ssh to a machine where I then work in emacs. I'm trying to pass mouse clicks into the emacs session so I can switch buffers/position by clicking rather than 'C-x o'ing.

Putting 

(global-set-key [mouse-1] '(lambda (event)
                 (interactive "e")
                 (mouse-set-point event)))

in my init.el file gets me part way. (The code was passed to me by someone else who hasn't got things working either.) 

Problem is, mouse-set-point has no function in emacs 22, as I am told when I click in a buffer in my emacs session. At least, the clicks are being passed in.

I think the above snippet is xemacs code, because I found a definition for mouse-set-point in some xemacs code files. Of course, that function depends on other functions, etc.

Suggestions?
Thanks!

---

