---
title: "[SOLVED] loading bar"
date: 2008-04-15
forum: Desktop Environments
---

### Post by danex_ali on 2008-04-15
hi.
i have Ubuntu installed on my pc and it came with the GNOME environment. Then i also installed the KDE (with the terminal console) so that i can choose between the 2 environment.
The problem is that since i have installed KDE, my loading up bar (the one that appears before the login on Ubuntu) is now the KDE's bar. This means that the bar now is blue and appears the letters "KUBUNTU" and the symbol of kubuntu on the loading up screen ( the screen that appears before the login screen ).
how do make my loading up bar return to the Ubuntu bar (the orange one, with the ubuntu letters on the screen and the symbol of ubuntu) ??
without uninstalling the KDE of course... :P
Thankx!

---

### Post by Diabolis on 2008-04-16
The blue loading bar with the kde logo is the splash screen and its called ksplash, in ubuntu its a package called usplash. Just uninstall it.

sudo apt-get remove ksplash

---

### Post by danex_ali on 2008-04-19
and then after i uninstall the KDE splash screen, how do i activate the Ubuntu splash screen?
thankx

---

### Post by danex_ali on 2008-06-29
> **Diabolis said:**
> The blue loading bar with the kde logo is the splash screen and its called ksplash, in ubuntu its a package called usplash. Just uninstall it.

sudo apt-get remove ksplash

Diabolis, thnkx for your reply but that command didn't do nothing to my blue loading screen....
After some investigation i finally found the solution for this 'problem', and i want to share it with u people.
The answer its simply this:
sudo update-alternatives --config usplash-artwork.so

and then choose the number of the ubuntu screen, that in my case was the number 1 .
;)

---

