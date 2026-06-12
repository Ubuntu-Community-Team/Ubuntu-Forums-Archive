---
title: "How do I get rid of the gnome panel without uninstalling it"
date: 2009-03-08
forum: General Help
---

### Post by beattyml1 on 2009-03-08
I recently switched from using the gnome panel to using the xfce panel and I was wondering how I would go about keeping it from starting up with ubuntu, I can't find it in the sessions thing

It's also really frustrating because I keep saying killall gnome-panel and as soon as I close the terminal window the panel comes back, goodness I haven't had my computer disrespect me like this since the last time I used windows

---

### Post by DeMus on 2009-03-08
> **beattyml1 said:**
> I recently switched from using the gnome panel to using the xfce panel and I was wondering how I would go about keeping it from starting up with ubuntu, I can't find it in the sessions thing

It's also really frustrating because I keep saying killall gnome-panel and as soon as I close the terminal window the panel comes back, goodness I haven't had my computer disrespect me like this since the last time I used windows

You could of course remove the panel this way:
right click it and select: Delete this panel.

---

### Post by cb951303 on 2009-03-08
sometimes people think of the more complicated solution before the simple one. like in your case you try to kill gnome-panel every time instead you can just right-click and delete it for good :D

edit: why my smiles doesn't work ?!

---

### Post by theozzlives on 2009-03-08
```
sudo apt-get remove ubuntu-desktop
```

---

### Post by redseventyseven on 2009-03-08
> **DeMus said:**
> You could of course remove the panel this way:
right click it and select: Delete this panel.

That doesn't work for all panels - it won't let you delete the last one.

The reason that gnome-panel comes back is because that's how the process is set up when you start your computer. 

Go to the Session Manager (I can't remember where it is in the Ubuntu menus as I no longer use Ubuntu) and go to the "Current Session" tab. Each process that is running in the current session has a Style associated with it - some process are set up to restart when they're killed. Gnome-panel is one of these. You can change the style of the process here so that it doesn't restart when you kill it.

---

### Post by sdennie on 2009-03-08
I was trying to look for a more elegant solution but, a brute force method is just to make gnome-panel -x:

```

sudo chmod -x /usr/bin/gnome-panel

```

Logout and log back in and it will not start.

Edit:
I meant -x...

---

### Post by beattyml1 on 2009-03-08
Thanks for the help everyone, I might end up using the chmod option but would like to know before I do so how I would undo it later if I change my mind, also I would ideally like to have a solution that only works for one user so that I can have the gnome panel for guests that aren't used to my ultra custom setup, so if anyone can think of a solution that could do this that would greatly appreciated.

---

### Post by sdennie on 2009-03-08
To undo the chmod option:

```

sudo chmod +x /usr/bin/gnome-panel

```

To make it a user specific option using the same sort of method:

```

cd
mkdir -p bin
touch bin/gnome-panel
chmod +x !$

```

Logout and log back in.

---

### Post by beattyml1 on 2009-03-08
Thanks for the help, I really appreciate it but would mind for the sake of helping me learn more about the OS what these commands are doing.  :)

---

### Post by sdennie on 2009-03-08
Absolutely:

```

cd                       # Change to your home directory
mkdir -p bin             # Make a bin directory.  Don't care if it doesn't exist
touch bin/gnome-panel    # Create an empty file named bin/gnome-panel
chmod +x !$              # !$ means "last thing on the last command line".  Make that executable.

```

The reason this works is because if ~/bin exists, it's made the first thing in your path.  You create a dummy "executable" that essentially masks the real gnome-panel and so /usr/bin/gnome-panel never actually loads.  To reverse the change it's simply:

```

rm bin/gnome-panel

```

No sudo or anything.  It's just a local "setting".

---

### Post by beattyml1 on 2009-03-08
Thanks for the help, if they still had the features I would now mark this as solved and thank you but they took those away :(

---

### Post by D1ZZ4ZZT3R on 2009-03-22
> **sdennie said:**
> I was trying to look for a more elegant solution but, a brute force method is just to make gnome-panel -x:

```

sudo chmod -x /usr/bin/gnome-panel

```


holy god! thank you. i've been searching for about an hour for that solution (not knowing what solution awaited me). i just started using gnome do today and i wanted to get rid of both panels and, thanks to you, i did! now i have a desktop that's about as minimalistic as they get.

---

