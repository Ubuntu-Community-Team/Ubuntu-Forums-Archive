---
title: "vim editor: How to save macros?"
date: 2009-01-18
forum: General Help
---

### Post by abcuser on 2009-01-18
Hi,
in Ubuntu 8.10 I have found excellent article about [how to record and play macros](http://www.thegeekstuff.com/2009/01/vi-and-vim-macro-tutorial-how-to-record-and-play/). But now I would like to save macro I have recorded. How?
Regards

---

### Post by phinullfermata on 2009-01-18
You don't exactly save the macro.

What you do is paste the register the macro is saved into (if you save the macro in register q, the command would be in bold, including the quote mark **"qp** )  in your vimrc file or something similar, and then use the map command in your vimrc to map a keystroke to the sequence that was recorded in the macro.  Which map command and what you map it to will depend on the circumstance, so you should look at **:help map** for more info.

---

### Post by samrat1985 on 2009-12-03
[FONT="Courier New"]LATE THAN NEVER. Saving MACROS in VIM Editor. See

[http://www.vim.org/scripts/script.php?script_id=2154](http://www.vim.org/scripts/script.php?script_id=2154)[/FONT]

[FONT="Arial Black"]Description
MARVIM - MAcro Repository for VIM

"Give your most complex macros a name and store it for future recall and use"

Problem statement(s):
-------------------------------
   * Can not remember those complex VIM macro sequences you use frequently?
   * Wish you could save those macros beyond your immediate session?
   * Wish you could share your VIM macros with each other?
   * Why not templates as well in the same script?

Features
------------
    * Recording of VIM macros into persistent storage for future use
    * Auto-complete based recursive search and load of stored VIM macros
    * Visually select and save templates into persistent storage
    * Macro namespaces, to permit organization of macros
    * Support for a default namespace based on filetype
    * Supports a shared macro repository for a team on a shared directory
    * Macro menu items in GVIM version for all main actions[/FONT]

---

### Post by Freaky#Funga on 2010-10-07
Hi, I don't know how did I acomplish this, but before reinstalling my ubuntu, I had somehow enabled autosave of settings.

Example: I enabled autoindent and syntax coloring and made some macros while editing some file in vim. :wq ... then I opened another file, and voila: same settings appeared here.

Can anyone tell me how to make this working again? :confused:

---

### Post by calmo on 2010-11-30
Documented (well!) here: 
[http://vim.wikia.com/wiki/Macros#Saving_macros](http://vim.wikia.com/wiki/Macros#Saving_macros)

---

