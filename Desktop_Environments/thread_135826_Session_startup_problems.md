---
title: "Session startup problems"
date: 2006-02-24
forum: Desktop Environments
---

### Post by c77m on 2006-02-24
I've recently converted a couple of machines to Ubuntu Breezy (primarily for MythTV), and I'm having some problems with executing commands on startup.  Particularly, within the GUI I have entered commands in System -> Preferences -> Session -> Startup Programs.  After logging in, it takes 5-10 minutes before these programs are run.  Where can I find out what the heck is going on, and why the heck would it take so long to start running startup scripts?

My second problem is that I've made changes to both /etc/profile and ~/.bash_profile -- neither of these files seem to be sourced when logging in either through ssh or locally in X.  Something as basic as this makes me think something simple is missing, but I don't know what.

Any help is appreciated on these two items.

---

### Post by Stormy Eyes on 2006-02-24
You might want to add the following to .bashrc:

```
source /etc/profile
source /home/$userid/.bash_profile
```

Also, I find that GNOME's "start-up programs" handling sucks. I prefer to do it [the OLD SCHOOL way.](https://wiki.ubuntu.com/CustomXSession) (It's a good howto; I wrote it myself. :evil:)

---

### Post by c77m on 2006-02-24
Thanks much for the link -- I will do it using ~/.xinitrc.  Wish I could figure out what the huge delay is still, but I won't care anymore once it's just working...

---

