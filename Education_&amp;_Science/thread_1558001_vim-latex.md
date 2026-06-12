---
title: "vim-latex"
date: 2010-08-21
forum: Education &amp; Science
---

### Post by SuperMiguel on 2010-08-21
So im trying to instal vim-latex on ubuntu, been researching alot but i gotten to no where.

Here is what i done so far:

Installed  “vim-gnome”, “vim-latexsuite”, and “vim-addon-manager.”
Next, i did sudo vim-addons -w install latex-suite

but when i go to gvim i just get a regular gvim, not the latex edition shown here: [http://vim-latex.sourceforge.net/screenshots/after-template.png](http://vim-latex.sourceforge.net/screenshots/after-template.png)

---

### Post by FreeTheBee on 2010-08-21
I recently started using this as well, but I added the plugin manually. The one in the repositories is only one version older though so, I guess that should be fine.
Did you make the necessary changes in your vimrc?

[http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html](http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html)

---

### Post by SuperMiguel on 2010-08-21
> **FreeTheBee said:**
> I recently started using this as well, but I added the plugin manually. The one in the repositories is only one version older though so, I guess that should be fine.
Did you make the necessary changes in your vimrc?

[http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html](http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html)

i dont have that file but ill create it..

created them and no go...

i also downloaded the file on their site, extracted in ~/.vim and when i go to gvim it looks like regular gvim.. ;(

got it i just needed to do ```
 gvim text.tex 
```

---

