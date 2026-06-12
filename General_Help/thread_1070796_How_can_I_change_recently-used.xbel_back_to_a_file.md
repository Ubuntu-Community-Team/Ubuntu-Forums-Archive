---
title: "How can I change recently-used.xbel back to a file from a directory?"
date: 2009-02-15
forum: General Help
---

### Post by fifth_rune on 2009-02-15
Hi,

A while back I wanted to get rid of 'recent documents' so I followed some advice in the forums and used

> $ rm ~/.recently-used.xbel $ mkdir ~/.recently-used.xbel

to get rid of the file and replace it as a directory (seems like a common hack/fix to the problem).  However, now I want to undo this and change it back to a file, but I can't do anything with the directory, either by removing it or changing permissions.  All I get is "operation not permitted" even when I am root.

---

### Post by geirha on 2009-02-15
What does this say?
```
rmdir -v ~/.recently-used.xbel
```

---

### Post by fifth_rune on 2009-02-15
> **geirha said:**
> What does this say?
```
rmdir -v ~/.recently-used.xbel
```

Result:

> rmdir -v ~/.recently-used.xbel
rmdir: removing directory, /home/david/.recently-used.xbel
rmdir: failed to remove `/home/david/.recently-used.xbel': Operation not permitted


---

### Post by geirha on 2009-02-15
And doing it with sudo gives the same output? what does these commands say?
```

ls -ld ~/.recently-used.xbel
fuser ~/.recently-used.xbel

```

---

### Post by fifth_rune on 2009-02-15
> **geirha said:**
> And doing it with sudo gives the same output? what does these commands say?
```

ls -ld ~/.recently-used.xbel
fuser ~/.recently-used.xbel

```

Output:

> david@Highwind:~$ ls -ld ~/.recently-used.xbel
drwxr-xr-x 2 david david 4096 2007-06-23 11:31 /home/david/.recently-used.xbel
david@Highwind:~$ fuser ~/.recently-used.xbel


I also ended up with a recently-used plain text file in the home directory but the recently-used.xbel directory was still there.  Sudo with the prior command gives the same result as well.

---

### Post by geirha on 2009-02-16
Seems the folder might be in use somehow, but fuser should have printed something if that were the case. Try logging out, then hit Ctrl+Alt+F1 to get to a console terminal, log in there and run rmdir ~/.recently-used.xbel. Same error? Hit Ctrl+Alt+F7 (or possibly F8 or F9) to get back to the login screen.

---

### Post by fifth_rune on 2009-02-16
No such luck, same message when tried as both user and root "Operation not permitted"

---

### Post by geirha on 2009-02-16
I did a little google on how to disable recently used, and one of the suggestions I found was setting the immutable flag. Have you by any chance done this?
```
lsattr -d ~/.recently-used.xbel
```
Does it have an i in there?

---

### Post by fifth_rune on 2009-02-16
> **geirha said:**
> I did a little google on how to disable recently used, and one of the suggestions I found was setting the immutable flag. Have you by any chance done this?
```
lsattr -d ~/.recently-used.xbel
```
Does it have an i in there?

I do not believe that I have.  Is there a way to check?

---

### Post by geirha on 2009-02-16
Yes, by running lsattr (list attributes) in a terminal:
```
lsattr -d ~/.recently-used.xbel
```
If there's no attributes set, there will just be alot of dashes (---), but if  
there's an i in there, then the attribute is on, turn it off with the following if that is the case:
```
sudo chattr -i ~/.recently-used.xbel
```

---

### Post by fifth_rune on 2009-02-16
> **geirha said:**
> Yes, by running lsattr (list attributes) in a terminal:
```
lsattr -d ~/.recently-used.xbel
```
If there's no attributes set, there will just be alot of dashes (---), but if  
there's an i in there, then the attribute is on, turn it off with the following if that is the case:
```
sudo chattr -i ~/.recently-used.xbel
```

Worked like a charm!  Thanks a lot!

---

