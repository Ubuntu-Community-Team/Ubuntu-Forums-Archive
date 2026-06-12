---
title: "psychocats method of kde install no longer working [Resolved]"
date: 2007-03-07
forum: Desktop Environments
---

### Post by dr johnson on 2007-03-07
[COLOR="Navy"]**EDIT: **[/COLOR]
comments #6 & 7 contain the answer to the problem.
[COLOR="Navy"]**END EDIT.**[/COLOR]



please see **[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)**

It gets a short way into the installation process, and invites you to hit an "OK" in the terminal display. Trouble is, the "OK" thingy (button? icon?) isn't active. I got kde installed onto ubuntu using their method a few months ago and it worked fine then. Is this worth bothering with, or are people now advised to use system>administration>synaptic package manager ?

---

### Post by zvacet on 2007-03-07
Why don´t you try to install it from alternate CD if you have one?

---

### Post by dr johnson on 2007-03-07
Because I understand that installing Kubuntu from the disc when you've already got Ubuntu is not cool for some reason (an inefficient use of the harddrive, maybe?). It does seem better to install one on top of the other, rather than keeping them entirely seperate.

---

### Post by rsambuca on 2007-03-07
Are you sure you are following the directions correctly?  It should still work.

Just enter these commands in a terminal```
sudo aptitude update
```
```
sudo aptitude install kubuntu-desktop
```

---

### Post by dr johnson on 2007-03-07
Yup, that's exactly right, and I did it several times too. There were two grey coloured screens that came up in succession in the terminal asking for a response. One of them--the second, I think--was asking me if I wanted kde or gnome as a default. This screen and the other screen that contained an option were easy enough to deal with. But when the third came up, the "OK" button was dead, and so the process just sat there without any apparent progress.

---

### Post by rsambuca on 2007-03-07
Sorry, but what do you mean the OK button was dead?  Did you use the arrow keys to select OK?, and what is the final message that isn't working?

---

### Post by dr johnson on 2007-03-07
rsambuca,
Wow thanks, I never thought to hit the (direction-right) arrow key! Command line n00b, I'm afraid. Thanks for the help.

---

### Post by rsambuca on 2007-03-07
Good stuff!!  Maybe you can edit your first post and mark the thread title as {Resolved}

---

### Post by dr johnson on 2007-03-07
done. that ok?

---

