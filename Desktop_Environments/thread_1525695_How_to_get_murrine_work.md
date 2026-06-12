---
title: "How to get murrine work?"
date: 2010-07-07
forum: Desktop Environments
---

### Post by ario on 2010-07-07
Installed Ubuntu 10.04
Have compiz version 1:0.8.4-0ubuntu15 enabled and have all its effects.
Have gtk2-engines-murrine version 0.90.3+git20100323-0ubuntu3 installed.
Installed some themes from murrine official site and enabled them from appearance page (I saw semi-transparent GTK widgets in their screen-shots).
**But GTK widgets are still fully opaque for me. What other things I must do to have my GTK widgets semi-transparent?**
Thanks for your helps guys.
Best wishes!

---

### Post by regala on 2010-07-07
> **ario said:**
> Installed Ubuntu 10.04
Have compiz version 1:0.8.4-0ubuntu15 enabled and have all its effects.
Have gtk2-engines-murrine version 0.90.3+git20100323-0ubuntu3 installed.
Installed some themes from murrine official site and enabled them from appearance page (I saw semi-transparent GTK widgets in their screen-shots).
**But GTK widgets are still fully opaque for me. What other things I must do to have my GTK widgets semi-transparent?**
Thanks for your helps guys.
Best wishes!

configure Compiz to do so. this is not even remotely related to Murrine. Just use CompizConfig thingy in the Preferences menu.

---

### Post by ario on 2010-10-02
> **regala said:**
> configure Compiz to do so. this is not even remotely related to Murrine. Just use CompizConfig thingy in the Preferences menu.

Can you please describe how? I went to that window but didn't see any thing about transparent widgets or... .

---

### Post by ario on 2010-10-02
No I think it's nothing about compiz config in system preferences menu. I installed murrine, murrine themes but window widgets (Not windows themselves) are still opaque.
So... BUMP!

---

### Post by hhh on 2010-10-02
Your right that the Murrine RGBA transparency is totally different from Compiz's transparency effect. Here's an article to help you...
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

---

### Post by ario on 2010-10-02
> **hhh said:**
> Your right that the Murrine RGBA transparency is totally different from Compiz's transparency effect. Here's an article to help you...
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

Thanks for the response, I did what he mentioned in the link you sent, but the most boring situation happened: Nothing! Just like before:D
Any idea?

---

### Post by hhh on 2010-10-02
You install gnome-color-chooser and gtk2-module-rgba and ran apt-get upgrade and enabled RGBA in gnome color chooser and logged out and back in? What video card do you have? BTW, those instructions worked for me but I lost my desktop and had to install Nautilus Elementary to fix it...
[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)

If RGBA doesn't work for you, you can uninstall everything, instructions are in the WebUd8 link.

BTW, my desktop...
[http://img101.imageshack.us/img101/9364/screenshotxp.png](http://img101.imageshack.us/img101/9364/screenshotxp.png)

---

### Post by ario on 2010-10-12
> **hhh said:**
> You install gnome-color-chooser and gtk2-module-rgba and ran apt-get upgrade and enabled RGBA in gnome color chooser and logged out and back in? What video card do you have? BTW, those instructions worked for me but I lost my desktop and had to install Nautilus Elementary to fix it...
[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)

If RGBA doesn't work for you, you can uninstall everything, instructions are in the WebUd8 link.

BTW, my desktop...
[http://img101.imageshack.us/img101/9364/screenshotxp.png](http://img101.imageshack.us/img101/9364/screenshotxp.png)

RGBA doesn't work for me. And I don't have enough time to find and solve the problem. It must be somewhere in my system but I think it's impossible to find that in two or three months and full time working! So I decided to forget about that.
Thanks a lot.

---

