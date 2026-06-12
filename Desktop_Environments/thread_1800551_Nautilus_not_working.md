---
title: "Nautilus not working"
date: 2011-07-09
forum: Desktop Environments
---

### Post by Channi on 2011-07-09
Hi friends,
I installed many software on my PC today, after that nautilus stopped working. It gives the error about GTK:
```
channi@channi ~ $ nautilus

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted

```

Though I have changed default file manager to Dolphin now, but I want to know the solution and probable reason of this problem.
Any idea friends.....??

---

### Post by koleoptero on 2011-07-09
It looks like you must have added a ppa or something that has upgraded nautilus to the gnome3 version but hasn't done the same for all the needed libraries? Or some nautilus extension perhaps? You should review what you've changed in your software more closely for this.

---

### Post by Channi on 2011-07-09
I did an upgrade 
```
sudo apt-get update && sudo apt-get upgrade
```
after installing Amarok and Kdevelop in Ubuntu 11.04.

---

### Post by Channi on 2011-07-09
I also installed unity2D but then removed it using
```
sudo aptitude purge unity
```
I am using gnome 2.X as my Desktop

---

### Post by koleoptero on 2011-07-09
If it's just those things then I don't know what could cause nautilus to stop working. You can try deleting the nautilus preferences in your home folder by deleting the .nautilus hidden folder. And if that doesn't work then perhaps reinstalling it from synaptic.

I'm sorry I can't be of more specific help but that's the first time I see such an error.

---

### Post by Channi on 2011-07-09
All right, thanks for giving your time......:)

---

### Post by Channi on 2011-07-10
Reinstalling nautilus solved the problem but now Nautilus starts with an ugly interface. Any suggestions to solve this ??

---

### Post by koleoptero on 2011-07-10
> **Channi said:**
> Reinstalling nautilus solved the problem but now Nautilus starts with an ugly interface. Any suggestions to solve this ??

You probably just had to kill nautilus and start it again. I imagine by the time you read this you'll have solved it. If it doesn't fix the problem try running gnome-settings-daemon and then killing nautilus again.

---

