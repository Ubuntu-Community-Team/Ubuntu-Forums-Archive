---
title: "Problem on login"
date: 2009-04-28
forum: General Help
---

### Post by FFGANDALF on 2009-04-28
Hey I tried to restore to a backup that I had on another partition. After copying all the files I get two problems. Instead of saying FFGANDALF@FFGANDALF-laptop it says localuser.localdomain. It is interesting to note that all ttys above ttt2 say FFGANDALF@FFGANDALF-laptop. The second problem is that when I try to sign into gnome I get the following error message:
         GDM could not write to your Authorization file. This could mean that you are out of disk space or your home directory could not be opened for witting.
this was followed by . to contact my sys admin

---

### Post by taurus on 2009-04-28
Look in /etc/hostname & /etc/hosts regarding the name of your machine.

Did you use the same username on your machine?  Otherwise, the backup version would belong to another user.

```
id
ls -la ~
```

---

### Post by FFGANDALF on 2009-04-28
okay, in the /etc/hosts file the entry the top line says:
            127.0.0.1	localhost.localdomain	localhost
now I tried to just delete this but when I rebooted it added it again. any ideas why?

---

### Post by taurus on 2009-04-28
> **FFGANDALF said:**
> okay, in the /etc/hosts file the entry the top line says:
            **[COLOR="Blue"]127.0.0.1	localhost.localdomain[/COLOR]**	localhost
now I tried to just delete this but when I rebooted it added it again. any ideas why?

You definitely need the entry in blue in /etc/hosts or things won't work.  However, you can add another line to /etc/hosts to something like

```
127.0.1.1   FFGANDALF-laptop
```

Make sure the name you use is the same one that you have in /etc/hostname or you won't be able to use sudo anymore.

Therefore, you need to edit both files at the same time.

```
gksudo gedit /etc/hostname /etc/hosts
```

---

### Post by FFGANDALF on 2009-04-28
thanks, however that doesn't help my second and more important problem, namely that whenever I log in I get an error message from gnome

---

