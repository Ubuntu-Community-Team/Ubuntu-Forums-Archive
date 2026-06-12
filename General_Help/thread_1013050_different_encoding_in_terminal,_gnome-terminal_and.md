---
title: "different encoding in terminal, gnome-terminal and konsole"
date: 2008-12-16
forum: General Help
---

### Post by xand on 2008-12-16
hi all,

I'm trying to run applications thru ssh that use the ibm850 encoding. I can normally do it via konsole, selecting this enconding from one of these paths:

- Settings->Edit current Profile -> advanced->Encoding-> Default 
character encoding: ibm850
OR
- View-> character encoding ->Western European -> ibm850

...and configuring the environment with "export TERM=linux".

Unfortunately, i can't do it via linux terminal or gnome-terminal. In gnome-terminal i've made the following procedure:

- added ""pt_BR.IBM850 IBM850" to the file "/var/lib/locales/supported.d/pt"

- updated locales: "dpkg-reconfigure locales"

- called gnome-terminal like this:
env LANG=pt_BR.IBM850 gnome-terminal --disable-factory --geometry 80x25

- and of course "export TERM=linux"

Apparently everything went fine, with accents working, but when inputting text, i realized the keys were still not configured for the encoding. Besides, there's these coordinates in the form "[0;850] [11;54]" popping in screen.

Using Intrepid!

Regards,

Alexandre

---

