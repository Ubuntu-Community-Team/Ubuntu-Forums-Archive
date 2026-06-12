---
title: "How to remap/change keyboard keys ?"
date: 2009-04-10
forum: General Help
---

### Post by rams123 on 2009-04-10
Hello everyone,

Could anyone please tell me how to easily change/remap keyboard keys? In windows I use *SharpKeys*.

---

### Post by _Purple_ on 2009-04-10
You can use the method given in [this post](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=590326&postcount=2).

---

### Post by rams123 on 2009-04-10
> **_Purple_ said:**
> You can use the method given in [this post](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=590326&postcount=2).

Sorry, I've not understood anything there.. :(

How to run ** xev** ?

---

### Post by ytsejam1138 on 2009-04-10
Try this:

Install a program called XKeyCaps (it's available in the Ubuntu universe repos). In terminal:

```
sudo apt-get install XKeyCaps
```


When you run the program, it will give you a GUI of the keyboard which will allow for easier remapping of the keys. Then you click on write output and make sure you add

```
xmodmap ~/.xmodmap-`uname-n`
```

to your sessions so it autostarts each time you boot up and your good to go.

---

### Post by _Purple_ on 2009-04-10
> **rams123 said:**
> Sorry, I've not understood anything there.. :(

How to run ** xev** ?

You can run it by typing it in the terminal. 
Go to Applications > Accessories > Terminal. Then type
```
xev
```

Once you get the keycode from there, type the second command in terminal according to your keycode. To do it automatically, add this command in the "startup session commands" or in your .bashrc.

---

