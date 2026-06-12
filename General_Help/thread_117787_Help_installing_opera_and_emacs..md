---
title: "Help installing opera and emacs."
date: 2006-01-15
forum: General Help
---

### Post by Aybara on 2006-01-15
I'm fairly new to Ubuntu and have problems installing programs. I have used FC4 at work, and used yum there to install programs. If I understand correctly, apt-get is the yum of Ubuntu.

At first I tried:
apt-get install emacs
And got: 
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Then I read someplace that I should put sudo in front (still no idea why) and tried:
sudo apt-get install emacs
And got:
Reading package lists... Done
Building dependency tree... Done
Package emacs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs has no installation candidate

I don't think I really have understood the process of installing programs in Ubuntu, so I was hoping that someone could help me out.

---

### Post by Aybara on 2006-01-15
hmm. I think I made it work by typing:

sudo apt-get install emacs21

was it just the name I had wrong? is there an equivalent of yum-search?

and another q: I have to input my ubuntu cd every time I install a program. Is this the way it is supposed to work? 

and last but not least, are these questions I should ask in a beginners forum?

---

### Post by Adrian on 2006-01-15
[QUOTE=Aybara]was it just the name I had wrong? is there an equivalent of yum-search?[/QUOTE]

The easiest thing is to use a program called **synaptic** which is a graphical package manager. It's in the menu (System->Administration->Synaptic Package Manager). Of course you can run it from the terminal as well.

If you don't want to use the graphical tools, use **apt-cache** for searching.

(Edit: For example, **apt-cache search gstreamer** searches for gstreamer packages)

---

### Post by cotcot on 2006-01-15
emacs21 is accessible with synaptic (in terminal : sudo synaptic). If you do not see emacs21 in the list you have to check your repositories (/etc/apt/sources.list). This is well explained in [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) .

---

### Post by cotcot on 2006-01-17
In the title of your post there is also "opera".
It can be installed with synaptic, but there is somewhat more to do to get the plugins working. I have succesfully installed "opera 8.51" with plugins according to the description in [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by darth_vector on 2006-01-17
> **Aybara]Then I read someplace that I should put sudo in front (still no idea why)[/QUOTE]

you have to put sudo because you are carrying out an administrative task. you dont want any user to be able to install software said:**
> I don't think I really have understood the process of installing programs in Ubuntu, so I was hoping that someone could help me out.

to search for a program you go into the terminal and type

sudo apt-cache search programname

when you know the name of the package you wish to install, you install it with

sudo apt-get install programname

there is nothing to it mate :-)

EDIT: by the way, why on earch would you want to install emacs? you get vi by default on any installation ;-)

---

### Post by Gustav on 2006-01-17
[QUOTE=darth_vector]EDIT: by the way, why on earch would you want to install emacs? you get vi by default on any installation ;-)[/QUOTE]
Ignore the VIer!

Emacs rulez!

---

### Post by darth_vector on 2006-01-17
there is only one true editor! all the faithful visit the cult of vi: [http://www.splange.freeserve.co.uk/misc/vi.html](http://www.splange.freeserve.co.uk/misc/vi.html)


"Emacs is a hideous monstrosity, but a functional one. On the other hand, vi is a masterpiece of elegance. Sort of like a Swiss Army knife versus a rapier."

[IMG]http://www.splange.freeserve.co.uk/img/viman.gif[/IMG]

:D

---

