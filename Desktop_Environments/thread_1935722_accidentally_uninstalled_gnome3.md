---
title: "accidentally uninstalled gnome3"
date: 2012-03-04
forum: Desktop Environments
---

### Post by Alphamonkey on 2012-03-04
Well, I feel pretty stupid. I was uninstalling things in the ubuntu software center and wasn't paying much attention. I accidentally uninstalled the gnome3 environment. Now my computer wont boot up. If someone could tell me how to boot into a CLI interface and set up my network I think I can just install it again with apt or if there are easier ways please let me know. 

On a side note I am taking classes at a community college for an "introduction to Linux" and I am wondering if anyone can help me with this part of the lab: 

"Navigate back to your Lab04 directory and copy the file fileK from /home/cnet146/Files to your
current directory.
Use grep to find the indicated lines in the fileK file.
1. lines with square brackets
2. lines containing a word ending with s
3. lines with dates in January (Dates are American: month-day-year)
4. lines with dollar amounts of $1000 or more
5. lines with even dollar amounts (no cents)
($25.00 is an "even dollar amount," but $26.50 is not.) "

its basically just a lab on the different types of grep (grep -e, -E, -F, -w, etc)

any help with either would be greatly appreciated. Thanks.

---

### Post by cortman on 2012-03-04
If you can get to grub, boot into recovery mode, which will give you your CLI. Your network should work if you connect by default to a certain network.
And on your second question, you need to learn regular expressions. It's a fascinating sub language, almost beautiful in its utterly confounding (to the unlearned) syntax, and very powerful and effective. Google "introduction to regular expressions" and you'll find plenty of resources!

---

### Post by Alphamonkey on 2012-03-04
Ok, well first of all I would like to say thanks for your response it  was helpful. Especially the part about regular expressions. I was able  to boot into the terminal and I reinstalled using apt-get install  gnome-desktop-environment. I rebooted after doing that and it still gave  me the same problems so I pushed ctrl+alt+F1 to get to the terminal and  did startx. It took "somewhat" to my desktop. it is more similar to the  gnome classic except it doesn't have any drop down menus or anything.  Also, it does not allow me to move my mouse to the top left corner to  open the usual "gnome3 menu." So, I guess it's not going to be quite as  easy as I thought for me to get it back in normal condition. I am  considering just putting kubuntu on it as a quick fix unless someone has  a better suggestion.

---

### Post by cortman on 2012-03-05
Have you tried

```
sudo apt-get install gnome-shell
```

If that doesn't work for you, a clean re-install may be the best solution. Just make sure you back up your data first!

I'm almost completed with the O'Reilly book *Mastering Regular Expressions* by Jeffrey Friedl. It's a very in-depth book and really piqued my interest in regexes and their use.

---

### Post by pavi_elex on 2012-03-09
```
sudo apt-get install gnome-desktop-environment gdm x-window-system-core desktop-base

```

---

