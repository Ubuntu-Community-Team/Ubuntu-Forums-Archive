---
title: "emerald themes"
date: 2008-07-28
forum: Desktop Environments
---

### Post by bradpurvis on 2008-07-28
hey i need some help using .emerald themes i have the emerald theme manager but i don't know how to use it

---

### Post by bradpurvis on 2008-07-28
please explain how this works. anyone?

---

### Post by gjoellee on 2008-07-28
emerald themes changes the themes you see around the edges of the windows... and runs with Compiz Fusion
if yo don't have compiz fusion you can install it by adding this line to the terminal (Applications->Accessories->Terminal):

install compiz fusion:
```
sudo apt-get install compizconfig-settings-manager
```

install emerald:
```
sudo apt-get install emerald
```then download emerald themes from [www.compiz-themes.org]("http://www.compiz-themes.org") then enter Emerald click on import and find the themes you have downloaded

to make emerald start on startup go to System->Preferences->Sessions click on add
Name: Emerald
command: emerald --replace
click on OK

to make compiz fusion run at startup go to Sessions
Name: Compiz Fusion
command: compiz --replace
click OK


if you want to start emerald manually press ALT+F2 and add this code:
```
emerald --replace
```

if you want to start compiz manually:
```
compiz --replace
```

---

### Post by tamoneya on 2008-07-28
i get all my themes for emerald and everything else from gnome-look

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by bradpurvis on 2008-07-28
k lol i already knew that stuff i need to know how to apply the themes. thanks for responding.:)

---

### Post by UbuntuNerd on 2008-07-28
To apply a theme, go back into Emerald Theme Manager by either right-clicking the Compiz Fusion Icon or by starting it from the Preferences menu. You should see you list of themes providing that you downloaded them from [www.gnome-look.org](www.gnome-look.org)  To apply one of the themes, simply left-click it. It may take a second to apply.
  also here is a more detail guide


[http://hacktivision.com/index.php/2008/01/08/how-to-install-emerald-theme-manager-in-?blog=2]("http://hacktivision.com/index.php/2008/01/08/how-to-install-emerald-theme-manager-in-?blog=2")

---

### Post by bradpurvis on 2008-07-28
i did the left-click and it didn't do anything. the orginal ubuntu theme stayed the same any other tips to get it running?

---

### Post by UbuntuNerd on 2008-07-28
Try this in the terminal "emerald --replace" I had the same problem

---

### Post by UbuntuNerd on 2008-07-28
also if when you close the terminal it terminates emerald 

type this instead,

emerald --replace &

but you will need to do this everytime you login, so better go to preferences->session and in startup programs, click on add and in the command box enter,

emerald --replace

ok and close. make sure your newly created entry is checked.

---

### Post by tamoneya on 2008-07-28
when i first installed emerald i found that restarting x helped.  save any documents you have open and hit ctrl-alt-backspace.

---

### Post by bradpurvis on 2008-07-28
thanks i will try

---

### Post by bradpurvis on 2008-07-28
idk. i have to keep the terminal open or the windows border goes away how annoying...

---

### Post by bradpurvis on 2008-07-29
still need help here getting desprete

---

### Post by bradpurvis on 2008-07-29
please someone help me i have been waiting for two days now

---

### Post by bradpurvis on 2008-07-30
someone at least tell me if the problem is unfixable so i don't have to keep coming back

---

