---
title: "changing root password - Ubuntu"
date: 2007-12-09
forum: Dell  Ubuntu Support
---

### Post by LesFromWaldenVT on 2007-12-09
Wow! Just read that you cannot become 'root' on Ubuntu. So long Ubuntu -hello Fedora Core. What a piece of junk. What is this - software  for babies? Give me a break.

sudo doesn't always work. For example, if I want to edit a 'root' owned file, 'sudo emacs <file>' doesn't work.

It's a pain to have to use 'sudo' all the time.

Oh well, it was fun while it lasted. Fedora here I come!

---

### Post by yota on 2007-12-09
have you tried 'sudo -s' or 'sudo su' or even 'sudo passwd'?

this kind of problem has been discussed countless times, and is well treated at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

please do a bit of searching before posting.

Hope this helps!

---

### Post by Steveway on 2007-12-09
Well here sudo nano /path/to/file works.
Also does gksudo gedit /path/to/file .
You seem to do something wrong or you are just a troll.

---

### Post by LesFromWaldenVT on 2007-12-09
I was going by what other posters had said about getting into 'root'. I am well-aware of the dangers of being 'root' but at work, I tend to be 'root' all day long (in Fedora Core) and so far have managed not to delete the contents of my drive.

---

### Post by LesFromWaldenVT on 2007-12-09
I apologize for the 'babies' remark. I'm just frustrated that i've had this system for months and still can't get around the video driver crash problem I'm having.

---

### Post by pebo on 2007-12-09
It's not that difficult to enable the root account if you really can't be without it ;)

---

### Post by gbrainin on 2007-12-09
From [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"):

If you want a root shell, the command is:
```
sudo -i
```
For a root shell with the current user's environment (as opposed to root's):
```
sudo -s
```

Both of these are non-recommended, and should include the standard disclaimer that nobody will help you when you accidentally honk up your system after using them.

---

### Post by mudguts on 2007-12-09
what system are you running and what video card does it have?

---

### Post by aysiu on 2007-12-09
> **LesFromWaldenVT said:**
> I apologize for the 'babies' remark. I'm just frustrated that i've had this system for months and still can't get around the video driver crash problem I'm having.
Since you've apologized for the "babies" remark, I've taken it out of the subject heading.

---

