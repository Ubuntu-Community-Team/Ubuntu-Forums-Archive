---
title: "how can I cut-and-paste from emacs to shell or vice versa"
date: 2007-05-12
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-05-12
how can I cut-and-paste from emacs to shell or vice versa?

I try it, it doesnot copy the selected to the clipboard.

Thank you.

---

### Post by dogamnit on 2007-05-12
You can use the menu commands, or

clipboard-kill-ring-save

and

clipboard-yank

---

### Post by rockdon on 2007-05-12
You should be able to use the X clipboard to go either way. I'm not sure how emacs does it, but i know to do it with vim, its kinda odd.

Usually, copying in vim is done with selection and the ```
y
``` command to "yank" text. To copy to the X clipboard however, one must select the text and use```
 "*y
``` to do so. This will copy the text from vim (or gVim) to the X clipboard, allowing pasting via middle click.

HTH

---

### Post by cdupree on 2007-07-09
Thanks, dogamnit :guitar: , you solved my problem too!  I was struggling with this feature, which worked out of the box on every other system I'd loaded Emacs onto (and that's saying something).

BTW, It appears you can set the cut and paste commands to use the clipboard automatically with "menu-bar-enable-clipboard".

---

