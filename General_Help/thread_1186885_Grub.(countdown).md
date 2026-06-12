---
title: "Grub.(countdown)"
date: 2009-06-13
forum: General Help
---

### Post by Im A Ninja on 2009-06-13
This isn't really about Ubuntu... 

When i boot my computer, i don't want grub to have the countdown where it automaticly chooses the Operating system that is highlighted.

I want it to have no countdown and wait for me to choose.

how do i do this?

EDIT: or i could someone tell me how to make the countdown much longer?

---

### Post by synapsys on 2009-06-14
Edit your menu.lst.

```
sudo gedit /boot/grub/menu.lst
```

comment out the line that says hiddenmenu.
old        hiddenmenu
new     #hiddenmenu

You can also change the timeout for default os boot.

---

### Post by Chemical Imbalance on 2009-06-14
A nice GUI that accomplishes this is startup-manager.

```
sudo aptitude install startupmanager
```

Appears under System, Administration after install.

---

### Post by Im A Ninja on 2009-06-14
> **synapsys said:**
> Edit your menu.lst.

```
sudo gedit /boot/grub/menu.lst
```comment out the line that says hiddenmenu.
old        hiddenmenu
new     #hiddenmenu

You can also change the timeout for default os boot.
I don't know how to do that... this is my first time installing Ubuntu.

---

### Post by Chemical Imbalance on 2009-06-14
Just open up Terminal under Accessories and paste the code in.

Enter your user password when it asks you and wait for it to finish installing.


Alternately you can open up Synaptic Package Manager under System, Administration and search for startup-manager and install it that way.

---

### Post by Im A Ninja on 2009-06-14
> **Chemical Imbalance said:**
> A nice GUI that accomplishes this is startup-manager.

```
sudo aptitude install startup-manager
```Appears under System, Administration after install.

I don't know what that is and I just want to make the Grub have no count down or a much longer one.

---

### Post by Chemical Imbalance on 2009-06-14
Please see my post above.

---

### Post by synapsys on 2009-06-14
Ok go to Applications menu on top.
Choose Applications >> Accessories >> Terminal
A box opens up with a command prompt.
Type in:
```
sudo gedit /boot/grub/menu.lst
```

This will open your text editor with the menu.lst file.

Scroll down about 20 lines to a block that reads:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

See the '#' in front of hiddenmenu?
If that is not there, then put it there and hit save.

You can also edit this section to increase or decrease the timeout:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

---

### Post by Im A Ninja on 2009-06-14
OK,  I changed it from 60 seconds to 600 seconds. :)

---

### Post by jenkinbr on 2009-06-14
That'll give you 10 minutes before it makes a choice for you.

Are you sure that's what you want to do?

edit: nevermind, you want it to not count down, or to extend the timing.

---

### Post by raymondh on 2009-06-14
Hello Im a Ninja,

Congratulations on editing the menu.lst. and getting what you wanted accomplished.

As a side note, what chemical imbalance (and others) was saying is that it could also be accomplished by start-up manager ... which also gives you a graphical interface.  If you want to experiment some more ... (only if) and I include this post *just in case you decide to change the timing again* and prefer not to edit the menu.lst

1.  Go to system > administration > synaptic package manager
2.  You will be asked for your log-in password
3.  When synaptic comes alive (pop-up), type in START UP MANGER in the search box.
4.  Tick/check the box for start-up manager
5.  Click apply and wait for the operation to finish
6.  Exit/close synaptic
7.  Go to system > admistration > start-up manager and edit away to your liking.

It looks like this (see screenshot)

Another alternative is to open a terminal (applications > accessories) and type

```
sudo apt-get install startupmanager
```

Of course, you will be required to also type in your password (which you will not see as you type).  Let it finish and exit/close.

Again, those above-mentioned are only learning "adventures" that you may try.  Most important is you were able to fix your issue =D>

Happy Ubuntu-ing

---

### Post by Chemical Imbalance on 2009-06-14
Just clarification:

To correct my earlier post and your's the code is:

```
sudo aptitude install startupmanager
```

Instead of startup-manager, its startupmanager.

My mistake earlier.

---

### Post by clydeseal on 2010-08-25
> **synapsys said:**
> Edit your menu.lst.

```
sudo gedit /boot/grub/menu.lst
```comment out the line that says hiddenmenu.
old        hiddenmenu
new     #hiddenmenu

You can also change the timeout for default os boot.

I went to terminal and typed in that command but it only opened a blank notepad. Did this change with the 10.4 LTS upgrade?

---

### Post by Quackers on 2010-08-25
I believe that the earlier instructions were written when grub is used. If you are running Lucid Lynx you will be using grub2, which does not use the menu.lst
What you need to do is change the default timeout to one of your choice (or to -1 if you want it to wait until you choose a system to boot). I've changed mine to -1 but I can't remember how I did it. I'll have a look and get back to you - unless somebody else can tell you first.

---

### Post by Quackers on 2010-08-25
From memory I started up a terminal and entered   sudo gedit /etc/default/grub   then entered my password. A new window opens up with your current grub file. Edit the GRUB TIMEOUT entry to what you want ( NOT GRUB HIDDEN TIMEOUT) then under File choose save then under File choose close.
Then run  sudo update-grub

I think that's right. Maybe somebody else could confirm/correct that?

---

