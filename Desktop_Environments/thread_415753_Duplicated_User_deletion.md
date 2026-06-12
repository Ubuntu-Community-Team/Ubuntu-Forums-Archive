---
title: "Duplicated User deletion"
date: 2007-04-20
forum: Desktop Environments
---

### Post by johnbl on 2007-04-20
Being rather sick of getting  warnings as " you may not have sufficient permission .. " messages I had a look into the System > Administation >Users &  Groups. There I found my user name duplicated, in one all permissions possible are selected, in the other;

* NO permissions are selected

* The user name is greyed out AND a warning popup advises the name as incorrect format [ it isn't but that's of small matter !]

*  both have the same user directory

My question is however, what is the effect of simply deleting the dupe, any?

---

### Post by s_p_a_r_k_y on 2007-04-20
it may not be popular, but open up the console, Applications->Accessories->Terminal

then type in
```
sudo nano /etc/passwd
```
and look for the last line with your username. Delete that line "ctrl-k" and save the file. Be sure not to delete more than one line.

---

