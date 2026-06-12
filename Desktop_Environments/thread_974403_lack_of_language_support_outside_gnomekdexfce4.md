---
title: "lack of language support outside gnome/kde/xfce4"
date: 2008-11-07
forum: Desktop Environments
---

### Post by baugen on 2008-11-07
I have a 512 ram machine and prefer to avoid the heavy desktops. I use Norwegian localization.
In Debian this was not a problem because you have text based tools for language setup.
F.ex you can add locales using the dpkg-reconfigure locales command --some idiot has removed this from ubuntu.

I installed Xubuntu using the net install cd but i use slim + wmaker as my desktop. I installed 8.04 then upgraded to 8.10.
Even with all language packs installed language support is way poorer than in Debian --seems it basically does not work outside the default desktop environments.

When I start a program i get 'locale not supported, reverting to default' (which is English US)
I cannot fix this as locales are handled autocrapically by the installation of language packs..

my /etc/default/locale

LANG="nb_NO.UTF-8"
#LANGUAGE="nb_NO.UTF-8"
LANGUAGE="nb_NO.UTF-8:nb:nb_NO:no:nn_NO:nn:en_GB:en_US:en"

Can this be done better?

anyone know of a manual way of adding locales to ubuntu?

---

### Post by baugen on 2008-11-07
had a look here, the locale-related stuff but it did not help on my system

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-2](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-2)

---

### Post by baugen on 2008-11-09
Right, got it working, as far as possible anyway, by enabling Debian Etch repos and installing locales-all.
I have not tried to mess with config files manually, takes too much time.
now works as well as it can outside gnome

---

