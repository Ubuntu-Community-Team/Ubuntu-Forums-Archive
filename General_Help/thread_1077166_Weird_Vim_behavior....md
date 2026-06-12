---
title: "Weird Vim behavior..."
date: 2009-02-22
forum: General Help
---

### Post by mharvey87 on 2009-02-22
:confused:When I use the arrow keys or the mouse scroll while in insert mode random letters are inserted 1 line at a time.
Pressing up 3times and then scrolling down twice would produce the following:
A
A
A
B
B

I was just wondering how I could change this so that even in insert mode those keys and the mouse scroll wheel would just move the cursor and scroll.
Thank in advance for the help.

---

### Post by geirha on 2009-02-22
By default, only vim-tiny is installed, which runs in vi compatability mode. Install [vim](apt:vim) for the regular vim editor, then edit /etc/vim/vimrc and uncomment the lines you prefer (you probably want syntax highlighting, automatic indentation and stuff like that) ```
sudo vim /etc/vim/vimrc
```

EDIT: Oh and if you want to use the mouse, I recommend you try [vim-gnome](apt:vim-gnome).

---

### Post by capscrew on 2009-02-22
See here: [http://www.workhabit.com/labs/fixing-broken-arrow-keys-vim-ubuntu]("http://www.workhabit.com/labs/fixing-broken-arrow-keys-vim-ubuntu")

Read it all, especially the comments.

Edit: As geirha has said: If you want all of VIM then install vim-full --
```
apt-get install vim-full 
```

---

### Post by mharvey87 on 2009-02-22
Thanks, I downloaded gVim a minute ago and that solved the problem.
That article was Exactly what I was looking for, thanks again.

---

### Post by heindsight on 2009-02-22
> **geirha said:**
> code]sudo vim /etc/vim/vimrc[/code]


I usually find it better to do
```
cp /etc/vim/vimrc ~/.vimrc
vim ~/.vimrc
```

If you're the only person ever using the machine, then it doesn't matter much, but I often find myself working in multiuser environments where I don't have root access. Apart from not always having permission to edit the systemwide vimrc, I find keeping my own ~/.vimrc useful simply because, if I find myself reinstalling, I don't have to worry about losing my vimrc because it's in my /home partition which I keep intact.

---

