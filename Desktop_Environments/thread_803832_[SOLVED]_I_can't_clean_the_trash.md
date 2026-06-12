---
title: "[SOLVED] I can't clean the trash"
date: 2008-05-22
forum: Desktop Environments
---

### Post by pepeugomez on 2008-05-22
hello I got some files in my trash that doesn't want to go away.
I was so happy of been free of windows and now this.
can anyone help me with that?

juan:guitar:

---

### Post by aysiu on 2008-05-22
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo rm -r ~/.Trash/*
``` It's very important that you *paste* this command in the terminal. Do not retype it manually.

*sudo* means "Whatever I run, run with administrative privileges"

*rm* means "Remove"

*-r* means "Recursively"

*~/* means "/home/username"

*.Trash/* means "anything inside the trash folder"

---

### Post by unutbu on 2008-05-22
aysiu, it's a little confusing -- your advice, which is correct -- contradicts your sig, which is under most circumstances also correct... lol:)

---

### Post by logos34 on 2008-05-22
> **aysiu said:**
> Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo rm -r ~/.Trash/*
```

But if your running 8.04 hardy then the command would be:

**sudo rm -r ~/.local/share/Trash/***

(they moved it, why I know not)

---

### Post by pepeugomez on 2008-05-22
Sorry it is me again
I do as you tell me to but the sistem answer me that he can't do it because the file or the directorie doesn't exist.
sistem is in spanish i don't know if it is important.
thanks.

juan:guitar:

---

### Post by pepeugomez on 2008-05-22
logos 34 you was right.
thank you very much.
I'm so happy of quitting windows as when i was a Mac user.
Thanks.


juan:guitar:

---

### Post by logos34 on 2008-05-22
> **pepeugomez said:**
> logos 34 you was right.
thank you very much.
I'm so happy of quitting windows as when i was a Mac user.
Thanks.

no prob.  enjoy ubuntu

---

### Post by aysiu on 2008-05-22
Why did they move that? That's annoying. Good to know for the future, though.

---

### Post by erginemr on 2008-05-23
> **aysiu said:**
> Why did they move that? That's annoying. Good to know for the future, though.

I hear you. 

Not only that; they have also changed the way icon themes are loaded. This way, some icon themes in gnome-look.org that could be installed before without a hitch, can only be installed partly now.

---

### Post by Rekiem on 2009-02-11
That's awful I spent like 30 mins looking for my ~/.Trash directory is unfair!!

Anyway, thanks for the note!
Let's keep linuxing =)

Regards!
Mike

---

### Post by nasir8891 on 2009-04-04
```
sudo rm -r ~/.local/share/Trash/ *
```

thanks . the command is working properly for ubuntu 8.04 :p

---

