---
title: "Pidgin closes immediately"
date: 2009-05-08
forum: General Help
---

### Post by jjblackfox on 2009-05-08
Every time I click pidgin, it closes immediately after I open it. It makes a little space in the top panel, but then disappears. I ran pidgin in the terminal, and I get is an error that says "Segmentation fault"

I don't remember how I installed pidgin, I think it was through the add/remove programs. I am using ubuntu 9.04.

---

### Post by _Purple_ on 2009-05-08
Which version of pidgin are you using?

---

### Post by Yellow Pasque on 2009-05-08
Reinstall it? (shouldn't touch your configuration)
```
sudo apt-get --reinstall install pidgin
```

---

### Post by jjblackfox on 2009-05-08
> **_Purple_ said:**
> Which version of pidgin are you using?

I don't know how to find out without opening it.
I uninstalled it by typing in sudo apt-get remove pidgin then reinstalled it using sudo aptitude install pidgin, so would this make it the latest version?

---

### Post by jjblackfox on 2009-05-08
> **Temüjin said:**
> Reinstall it? (shouldn't touch your configuration)
```
sudo apt-get --reinstall install pidgin
```

No luck

---

### Post by _Purple_ on 2009-05-08
I think this was a bug in earlier version and was fixed in 2.5.2.
You can find the version using
```
pidgin -v
```

---

### Post by drs305 on 2009-05-08
I would rename your user file - /home/yourusername/.purple and then completely remove and then reinstall pidgin:
```

mv $HOME/.purple $HOME/.purple.bak
sudo apt-get purge pidgin
sudo apt-get update && sudo apt-get install pidgin

```

If it runs, rename the new $HOME/.purple folder and try to reinstate your old .pidgin folder again to see if you can preserve your settings.

---

### Post by jjblackfox on 2009-05-08
> **_Purple_ said:**
> I think this was a bug in earlier version and was fixed in 2.5.2.
You can find the version using
```
pidgin -v
```

Pigin 2.5.5

It worked fine until a few days after I installed the pidgin facebook chat plugin from: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)
I downloaded the pidgin-facebookchat-1.50.deb file. Don't know if this is related to the problem or not.

---

### Post by jjblackfox on 2009-05-08
> **drs305 said:**
> I would rename your user file - /home/yourusername/.purple and then completely remove and then reinstall pidgin:
```

mv $HOME/.purple $HOME/.purple.bak
sudo apt-get purge pidgin
sudo apt-get update && sudo apt-get install pidgin

```

If it runs, rename the new $HOME/.purple folder and try to reinstate your old .pidgin folder again to see if you can preserve your settings.

This did the trick, thanks

---

