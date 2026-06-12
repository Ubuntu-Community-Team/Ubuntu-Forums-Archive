---
title: "Reset Desktop"
date: 2011-03-07
forum: Desktop Environments
---

### Post by blenderfox on 2011-03-07
I've messed up my desktop, and want to reset it back to the state it was when I installed Ubuntu originally. Is this possible?

---

### Post by Veovis Muad'dib on 2011-03-07
You could create a new user, move all your files to the right home folder, chown them to the new user, and then delete the old one.  But that seems like a lot of steps, so we'll see if anyone else can suggest something quicker.

---

### Post by wojox on 2011-03-07
Define "messed up".

---

### Post by Frogs Hair on 2011-03-07
Hi
Could you please  give some more information  about what is messed up. You could start by selecting the ambiance theme in appearance preferences.

---

### Post by blenderfox on 2011-03-07
Well, I'm not sure what I've done, but I'm now back at a command line prompt each time I bootup. I login as normal, and get a command prompt with my name and hostname. Nothing else.

God, I feel stupid. >_<

---

### Post by Johnce on 2011-03-07
If you choose to reset back to default desktop (assuming you use gnome), type in terminal.

```
[I]rm -rf .gnome .gnome2 .gconf .gconfd .metacity
[/I]
```

---

### Post by wojox on 2011-03-07
When you log in at the command line does **startx** do anything or throw any errors?

---

### Post by blenderfox on 2011-03-07
> **Johnce said:**
> If you choose to reset back to default desktop (assuming you use gnome), type in terminal.

```
[I]rm -rf .gnome .gnome2 .gconf .gconfd .metacity
[/I]
```

I'll give that a try once my laptop finishes backing up.

wojox, I'll try startx if Johnce's method doesn't work. Thanks :)

---

### Post by robro on 2011-03-07
i would try startx first because if it works you dont have to delete your desktop configuration files :)

---

### Post by Johnce on 2011-03-07
that's right," startx" first. deleting config files (the code i posted) should be the last fix.

Gl!

---

### Post by blenderfox on 2011-03-08
Thanks for all the advise. startx worked perfectly :)

---

### Post by JuR-97 on 2011-06-15
> **momokoyukino said:**
> Thanks for all the advise. startx worked perfectly :)

"Command not authorized"  ?????? I thought terminal has root access > can edit anything!! And i haven't changed the sudoers file

Can some1 help me, please?

---

### Post by blenderfox on 2011-06-16
> **JuR-97 said:**
> "Command not authorized"  ?????? I thought terminal has root access > can edit anything!! And i haven't changed the sudoers file

Can some1 help me, please?

Terminal doesn't have root access, it's the user that has the root access. Try doing

```
sudo startx
```

---

### Post by dhinteractive on 2011-06-16
thanks for this information sharing

---

### Post by Elline on 2011-06-16
Haven't you choosed "xterm" in session by accident?

---

