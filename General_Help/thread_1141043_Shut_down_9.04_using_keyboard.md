---
title: "Shut down 9.04 using keyboard"
date: 2009-04-28
forum: General Help
---

### Post by triplemaya on 2009-04-28
Hi. How do I shut down the computer using keyboard in 9.04?

---

### Post by nothingspecial on 2009-04-28
If you mean from the terminal```


sudo shutdown -h now
```

---

### Post by alfkh on 2009-04-28
without the terminal interface, i would say ctrl-alt-del. Default is shutdown, there are restart & couple more option depending where your mouse is at that time. if it's not directly over shutdown, do an arrow up (since shutdown is right on top) until shutdown is hi-lighted. Enter!

alf(kh)

---

### Post by nothingspecial on 2009-04-28
Pressing Alt with F1 will launch your main menu which you can navigate using the arrow keys and select shutdown with enter.

---

### Post by triplemaya on 2009-04-28
Many thanks all for your quick responses.

The ctrl-alt-del solution is exactly what I wanted. Plus this is a HUGE improvement on previous releases, ctrl-alt-del and then enter and I'm all done. Lovin it.

The main menu thing doesn't work anymore, not on my install anyway, I just circulate between the Applications Places and System menus, it doesn't get over to the shutdown menu, hence the question.

Up until jaunty I've just done the main menu thing, which is a lot quicker than getting a terminal and typing in the command.

Trying to make it easier and quicker I made myself a main menu entry some time ago to shutdown with the line 
sudo /sbin/shutdown -h now
but it doesn't work.

---

### Post by StuartN on 2009-04-28
> **triplemaya said:**
> Trying to make it easier and quicker I made myself a main menu entry some time ago to shutdown with the line 
sudo /sbin/shutdown -h now
but it doesn't work.

If you want it to work as it did before, then add this to your main menu to restore the old dialog:

```
gnome-session-save --shutdown-dialog
```

---

### Post by triplemaya on 2009-04-28
That's really quick and neat, and familiar! Thanks. [can't help wondering how you get to know all this stuff - dazzled smiley!]

BTW, is there a simple way to make the 
sudo /sbin/shutdown -h now
command work as an item in the main menu?

---

### Post by StuartN on 2009-04-28
> **triplemaya said:**
> BTW, is there a simple way to make the 
sudo /sbin/shutdown -h now
command work as an item in the main menu?

sudo fails in the menu because there is no dialog to accept your password. If you replace sudo with the graphical gksudo then your command should run, but of course you would then need to type in your password to shut down.

---

### Post by triplemaya on 2009-04-29
Thanks Stuart

I found this thread

[http://ubuntuforums.org/showthread.php?t=219618](http://ubuntuforums.org/showthread.php?t=219618)

and followed the instructions, so I now have a script that executes a shutdown without typing in the password ... but it still won't work as a menu item!? I've given the full path of the script in the main menu tool, but nothing happens.

---

### Post by El Zoido on 2009-04-29
You could also use Gnome-Do, which is a very nice utility anyway

---

### Post by theozzlives on 2009-04-29
> **triplemaya said:**
> That's really quick and neat, and familiar! Thanks. [can't help wondering how you get to know all this stuff - dazzled smiley!]

BTW, is there a simple way to make the 
sudo /sbin/shutdown -h now
command work as an item in the main menu?

Trial and error.

---

### Post by triplemaya on 2009-04-30
Gnome-Do is very nice, and I'm sure it will come in handy, thanks, but selecting it on the main menu, then typing is less straightforward than simply selecting a shutdown item on the menu, which is what I'm really after.

---

### Post by triplemaya on 2009-04-30
theozzlives, could you make a suggestion of the kind of thing to try, I have no idea where to start. Presumably the main menu items are run as me as a user, but on another issue someone pointed out that tsink needs to be run as a user in the group lp so running it from the main menu works, but I have no concept of why. What's special about running a program in this way?

---

### Post by kpkeerthi on 2009-04-30
> **triplemaya said:**
> Gnome-Do is very nice, and I'm sure it will come in handy, thanks, but selecting it on the main menu, then typing is less straightforward than simply selecting a shutdown item on the menu, which is what I'm really after.
It is not required to select gnome-do from menu. By default, it is mapped to [super] + [space].

---

### Post by triplemaya on 2009-04-30
Thanks kpkeerthi, still have to type! I use super for main menu so all my most used operations are super, up arrow x times, enter.

---

### Post by triplemaya on 2009-04-30
I forgot to mention I've got a simple shutdown script to run without needing a password by editing /etc/sudoers:

username ALL= NOPASSWD: /home/startupscipt

which works perfectly with no intervention *except* as a main menu item!

---

### Post by triplemaya on 2009-04-30
Solved, but I'm not sure why! I tried out the menu item one more time, and now it works. I'm now on the new install so that could be the reason.

---

### Post by triplemaya on 2009-04-30
Hmm, now it doesn't work again!?

---

