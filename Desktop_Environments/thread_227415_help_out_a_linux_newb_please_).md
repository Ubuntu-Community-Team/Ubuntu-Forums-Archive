---
title: "help out a linux newb please :)"
date: 2006-08-01
forum: Desktop Environments
---

### Post by _DjScrew_ on 2006-08-01
well i installed breezy and it was up and running fine, but i wanted to upgrade to dapper. conviently, i seen the upgrade box at the top of the 'update manager' i let it do it's thing and then after i restarted i couldn't login. it takes my username and pass and then goes to a black screen, the back to a purple screen and then the login dialog re-appears.. any ideas, i'm stumped

thanks,
mike

EDIT: sorry about putting it in the wrong section, mods. I don't want to double post, move it if neccessary :) thanks

---

### Post by pdc303 on 2006-08-01
Sounds like a problem initializing your window manager (I presume gnome).

You should look at the gdm logs:-

```
cat /var/log/gdm/:0.log | tail
```
```
nano /var/log/gdm/:0.log
```

See if you see any errors.

/var/log/Xorg.0.log may be worth a look as well.

---

### Post by neoeden on 2006-08-01
One thing to note is that to get a prompt to type those commands, hit ctrl+alt+F1 to head to the console. ctrl+alt+F7 brings you back to your window manager.

---

### Post by Kanja on 2006-08-01
I'm getting the same problem - except when I specify GNOME as my windowing system I get an error message that says "GDM could not write to your authorization file"

---

### Post by _DjScrew_ on 2006-08-02
cool i'll give that a shot and let you guys know what I come up with, thanks.

---

### Post by Ramses de Norre on 2006-08-02
> **Kanja said:**
> I'm getting the same problem - except when I specify GNOME as my windowing system I get an error message that says "GDM could not write to your authorization file"

```
sudo chown `whoami` ~/*authority && chmod 600 ~/*authority
```

---

