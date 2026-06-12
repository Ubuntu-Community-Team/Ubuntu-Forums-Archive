---
title: "Symbolic links problem  9.04"
date: 2009-06-05
forum: General Help
---

### Post by pluscool on 2009-06-05
I have a problem making symbolic links. 

I tested the symbolic link:

:/$ ls -l | grep tvix

and the results:

drwxr-xr-x 2 julian root 4096 2009-06-05 22:35 tvixhd1

It didn't show the arrow "path -> path"  ](*,)as it should, like:

:/$ ls -l | grep tvix
lrwxrwxrwx 1 root root 25 2007-10-02 15:02 tvixhd1 -> /mnt/lacie/hellanzb/done/

I tried to make the symbolic link several times

any ideas? greatly appeciate!

---

### Post by jonobr on 2009-06-05
Looks like you didnt create a symbolic link??


The first ls seems to show its an actual directory you are listing

drwxr-xr- so there is nothing to link to , and so no --->

in the second example its a link.

---

### Post by Xanthomryr on 2009-06-05
How do you create the symlink?

It must be:
```
ln -s /path/to/file/or/dir linkname
```

By the way, there&#347; no deed to drep, "ls -l tvix" would do.

And you can see that your first example is a directory by the leading "d" at the permissions. Your second example has a leading "l" wich indicates a link.

---

### Post by pluscool on 2009-06-10
Thanks, I solved with your help. I made a silly mistake: I create an unnecessary directory with the same name before I made the symlink. I was assuming that I need it. :-)

---

