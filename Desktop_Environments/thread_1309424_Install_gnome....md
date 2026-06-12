---
title: "Install gnome...?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by gypsumwolf on 2009-11-01
I have ubuntu installed and then I installed xubuntu-desktop and removed ubuntu-desktop. Everything works fine.

I want to add gnome as a session option but I don't want to install everything that comes with ubuntu-desktop (like evolution, gnome-games...). Should I just do "apt-get install gnome"?

---

### Post by Turtle.net on 2009-11-01
If you just remove the ubuntu-desktop package you should have a gnome session available. This package is a meta package (empty, just the needed dependencies).If you select it in synaptic it will give you all the dependencies.
If you do not have the gnome session available when you log in (in the bottom bar when you entered you login and the system is waiting for your password), then launch synaptic and select ubuntu-desktop. Accept all the suggestions.
Then in synaptic go to Marked Changes.
Unmark unbuntu-desktop, and then unmark all the packages you don  want (like evolution for instance).
Then apply the changes.
You can after that either use the Computer janitor or ```
sudo apt-get autoremove
``` to make sure that you removed all the unrequired dependencies.
Then log out and you should be able to select Gnome during your next login.

---

### Post by gypsumwolf on 2009-11-01
Thanks for the nice clear response. I will try that.

---

### Post by Turtle.net on 2009-11-01
Make sure to post the result and to close your thread if it is.

---

### Post by gypsumwolf on 2009-11-02
It was just fine, GNOME was still installed.

How do you close a thread? Mark it as solved? I did that.

---

