---
title: "desktop gone"
date: 2015-06-11
forum: Desktop Environments
---

### Post by jimbo10 on 2015-06-11
[FONT=arial]just installed Ubuntu 14.04/64-bit;
(my previous 32-bit install had corrupted due to HDD probs)
seemed to work OK....but....now...the "icon" bar on the left-hand side has disappeared..... :(
also....there is no "system menu" in the top RH corner.....
all i got is the "wall-paper"

any help/tips much appreciated!

ta![/FONT]

---

### Post by grahammechanical on 2015-06-11
There are a couple of things that you can try.

1) Right click the wallpaper and in the menu that appears select Change Desktop Background. That will open System Settings in the appearance utility but from there you can get to Software & Updates and in the Additional Drivers tab you can change the video driver.

2) Open a terminal Ctrl+Alt+T or Ctrl+Alt+F2 and run

```
dconf reset -f /org/compiz/
```

and/or

```
 setsid unity
```

To restart from the terminal

```
sudo shutdown -r now
```

to shut down or halt

```
sudo shutdown -h now
```

Regards

---

### Post by jimbo10 on 2015-06-11
[FONT=arial]thnx for that!

got into the "system settings" but couldn't find any-where to dwn/ld additional drivers [/FONT]:|[FONT=arial]

will have another look tomorrow maybe....

^ Alt T wouldn't bring up the Term window but ^ Alt F[SUB]2[/SUB]  did!

the "dconf" command did nothing AFA i could tell;
the "sudo shutdown" command did re-boot, though!
the trouble seemed to start when i tried dwn/ldng this Oracle Virtual Machine bizzo;
it wouldn't install;

...although every-thing seemed to be very sluggish before that, too!
am wondering if only having 4gig of RAM might have some bearing on it all ?
the 64-bit Ubuntu install only seems to be recognising 3gig of that (?) would i be better off re-installing the 32-bit version? 
(i'm running an old dual core Intel P4 CPU with a 1gig gfx card)

thnx!








[/FONT]

---

### Post by Frogs Hair on 2015-06-11
Try system Settings> Software & Updates > Additional Drivers.

---

### Post by jimbo10 on 2015-06-11
[FONT=arial]thnx again!
yeh...got onto that "system settings" & the 'additional drivers' tab.....
but....there didn't seem to be any way of dwn/ldng.....  :(

(maybe i should re-install the 32-bit vrsn of Ubuntu, eh?)[/FONT]

---

### Post by jimbo10 on 2015-06-12
[FONT=arial]OK....dwn/ld the 32-bit Ubuntu & re-installed.....
so far: seems OK....
(the 64-bit vrsn must still have some issues....or.....maybe i don't have enough RAM, eh?!? :(  )
[/FONT]

---

### Post by Frogs Hair on 2015-06-12
If you have more than 4GB of memory you would need 64 bit to utilize it.

---

