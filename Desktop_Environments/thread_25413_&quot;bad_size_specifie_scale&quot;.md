---
title: "&quot;bad size specifie scale&quot;"
date: 2005-04-10
forum: Desktop Environments
---

### Post by rocket.nz on 2005-04-10
Hi there, after an apt-get upgrade i got the following error when x starts, i cannot get to the ubuntu x login screen because of the following error.

"there was an error loading the theme human"
"bad size specifier scale"

anyone know how i can fix this? :( :(

any help much appreciated!! :-?   :-P

---

### Post by humanity_to_others on 2005-04-10
You can try another theme or reinstall current theme pack.

---

### Post by rocket.nz on 2005-04-10
[QUOTE=humanity_to_others]You can try another theme or reinstall current theme pack.[/QUOTE]


yes but how would i do that from console?

---

### Post by humanity_to_others on 2005-04-10
install xfce4 then you have a gui:
```
sudo apt-get install xfce4
```

---

### Post by rocket.nz on 2005-04-10
[QUOTE=humanity_to_others]install xfce4 then you have a gui:
```
sudo apt-get install xfce4
```[/QUOTE]


thx i will try that, but what do you think caused the problem in the first place?

---

### Post by brian g on 2005-07-09
i have this problem as well.. 

i get the error bad size specifier scale.
then it continues to load gnomes default login screen with no mouse support and i have no way to get the cursor to the User field. 

how can i get to a command line to *sudo apt-get install xfce4* if gnome is basicly unresponsive?
is there a way to start my computer to a command line without is starting gnome?
then i could just *sudo apt-get install xfce4* right?

brian g
total linux noob coming to you live from knopix..  ](*,)

---

### Post by lreyes6 on 2005-07-11
I've tryed to install Xfce4 from synaptics and from terminal with **sudo apt-get install xfce4** and i'm having this error message... [B]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-panel/xfce4-panel_4.2.1.1-1ubuntu1_i386.deb)
  MD5Sum mismatch[/B]

I did an apt-get update but nothing... any idea? 

thanks

---

### Post by brian g on 2005-07-12
lreyes-
i'm having that same problem as well.
more details [here](http://ubuntuforums.org/showthread.php?t=47962).

---

