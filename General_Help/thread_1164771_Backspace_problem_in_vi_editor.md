---
title: "Backspace problem in vi editor"
date: 2009-05-20
forum: General Help
---

### Post by colau on 2009-05-20
Hi,
In vi editor backspace key is not working to delete a character from a line of text.

---

### Post by redmk2 on 2009-05-20
Are you in edit mode?

---

### Post by colau on 2009-05-20
> **redmk2 said:**
> Are you in edit mode?
Yes.

---

### Post by redmk2 on 2009-05-20
There is more than one package for vim.  There is vim-tiny for non gui and vim-gnome.  It sounds like you need to investigate other vim packages.

---

### Post by geirha on 2009-05-20
vi only allows you to use backspace to delete characters you've typed in the current insert mode. You should install [vim](apt:vim), which allows you to do what you want.

I also recommend you edit /etc/vim/vimrc to your liking after the vim package is installed.

---

### Post by asmoore82 on 2009-05-20
[SIZE="5"]**A:**[/SIZE] ```
sudo apt-get install vim-full
```

[SIZE="5"]**Q:**[/SIZE] What's the first thing **I** _need_ to do after _every_ Ubuntu install?

:lolflag:

---

### Post by colau on 2009-05-20
Thanks.

---

### Post by KeyserSoze93 on 2009-05-20
Exactly... I'm sure the reason many Ubuntu users rarely stray away from Gedit is because, on being told about this great Vi editor, they start in up and find it incredibly frustrating to use. If Ubuntu came with vim-full to start with, many more people would realise just what this incredible piece of software is really capable of!

> **asmoore82 said:**
> [SIZE="5"]**A:**[/SIZE] ```
sudo apt-get install vim-full
```

[SIZE="5"]**Q:**[/SIZE] What's the first thing **I** _need_ to do after _every_ Ubuntu install?

:lolflag:

---

