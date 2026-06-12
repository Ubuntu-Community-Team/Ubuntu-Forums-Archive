---
title: "Installation Question"
date: 2006-05-06
forum: Desktop Environments
---

### Post by dnalevelc on 2006-05-06
I am installing Ubuntu on a 2 gig HD.  I would like to skip Open Office and a few other items during the installation.  Is there a way I can do that?  I don't want to install as a server since I want the GUI to be on there.  I am gonna be learning this and I am gonna get my g/f to start using it too.  Please Help.

Thank You
DNA

---

### Post by matthewstory on 2006-05-06
In the installer there is a way to manually select packages for installation, what you might want to do is select all the things you want to install from the guided installation (like desktop environment, mail server etc) and then go to the manual package selection area and deselect the open office package.

---

### Post by aysiu on 2006-05-06
Do server install and then type ```
sudo apt-get update
sudo apt-get install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo /etc/init.d/gdm start
``` Then log in and fire up Synaptic and install only the packages you want.

A good way to approach this would be to mark *ubuntu-desktop* for installation, unmark the ones you **don't** want installed, and finally apply the changes.

In case you're not familiar with Synaptic:
[http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing.html#installing_with_synaptic)

---

### Post by dnalevelc on 2006-05-07
it is tellin me

"couldn't find package icewm"


am I doing something wrong?  I typed in what was typed in the post word for word a few times.  The first line worked perfect.  Now I am lost.

DNA

---

### Post by dnalevelc on 2006-05-07
Nevermind on that icewm comment.  I figured out how to do it.  I had to go into the source.list for where it was gonna look to find the updates.  I think it was the Universal Resource or something like that.  I am very very very new to linux.

I got the comp to load that up and then I got gnome on the comp.  Now my big thing is how do I get AIM and yahoo on it so I can chat while on the comp.  Also my g/f will be using this comp for e-mail and chat also.

I have the .deb files for yahoo and aim.  but from there I can't get them to do anything.  :-({|=   Any ideas will be helpful.

Thanks
DNA

---

### Post by Resurrection on 2006-05-07
Did you try installing the .deb packages by typing the following into the terminal:

sudo dpkg -i [name of package]

Just replace [name of package] with what you are trying to install.

---

### Post by aysiu on 2006-05-07
You don't need to download the .debs separately. Just type ```
sudo apt-get update
sudo apt-get install gaim
```

Read more here:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

