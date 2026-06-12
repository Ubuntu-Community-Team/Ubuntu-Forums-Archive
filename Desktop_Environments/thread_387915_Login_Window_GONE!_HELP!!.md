---
title: "Login Window GONE! HELP!!"
date: 2007-03-18
forum: Desktop Environments
---

### Post by Nectron on 2007-03-18
I'm having a problem logging in to my Ubuntu 6.06 Dapper..
I set a new login window (style) and when I wanted to test it out, I got locked out.

I get the error:
```

The theme does not contain definition for the username/password entry element
There was an error loading the theme, and the default theme ccould not be loaded. Attempting to start the standard greeter...

```

Now, I got shell access but don't know where to go from here..

Please help, I have assignments I need to hand in tomorrow saved inside..

Thanks..

---

### Post by brunomiguel on 2007-03-18
In the shell, login and type **startx**

---

### Post by Nectron on 2007-03-18
that only starts X..

I need to change the login theme through commands..

---

### Post by neo_reloaded on 2007-03-18
Now, this is kind of a gamble.

You have to edit your
/etc/gdm/gdm.conf-custom file

and change entry under [greeter] section. Pick up a friendly working greeter theme from. Or if you completely remove the section, it should use default greeter.

/usr/share/gdm/themes 

Rock on..

---

### Post by Nectron on 2007-03-19
> **neo_reloaded said:**
> Now, this is kind of a gamble.

You have to edit your
/etc/gdm/gdm.conf-custom file

and change entry under [greeter] section. Pick up a friendly working greeter theme from. Or if you completely remove the section, it should use default greeter.

/usr/share/gdm/themes 

Rock on..

My friend tells ya: Enta Fannaan = You're an artist.. in Arabic :D

---

