---
title: "How to protect /home Directory?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by tubunu2005 on 2005-07-14
I created a second user and had to realise that my own home directory was accessible to him. How can I change that?

In general, only a user should be able to access his home directory, nobody else.

Tubunu

---

### Post by felipe on 2005-07-14
change permissions to your home directory with Nautilus, make sure "others" don't have read/execute permissions.

...or

chmod o-rx /home/tubunu

:-)

EDIT:

o = affects "others"
- = take away
rx = read/execute permissions

you may want to read the manual page for chmod

---

### Post by tubunu2005 on 2005-07-14
Thank you!

Tubunu

---

### Post by JayCnrs on 2005-07-14
I noticed this too, I was just wondering why Ubuntu sets the permissions this way. I have changed the home directory by using

chmod  700 /home/username

---

### Post by doclivingston on 2005-07-15
By default your home directory should be chmod'ed 711 (at least mine are), which means that other users can go through your home directory to get to other things (especially "public_html" is you have that set up for a web server), but they can't read files, or even see them.

---

### Post by JayCnrs on 2005-07-16
[QUOTE=doclivingston]By default your home directory should be chmod'ed 711 (at least mine are), which means that other users can go through your home directory to get to other things (especially "public_html" is you have that set up for a web server), but they can't read files, or even see them.[/QUOTE]
 Yes that does make sense if you are running a web server. I am just running a regular desktop so I like to keep my own home directory under just my user name for privacy when other people are on my laptop.

---

