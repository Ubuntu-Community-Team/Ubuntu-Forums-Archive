---
title: "remove username from indicator-sessions"
date: 2011-10-30
forum: Desktop Environments
---

### Post by zenkaon on 2011-10-30
Hello,

How do I remove my name from the top right of the screen in 11.10? I know what my name is and don't really need reminding.

I would also like to remove the option of switching users. I'm setting up a living room PC and want everything to run from the living room user account. No switching to guest session or switching to other users. Logging in as other users is reserved for people who know how ssh works.  

I've trying apt-get remove indicator-session, but that removes the shutdown menu as well.

Any hints would be great

---

### Post by Frogs Hair on 2011-10-30
On 11.04  it was possible to remove indicator-me without affecting the rest of the menu . As far as I know the name is tied together with indicator-session . I have looked through synaptic a number of times and found no separate package as in previous releases . :popcorn:

---

### Post by aeronutt on 2011-10-30
fpmurphy had an extenion that did this, but seems it'll be a week or so until his extensions get updated to gnome-shell 3.2

[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by lswb on 2011-10-30
What's your problem? The developers said you should have your name in the corner, and by gosh, you will. It's the height of arrogance to think that you know what you need more than they do.  :)

---

### Post by Frogs Hair on 2011-10-30
It's nice to know who is logged in , but as a single user a different name in the corner would indicate a haunting . :P

---

### Post by Steeperton on 2011-10-30
install dconf-tools, then run dconf-editor.... look under apps > indicator-session.

there you have the ability to turn off the name, and a number of other options....

---

### Post by zenkaon on 2011-10-30
perfect, dconf-editor solves the problem.

---

