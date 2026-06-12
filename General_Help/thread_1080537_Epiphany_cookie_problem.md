---
title: "Epiphany cookie problem"
date: 2009-02-25
forum: General Help
---

### Post by dbbolton on 2009-02-25
Not sure if this is a bug, but every time I close Epiphany, all of my saved passwords and whatnot disappear. I have noticed this with several sites (Gmail, Debian forums, Ubuntu forums). In Preferences > Privacy > Cookies, I have enabled "Always Accept".

Any suggestions?

---

### Post by fragos on 2009-02-25
> **dbbolton said:**
> Not sure if this is a bug, but every time I close Epiphany, all of my saved passwords and whatnot disappear. I have noticed this with several sites (Gmail, Debian forums, Ubuntu forums). In Preferences > Privacy > Cookies, I have enabled "Always Accept".

Any suggestions?

There is a remember passwords check box in the Privacy tab. Mine is checked as is "Accept only from sites you visit" and all works for me. Note that "Accept All" will accept cookies from advertisers on pages you visit.

---

### Post by dbbolton on 2009-02-25
> **fragos said:**
> There is a remember passwords check box in the Privacy tab. Mine is checked as is "Accept only from sites you visit" and all works for me. Note that "Accept All" will accept cookies from advertisers on pages you visit.
It was originally set to "Only from sites you visit" but after I noticed this problem, I changed it to "Always" to see if it would fix the issue. 

I just checked my taskmanager and noticed that Epiphany was still running even after I closed it. I killed the process, and now everything seems to be working normally.

---

### Post by fragos on 2009-02-25
That explains things. I'm curious how more that one instance of Epiphany was running. Certainly not how it was designed.

---

### Post by dbbolton on 2009-02-25
I wonder if it could have to do with this:

```

(xfdesktop:2724): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

```

xfdesktop crashed while epiphany was running. It took me back to GDM, I logged in, an then this business started

---

### Post by fragos on 2009-02-25
I'm a Gnome desktop user. Perhaps running aps from more than one desktop environment could provide opportunities for less graceful terminations.

---

