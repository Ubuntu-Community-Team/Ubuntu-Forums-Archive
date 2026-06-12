---
title: "Disable recent documents"
date: 2005-09-18
forum: Desktop Environments
---

### Post by larry_steiner on 2005-09-18
Hi Crew,
I searched all the keys and could not figure out how to turn off the recent document history.  Any ideas?

Thanks.
Larry

---

### Post by sizzam on 2005-10-21
chmod +400 .recently-used

to change it back so that it works again you switch to +600

chmod +600 .recently-used

---

### Post by hanspb on 2005-12-02
Hi, my permissions for .recently-used are 600. Any idea why it does not work?

Hans Petter

---

### Post by marcelloconti on 2006-05-12
Thanks, this sugestion is 100%.

I discover one crash when document posted in .recenty_used with character '&'.
gnome-panel restart in loop.

To solve, delete the .recently_used file in $home.

p.s.: it forgives my English, I live in Brazil and I do not dominate the language.

---

### Post by indian_gamer2003 on 2007-12-08
The chmod didnt work for me, try this instead

> rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel

---

### Post by mali2297 on 2007-12-08
This should work as well:
```

rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
chmod 400 ~/.recently-used.xbel

```
Note, no + in front of 400.

---

### Post by vt100 on 2007-12-17
You shouldn't have to do a hack like this. It should be a simple setting in the preferences. I thank the people who came up with the workaround, but it needs to be fixed at the source.

---

### Post by dapaintballer331 on 2008-03-09
> **mali2297 said:**
> This should work as well:
```

rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
chmod 400 ~/.recently-used.xbel

```
Note, no + in front of 400.

thanks a lot, worked perfectly.

---

### Post by bkraptor on 2008-04-04
This still doesn't work for me. Running Hardy Beta. After running the above commands, when the first document is opened the file permissions are changed back to 644.

---

### Post by mali2297 on 2008-04-04
> **bkraptor said:**
> This still doesn't work for me. Running Hardy Beta. After running the above commands, when the first document is opened the file permissions are changed back to 644.

Interesting, the gnome developers don't seem to like that we hack their system.

Try
```

rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
sudo chattr +i ~/.recently-used.xbel

```
The idea comes from this [post]("http://ubuntuforums.org/showthread.php?t=91154?post=#12"). The man page about chattr says
> 
A file with the &#8216;i&#8217; attribute cannot be modified: it cannot be deleted or renamed, no link can be created to this file and no data can be written to the file.  Only the superuser or a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

This has to work.

---

### Post by QCompson on 2008-04-12
Thanks mali2297, that seems to have worked.

I can't imagine why the gnome-developers think it is so incredibly important to have a list of recently accessed documents, especially given that so many people with wives and families would rather keep some of their computer *ahem* activities private.

---

### Post by analoog on 2008-04-17
```
mind@broom:~$ sudo chattr +i ~/.recently-used.xbel
[sudo] password for mind:
chattr: Inappropriate ioctl for device while reading flags on /home/mind/.recently-used.xbel

```
I got this error message, any idea's what iit means?
I did the exact commands as described in mali2297's last post.
```

rm ~/.recently-used.xbel
touch ~/.recently-used.xbel
sudo chattr +i ~/.recently-used.xbel
```

---

### Post by mali2297 on 2008-04-17
> **analoog said:**
> ```
mind@broom:~$ sudo chattr +i ~/.recently-used.xbel
[sudo] password for mind:
chattr: Inappropriate ioctl for device while reading flags on /home/mind/.recently-used.xbel

```
I got this error message, any idea's what iit means?


Check
```

lsattr ~/.recently-used.xbel

```
What does it say?

Which version of ubuntu do you use? (7.04,7.10 or 8.04) Do you use another filesystem than the default ext3?

---

### Post by analoog on 2008-04-17
I use 7.10 with ReiserFS.
2.6.24-11-generic kernel.

[quoye]
mind@broom:~$ lsattr ~/.recently-used.xbel
lsattr: Inappropriate ioctl for device While reading flags on /home/mind/.recently-used.xbel
[/quote]

---

### Post by mali2297 on 2008-04-18
> **analoog said:**
> I use 7.10 with **ReiserFS**.


That's probably the explanation. I think chattr is for ext2/ext3 only. I don't know if there's any similar tool for ReiserFS.

---

### Post by analoog on 2008-04-18
yeah it seems so, tried searching for a reiserFS tool but seems there isn't one. 
Maybe I should contact Gnome to make them aware of this issue and make option to disable the list. not sure how to that tho'.

thanks for your help Martin.

---

### Post by analoog on 2008-04-18
double :oops:

---

