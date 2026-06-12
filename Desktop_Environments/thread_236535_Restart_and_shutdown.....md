---
title: "Restart and shutdown...."
date: 2006-08-14
forum: Desktop Environments
---

### Post by Nhatz on 2006-08-14
Hi guys!..... i'd just installed ubuntu 6.06 the other week then the other day when im about to quit...... my restart anf shutdown buttons are gone!

---

### Post by hopstah on 2006-08-15
what exactly do you mean?  do you mean that when you go to System > Quit... that the options to shutdown and restart are gone?  Or did you have a button on a panel that has disappeared?

---

### Post by sarbor77 on 2006-12-06
> **hopstah said:**
> what exactly do you mean?  do you mean that when you go to System > Quit... that the options to shutdown and restart are gone?  Or did you have a button on a panel that has disappeared?

Yes, when I go to System > Quit... that the options to shutdown and restart are gone!

---

### Post by nealaustin on 2008-01-17
My shutdown and restart buttons disapeared (7.10) how do I get them back? The red log off button is still there.

---

### Post by GSF1200S on 2008-01-18
> **nealaustin said:**
> My shutdown and restart buttons disapeared (7.10) how do I get them back? The red log off button is still there.

Im not exactly sure what caused it, although it seems that its something with X.

As a temporary solution, you can use the following commands (if you dont know them already) to accomplish shutdown and reboot:

Shutdown
```
sudo shutdown -h now
```

Restart
```
sudo reboot
```

The below command will restart X, so make sure you save your work!
Just out of curiousity, what happens when you put in:

```
sudo /etc/init.d/gdm restart
```
does the option pop up in the Exit button then?

You can try to run:
```
gdmsetup
``` If it complains about not being root, put sudo in front...

And I suppose another option would be to reconfigure gdm with apt:

```
sudo dpkg-reconfigure gdm
```
and then restart X (Ctrl+Alt+Backspace) to see if that helps...

Good luck :)

**EDIT** This thread may be of help- try this first and then try the above:
[http://ubuntuforums.org/showthread.php?t=417755](http://ubuntuforums.org/showthread.php?t=417755)

---

