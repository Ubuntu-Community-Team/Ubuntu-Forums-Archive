---
title: "Login screen"
date: 2009-11-25
forum: Desktop Environments
---

### Post by nomko on 2009-11-25
I'm not quit sure if i'm at the right place here for my question, but up till version 9.04 it was possible to change the login screen and boot screen. I'm using 9.10 right now and i can't find the option to change all this. Does anyone know where i might find the option to change the boot screen as well the login screen? Both screens used by 9.10 are very ugly.
Many thanks!

---

### Post by scorp123 on 2009-11-25
> **nomko said:**
> Both screens used by 9.10 are very ugly. You'll have to downgrade to the old version of the login manager because the new version of GDM is so totally not themable or customizable in any way. Nope, I am not kidding. Great progress, huh?

So here are the instructions on how to downgrade the login manager that came with Ubuntu 9.10 back to the themable and customizable one from Ubuntu 9.04:


[http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)

---

### Post by nomko on 2009-11-25
> **scorp123 said:**
> You'll have to downgrade to the old version of the login manager because the new version of GDM is so totally not themable or customizable in any way. Nope, I am not kidding. Great progress, huh?

So here are the instructions on how to downgrade the login manager that came with Ubuntu 9.10 back to the themable and customizable one from Ubuntu 9.04:


[http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)


That really sucks! This means that one of the reason of choosing for Linux/Ubuntu has been killed by Canonical... no more changing without some hardcore adjustments. To me, this looks more like a Microsoft thing. But i'll try your way scorp123, thanks anyway!

---

### Post by scorp123 on 2009-11-25
> **nomko said:**
> ... no more changing without some hardcore adjustments.  Apparently they will re-add this to the next version of GDM and Ubuntu (Ubuntu 10.04). But IMHO they should not have released this version if it's so crippled like that ... they should ship with the old good login manager per default. Don't fix it if it ain't broken.

Downgrading GDM works tip top ... I just did it again today for two coworkers (they too were unhappy with the new GDM and its total lack of features ...) and it worked. Just remember to either adjust the wrong path in the config file or to create the missing symbolic link or else GDM won't be able to start ...

---

