---
title: "two little cd command questions"
date: 2009-05-24
forum: General Help
---

### Post by netimen on 2009-05-24
1. I used cd command to some directory.Is there any way to return to the previous location? I mean not ```
cd ..
``` but an universal way of returning back.
2. For example I type ```
locate russian.lbx
``` and get ```
/usr/share/texmf-texlive/tex/latex/biblatex/lbx/russian.lbx
``` If I want to get to that location, can I somehow use the result of previous locate call and not typing manually that long path?

---

### Post by kmitnick on 2009-05-24
there is a temp method but this method won't be there when you close the bash shell

it is using the export command
```
export old_dir=usr/share/texmf-texlive/tex/latex/biblatex/lbx/russian.lbx
```

then it can be used as $old
so if it is a dir without the last/russian.lbx 
you can use
```
cd $old
```

---

### Post by kmitnick on 2009-05-24
or you can 
```
cd `locate russian.lbx`
```

---

### Post by madmaxou on 2009-05-24
1) Yeah there is one:
```
cd ~-
```With this one you'll get to the dir you were last in..
It's less complicated than the other command...

---

### Post by netimen on 2009-05-24
Thank you, but in your first method I should manually type that path, when I do ```
export old_dir=usr/share/texmf-texlive/tex/latex/biblatex/lbx/russian.lbx
```
and with your second method I get
```
bash: cd: usr/share/texmf-texlive/tex/latex/biblatex/lbx/russian.lbx: Not a directory
```

---

### Post by netimen on 2009-05-24
> **madmaxou said:**
> 1) Yeah there is one:
```
cd ~-
```With this one you'll get to the dir you were last in..
It's less complicated than the other command...

Yeah, that's it!

---

