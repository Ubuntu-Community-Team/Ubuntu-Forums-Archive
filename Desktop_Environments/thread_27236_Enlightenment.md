---
title: "Enlightenment"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Fab on 2005-04-15
I installed the Enlightenment package from the universe repo as well as the enlightenment-data , the themes, the menu editor and the keybindings editor.
I tried to manually create an ~/.xsession file to use E, log out, ctrl+alt+del, login, starts metacity.
I ran enlightenment-install, it created the same ~/.xsession file with some additional comments, but the same commands. Tried logout, ctrl+alt+del, login anyway, still metacity.
Can someone point me out to the obvious thing i missed? :P

thanks in advance  ](*,)

---

### Post by Stormy Eyes on 2005-04-15
Try **ln -s ~/.xsession ~/.xinitrc** and then select "Custom Session" from the GDM sessions menu.

---

### Post by Fab on 2005-04-15
ah
silly me, i forgot that i had gnome as default session

thank you anyway :)

---

