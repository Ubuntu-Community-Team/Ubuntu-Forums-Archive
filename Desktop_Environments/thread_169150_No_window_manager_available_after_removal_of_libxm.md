---
title: "No window manager available after removal of libxml2 package"
date: 2006-05-02
forum: Desktop Environments
---

### Post by baswi on 2006-05-02
I am new to Ubuntu; I installed Breezy Badger on my dual boot laptop and everything worked OK.
I downloaded OPENSYNC (opensync.org) and tried to make the package. Because of unresolved externals I tried to intall LIBXML2-DEV via Synaptic package manager. I ran in all kind of version/depency problems; So I tried to uninstall LIBXML2; after that the only option I had in the GUI was to LOG OUT.
I couldn't create any new windows.
Somewhere I saw a message that no window managers were available.

AFter reboot it didn't start up X; After "$apt-get install fwm" I could do $startx and get the fwm window manager. However I cannot get GNOME again.
How can I correct my installation?

I tried already the following(without success)
[LIST]
[*]apt-get dist-upgrade
[*]apt-get install -f
[/LIST]

Bas

---

### Post by helpme on 2006-05-02
Install ubuntu-desktop again, to make sure everything the default install offers is really installed.

sudo apt-get install ubuntu-desktop

---

### Post by baswi on 2006-05-02
Thanks for your prompt reaction; that worked out.
Where can I find more of such handy 'apt-get install xyz's?

---

### Post by helpme on 2006-05-02
[QUOTE=baswi]Thanks for your prompt reaction; that worked out.
Where can I find more of such handy 'apt-get install xyz's?[/QUOTE]
Well, I don't think there are many more.
ubuntu-desktop is a meta-package, that is, it's sole purpose is to depend on everything that is installed with a default ubuntu install.
Similar kubuntu-desktop is the meta-package for kubuntu and xubuntu-desktop the one for kubuntu.

Btw., I think your problem was cause by uninstallin libxml2, instead of only uninstalling the dev package.

---

