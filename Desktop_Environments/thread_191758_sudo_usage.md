---
title: "sudo usage"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Cable on 2006-06-07
What command do I use with sudo to copy a whole directory from one place to another?  Also, what's a good website to check out for sudo usage references/manuals?

---

### Post by scxtt on 2006-06-07
there really isn't much to sudo - just a quick way to "pretend" to be root (or any user, i suppose - to some degree) ... the man page (man sudo) should answer any question you have ...

to move a directory, if you're in your home dir (~):

sudo mv move_dir/ /dir/where/i_am/moving/it

would move "move_dir" to /dir/where/i_am/moving/it/move_dir

and you might not need to sudo, depending on what and where you're moving ...

---

### Post by gerbman on 2006-06-07
[QUOTE=Cable]What command do I use with sudo to copy a whole directory from one place to another?[/QUOTE]If you're the owner of the directory you don't need to use sudo, just do ```
cp -R <current dir> <copied dir>
```If you're not the owner, put sudo at the beginning.

---

### Post by Cable on 2006-06-07
Just trying to move a directory to a folder on my root partition, and it won't let me via Nautilus.  I'm assuming it's supposed to do that...seems a little annoying though.  Why does it do that?

---

### Post by aysiu on 2006-06-07
Alt-F2 ```
gksudo nautilus
```

---

### Post by gerbman on 2006-06-07
[QUOTE=Cable]Just trying to move a directory to a folder on my root partition, and it won't let me via Nautilus.[/QUOTE]Try performing the move in a terminal Window using the previous poster's "mv" command.> I'm assuming it's supposed to do that...seems a little annoying though.  Why does it do that?Linux is restrictive by default, unlike Windows. This is a good thing because it prevents programs executed by the user from gaining admin privileges (unless the user gives them to the program explicitly). It's a little annoying, but it's much more secure.

---

### Post by scxtt on 2006-06-07
yeah, it's for our protection ...

:mrgreen:

i generally use a:

$:> sudo nautilus

when i'm in a hurry ...

---

### Post by aysiu on 2006-06-07
[QUOTE=Cable]Also, what's a good website to check out for sudo usage references/manuals?[/QUOTE] [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

