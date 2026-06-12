---
title: "ICE Authority cannot be read!"
date: 2005-03-21
forum: Desktop Environments
---

### Post by cdhotfire on 2005-03-21
Just restarted my gnome, and now it says session lasted less than  seconds, and that ICEauthority is not able to be read. Umm, help.8-[

---

### Post by bored2k on 2005-03-21
[QUOTE=cdhotfire]Just restarted my gnome, and now it says session lasted less than  seconds, and that ICEauthority is not able to be read. Umm, help.8-[[/QUOTE]
 Did you install K3B or something ?

alt+ctrl+f1

Login in a shell
You can change permissions to the ICEauthority file to your users [or if its already the users, to root] or delete the file .

I suggest you try chown first then deleting [Justin Case] .

---

### Post by cdhotfire on 2005-03-21
will try, thxs.:-D

---

### Post by cdhotfire on 2005-03-21
yay, that poped like popcorn. O and i did install k3b, then decided to stay with the baka.:twisted:

---

### Post by bored2k on 2005-03-21
[QUOTE=cdhotfire]yay, that poped like popcorn. O and i did install k3b, then decided to stay with the baka.:twisted:[/QUOTE]
 So wich trick was it ? deleting the file or chowning it ? [for future reference]

---

### Post by cdhotfire on 2005-03-21
delete.=D>

---

### Post by bored2k on 2005-03-21
[QUOTE=cdhotfire]delete.=D>[/QUOTE]
 *Parfait*. *adds this error up on his error solutions ;)*

---

### Post by az on 2005-03-21
I think that the recommended way of fixing this is chowning it.

---

### Post by cdhotfire on 2005-03-21
that did not work.:sad:. So operation deletion was a go.8-)

---

### Post by az on 2005-03-21
[http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b](http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b)

Quote:

If you ever use plain sudo instead of gksudo to open K3B and you cannot log into Gnome afterwards, you must boot into safe mode and type:
sudo chown your user name:your user name.ICEauthority?
in the terminal.

---

### Post by cdhotfire on 2005-03-21
[QUOTE=azz][http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b]("http://www.ubuntulinux.org/wiki/K3BHowto/view?searchterm=k3b")

Quote:

If you ever use plain sudo instead of gksudo to open K3B and you cannot log into Gnome afterwards, you must boot into safe mode and type:
sudo chown your user name:your user name.ICEauthority?
in the terminal.[/QUOTE]

 	that did not work.:sad:. So operation deletion was a go.8-)

did we not already establish this?

---

