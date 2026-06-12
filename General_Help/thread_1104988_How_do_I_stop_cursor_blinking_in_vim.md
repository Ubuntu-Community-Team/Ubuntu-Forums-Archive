---
title: "How do I stop cursor blinking in vim?"
date: 2009-03-24
forum: General Help
---

### Post by newbuntus on 2009-03-24
I tried a few things including set guicursor=a:blinkon0 but nothing I tried worked. Anyone know how this is done?

---

### Post by kryptikos on 2009-03-24
Are you using the small included VIM that came with the distribution? If you run :version you'll probably see this is not a fully loaded VI. My version shows that it is a small version without GUI and does not include the guicursor (gcr) options. Might need to deploy the full mama:

[http://www.vim.org/download.php#unix]("http://www.vim.org/download.php#unix")

---

### Post by fcuk112 on 2009-03-24
press alt-f2, run gconf-editor, navigate to /desktop/gnome/interface, uncheck cursor_blink.

---

### Post by newbuntus on 2009-03-24
thanks fcuk112 that works in X. Is there a way to do this in the virtual terminal as as well? 

Kryptikos, I only had the guicursor in that command because the commands I found on the net relating to cursor blinking all seemed to specify a gui cursor. Is there a way to specify a non-gui cursor? I had a look at a section on cursors in vim's help, but I find vim's help extremely confusing.

---

