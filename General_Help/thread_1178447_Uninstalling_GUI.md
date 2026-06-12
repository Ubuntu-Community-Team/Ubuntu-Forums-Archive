---
title: "Uninstalling GUI"
date: 2009-06-04
forum: General Help
---

### Post by Psycho.mario on 2009-06-04
Is it possible to uninstall everything gui (gdm && gedit, brasero...) with only a couple of commands. Id rather not have to type 
```
sudo apt-get remove gedit brasero...
```
anything easier?

Thanks

---

### Post by oldos2er on 2009-06-04
How far do you want to go in uninstalling everything gui? Remove X?

 You could try
```
sudo apt-get remove ubuntu-desktop gdm
```

---

### Post by Psycho.mario on 2009-06-04
I want to remove the GUI completely, so its just command line.

---

### Post by ajgreeny on 2009-06-04
I think ```
sudo apt-get autoremove ubuntu-desktop
``` may do the job, though I have to admit I've never used autoremove so am not 100% sure.

man apt-get shows:-
```
autoremove
           autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for some package and that are no more needed.
```

---

### Post by pmfabri on 2009-06-04
> **Psycho.mario said:**
> I want to remove the GUI completely, so its just command line.

Are you a h4x0r with $killz?

---

### Post by oldos2er on 2009-06-04
> **Psycho.mario said:**
> I want to remove the GUI completely, so its just command line.

 Then try
```
sudo apt-get remove ubuntu-desktop gdm xserver-xorg
```

---

