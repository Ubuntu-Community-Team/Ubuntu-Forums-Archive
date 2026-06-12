---
title: "gksudo nautilus problem"
date: 2009-06-10
forum: General Help
---

### Post by Jcdlvsrbld on 2009-06-10
when i run the command gksudo nautilus i get this error:

  (gksudo:6629): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
**Eel:ERROR:eel-preferences.c:107: preferences_gconf_value_get_bool: assertion failed: (value->type == GCONF_VALUE_BOOL)

anyone know how i can rectify the situation? 
thanks in advance!!

(btw, im using jaunty 32 bit)

---

### Post by Chrus on 2009-06-10
try this

```
gksu "nautilus --no-desktop"
```

---

### Post by Jcdlvsrbld on 2009-06-10
> **Chrus said:**
> try this

```
gksu "nautilus --no-desktop"
```

thanks, this worked, but i got several warnings/errors before it opened as root

---

### Post by Chrus on 2009-06-10
What errors/warnings did you get?

---

### Post by Jcdlvsrbld on 2009-06-10
(gksu:4027): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

** (nautilus:4028): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root/Desktop
--> trash:///
--> file:///
--> file:///root

(nautilus:4028): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 4 elements at quit time (keys above)

(nautilus:4028): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time

---

### Post by michy99 on 2009-06-10
I always get those warnings when running nautilus as root, but they don't seem to affect anything.

---

### Post by doas777 on 2009-06-10
ok, basically what is happening here, is that nautilus is looking for settings associated with the user account under which it runs; usually your user desktop. 

when you run an app as gksu or sudo however, the user is no longer you; but root. since the root desktop has never been logged into, and has no themes or usershare info available, you recieve this message when ever nautilus looks for the theme to apply.

I've never noticed it being harmful. nautilus just loads with a default theme instead of the one my desktop is configured to use. no biggie. 
 
are these errors causing you problems using nautilus?

---

### Post by Jcdlvsrbld on 2009-06-10
> **doas777 said:**
> ok, basically what is happening here, is that nautilus is looking for settings associated with the user account under which it runs; usually your user desktop. 

when you run an app as gksu or sudo however, the user is no longer you; but root. since the root desktop has never been logged into, and has no themes or usershare info available, you recieve this message when ever nautilus looks for the theme to apply.

I've never noticed it being harmful. nautilus just loads with a default theme instead of the one my desktop is configured to use. no biggie. 
 
are these errors causing you problems using nautilus?


no, not really, thanks

---

