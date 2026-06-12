---
title: "I did something retarded - 0% opacity in compiz"
date: 2009-02-27
forum: Desktop Environments
---

### Post by Aped on 2009-02-27
Gah I'm a tard. Put a "!" in the box and hit OK... why is 0% the default anyway? Wacky business. Can't even change it now; anyone know where the config file is kept so I can go in commando line and fix it up? Alternately I guess I could try to uninstall it from said command(o) line...

OR, is there a cake way to change the opacity plugin's settings FROM commando line?

One thing's for sure, I'll be going commando for a while now, none of this window dressing stuff for me :(

---

### Post by WakkiTabakki on 2009-02-27
I'm not sure exactly where you made the change, but a start would be to check in the file:
~/.gconf/apps/compiz/general/screen0/options/%gconf.xml

From command line, you can edit it with:
```
gedit ~/.gconf/apps/compiz/general/screen0/options/%gconf.xml
```

/N

---

### Post by Aped on 2009-02-27
> **WakkiTabakki said:**
> I'm not sure exactly where you made the change, but a start would be to check in the file:
~/.gconf/apps/compiz/general/screen0/options/%gconf.xml

From command line, you can edit it with:
```
gedit ~/.gconf/apps/compiz/general/screen0/options/%gconf.xml
```

/N

Seriously, I did it from the compizconfig manager.


EDIT: That directory /.gconf doesn't exist. Also, I don't think a command-line version of gedit exists...

Anyway, even with vi or pico the file doesn't seem to be there. 

Going to bed now, it's late, hope to wake to sweet responses :D TY again smarty pantses of the ubuntu community.

---

