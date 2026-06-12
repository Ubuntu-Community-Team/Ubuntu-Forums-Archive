---
title: "Is there a key repeat line commands?"
date: 2009-03-15
forum: General Help
---

### Post by boothruwindow on 2009-03-15
I have not used the command line much on any system recently, but I remember the DOS command-line days. DOS would display the previous command (to save you repetitive typing) when you pressed the F3 key. Dare I hope that there's something like that in Linux?

Thanks.

---

### Post by lykwydchykyn on 2009-03-15
The up arrow does it.

---

### Post by warjowuch on 2009-03-15
Try arrow up! Arrow down goes (of course) in the opposite direction again :-)

---

### Post by sisco311 on 2009-03-15
if you want to run the previous command again, type:
```
!!
```

e.g.
```

echo "this command"
!!

nano /etc/fstab
sudo !!
```

--------------------------------------------------------------

you can press Ctrl+R to search in history.

---

### Post by sdennie on 2009-03-15
Another useful one that I use constantly is !$.  It means, "The last argument of the last command".  For example:

```

cp somefile /some/long/directory/name
cd !$

```

That copies a file and then changes to /some/long/directory/name.

Also, if you are a vi user, you can enable bash vi bindings by adding the following to ~/.bashrc:

```

set -o vi

```

In that case, you can hit <Esc> and then k/j to move through the history.  Some users find this a lot more natural than using the arrow keys.  ;)

---

### Post by sisco311 on 2009-03-15
oh, and to return to the previous working directory:
```
cd -
```

e.g.
```
#cd /very/very/very/long/path/to/dir
#pwd
/very/very/very/long/path/to/dir
#cd 
#pwd 
/home/username
#cd - 
/very/very/very/long/path/to/dir
```

---

### Post by boothruwindow on 2009-03-15
Wow, thanks for all the help! :D I'm not used to a system with so many options, it's hard to guess where to start.

I am kinda red in the face for not having thought to try the Up Arrow first - not me, I got stumped after punching every F button, and finding that nearly all did nothing.

Thanks again, all!

---

### Post by lvleph on 2009-03-15
```
cd
```
returns you to home directory
```
cd ~/dir
```
sends you to /home/<user>/dir
```
rename 's/<regex>/<replace>/' <file>
```
this will find the pattern <regex> in <file> and replace it with <replace>. Be careful with this one and test it out with the -n option; i.e.,
```
rename -n 's/<regex>/<replace>/' <file>
```

---

