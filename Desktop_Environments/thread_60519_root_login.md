---
title: "root login"
date: 2005-08-28
forum: Desktop Environments
---

### Post by aroselli on 2005-08-28
Ho installato ubuntu linux 5.04 senza grossi problemi.
Il sistema non ha chiesto una password per l'utente root.
In una schermata dell'installazione il sistema diceva che l'utente root era disabilitato per default e di usare il comando sudo per eseguire comandi con i privilegi del''amministratore.
Ora vorrei sapere come si può riabilitare l'utente root assegnandogli una password perchè usare il comando sudo è alquanto scomodo.
Grazie

---

### Post by angkor on 2005-08-28
I think:

```
sudo passwd root
```

will do the trick,

Or maybe I just completely misunderstood your Italian :)

Next time you'd better post in English cause in that way a_lot_more people will be able to understand it.

Ciao

---

### Post by aroselli on 2005-08-28
[QUOTE=angkor]I think:

```
sudo passwd root
```

will do the trick,

Or maybe I just completely misunderstood your Italian :)

Next time you'd better post in English cause in that way a_lot_more people will be able to understand it.

Ciao[/QUOTE]
Thankyou for your fast answer

When I type sudo password root in a windows terminal system ask me for the root password. I don't know root password becouse when I installed ubuntu linux system don't ask me for a root password but only for user password.
System tells,during installation, that root is disabled for default, but I cannot find how I can reenable root user and assign it a password.
My problem is how can I reenable root user, assign it a password an login as root user, becouse this is the best way for administrive tasks.
Thankyou

---

### Post by angkor on 2005-08-28
when you use 'sudo' in a terminal the system **doesn't** ask you for you **root** password. It asks you for the *password for the user you created during the install*. After you type in that password you're able to set the password for root. After that you can use 'su' or log in as root at the terminal.

Check out the guide:

[http://www.ubuntuguide.org/#setchangeenablerootpassword](http://www.ubuntuguide.org/#setchangeenablerootpassword)

Good luck

---

