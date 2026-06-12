---
title: "No X Close Button on windows"
date: 2008-02-28
forum: Desktop Environments
---

### Post by sablefoxx on 2008-02-28
Hey guys im pretty new to ubuntu but hopefully this is an easy fix, a setting perhaps somewhere i cant find.  Any way all my windows are missing the top bar (with the min/max/close), how do i get it back.  And it only goes away when i have Compiz on so i assume its some setting in there but i just cant find it!

---

### Post by overdrank on 2008-02-28
> **sablefoxx said:**
> Hey guys im pretty new to ubuntu but hopefully this is an easy fix, a setting perhaps somewhere i cant find.  Any way all my windows are missing the top bar (with the min/max/close), how do i get it back.  And it only goes away when i have Compiz on so i assume its some setting in there but i just cant find it!

Hi and if you have a nvidia card you can try this command ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by sablefoxx on 2008-02-28
Nope :( , integrated intel chipset its an eee-PC  :)

Specs:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220261](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220261)

---

### Post by overdrank on 2008-02-28
> **sablefoxx said:**
> Nope :( , integrated intel chipset its an eee-PC  :)

Specs:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220261](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220261)

Ok do you have compizconfig-settings-manager installed ? if so then you can open CCSM under system, preference and look for window decorations and ensure it is checked and also look at the command on the general tab there also.

---

### Post by sablefoxx on 2008-02-28
> **overdrank said:**
> Ok do you have compizconfig-settings-manager installed ? if so then you can open CCSM under system, preference and look for window decorations and ensure it is checked and also look at the command on the general tab there also.

I got it installed, and command is blank.

---

### Post by overdrank on 2008-02-28
> **sablefoxx said:**
> I got it installed, and command is blank.

Ok try the command compiz and you may have to install emerald and then enter emerald in the command. You can start emerald with the command emerald --replace by using the alt, F2 keys

---

### Post by sablefoxx on 2008-02-29
okay i installed emerald but same problem the bar shows up for a second but as soon as i close the terminal they all go way :(  and alt+F2   isnt working

[B]
***UPDATE SOLVED***[/B]

Disabled all visual effects, Alt+F2 working again, ran "emerald --replace" re-enabled visual effects working again.  Thx for all the help bro!

---

### Post by ansicplusplus on 2008-03-01
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Thanks, this worked for me, too. While trying a custom-build kernel, I somehow scrambled my X configuration and spent the rest of the day getting thing back in order.
The missing 'X'-Button is quite a mysteroius effect, as I couldn't find an errormessage. The buttons where just missing.
Thanks alot,
ansicplusplus

---

