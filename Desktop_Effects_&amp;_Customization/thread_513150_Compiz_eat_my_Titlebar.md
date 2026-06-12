---
title: "Compiz eat my Titlebar"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by moshazat on 2007-07-30
[[IMG]http://img255.imageshack.us/img255/2008/screenshot2mv9.th.png[/IMG]]("http://img255.imageshack.us/my.php?image=screenshot2mv9.png")

i really need help from u guys plz,If u can see from the picture, my titlebar was disappear when im using compiz fusion...

im using ubuntu feisty fawn, and boot this ubuntu using wubi, so i have dual boot ;windows xp and linux ubuntu

so i want my titlebar back but still can activate compiz, so anyone with solution?

---

### Post by AtrejuT on 2007-07-30
This means that your window decorator is not running.
To use emerald you have to run in a console
```

sudo apt-get install emerald
emerald --replace &

```

I hope this helps. Let us know.

---

### Post by hidden_leaf_sasuke on 2007-07-30
you maybe closing terminal application where you initiated compiz fusion. Dont close terminal. Let the terminal go to other workspaces..:)

---

### Post by ahchong on 2007-07-30
as for using the terminal, u can use the run application program by pressing alt+F2. then write compiz --replace at the corum..
then u dont need to close the terminal or hide the terminal at other workspace.

---

### Post by Espreon on 2007-07-30
Is that transparency on the top panel? How did you do that, I would love that!

---

### Post by moshazat on 2007-07-31
Hi guys,thanx a lot to u guys:D my compiz is working normally:D it is because im not activate the window decoration;) im  not activate compiz using terminal, but i set compiz to start at startup so it will start automatically when i boot ubuntu:) 


it just now that if i try to play movie using totem or vlc, the picture dont appear but the sound is still there, so what is wrong with that?

> **Espreon said:**
> Is that transparency on the top panel? How did you do that, I would love that!

Hi, yes the top panel is transparent, u just right click on the panel and chose properties i think, and u just adjust the transperancy...

sory, im using windows now at library, bcoz theres no internet at my place:p

---

