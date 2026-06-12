---
title: "Cheat Tool -- Memory Scanner"
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by MasterXandrex on 2008-07-12
All,

I am looking for a memory scanner like gamewiz32 or cheat-o-matic in Windows. It's typically a cheat tool for simple games it allows one to look through memory for a value, narrow the list of possible locations down as the values change, and then change it.

Anyone know of any?


Xan

---

### Post by scragar on 2008-07-12
scanmem is a command line tool that achives the desired effect.
```
sudo apt-get install scanmem
```

---

### Post by NovruzeliH on 2008-07-12
Nvm He Already Said It

---

### Post by MasterXandrex on 2008-07-12
Alright, looks promising. Wanna give me a rundown on hoe it works?

Xan

---

### Post by scragar on 2008-07-12
before you want to run scanmem you want to find the PID(Process ID), so ps is a good tool for that:
```
ps -Ao pid,command | grep **NAME OF GAME HERE**
```
the PID is the number at the front. Now launch scanmem with with the program:
```
scanmem **PID here**
```
or, if you wanted like so:```
scanmem
pid **PID here**
```
now it's running just put in a value to find, change the value in the game/whatever, then retest until there's 1 result. then set it like so:
```
set **NUMBER**
```
couldn't get much easier than that.
```
reset
```
will let you test for a new number then, and:
```
>
<
=
```
let you test for values which are higher, lower or unchanged, handy if you can't see the real value of a variable.

---

### Post by Vadi on 2008-07-13
Kind of confused about the value thing. I tried some numbers/words and it didn't work, "list" doesn't show anything either.

---

### Post by scragar on 2008-07-13
you try the number, then do it again after changing it in the game until you only have 1 result in scanmem (it say's the number of matches each time), then you set it.

Oh, and don't put in "0" on it's own, as far as scanmem works a number starting with 0 repesents hex(I think), with a wild card on each side, so you actualy wind up matching every single chunk of memory, which will cause a fair increase in ram usage as it atempts to store such a huge list, use **000** instead, since this will match a byte with the value 0

---

### Post by FranMichaels on 2008-07-14
```
scanmem `pidof whatever`
```

replace whatever with the name of the app running (check taskmanager ;) )
Is easier :)

---

