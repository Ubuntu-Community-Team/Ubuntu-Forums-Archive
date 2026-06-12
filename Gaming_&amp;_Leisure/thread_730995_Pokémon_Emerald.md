---
title: "Pokémon Emerald"
date: 2008-03-21
forum: Gaming &amp; Leisure
---

### Post by erakko on 2008-03-21
I need help with VBA Express: I'm trying to play Pokémon Emerald on it, but screen is white always. Save type is set to Flash-128k. What do I do?

---

### Post by BigSilly on 2008-03-22
I had this problem too. I ended up having to get hold of a US version, rather than a EU version, in order to get rid of this problem. You've set your save right though - it has to be set to 128k flash in the VBA config file. 

Have a look around and let me know how you get on.

---

### Post by jj-johjoh on 2008-05-11
All right...
But, where have you gotten a US version of Pokémon Emerald:-s

---

### Post by hessiess on 2008-05-12
you could try mednafen emulator instead.

```
sudo apt-get install mednafen
```

its CLI, start it by selecting a rom, open with outher, use custom command and type 'mednafen'.

---

### Post by jj-johjoh on 2008-05-13
Aha!

Now I got it.

If you try oppening Pokémon Emerald BEFORE setting VBA-Express to use 128K flash save files, the emulator will automatically make a save file in 64K.
In such case, even after you set it to use 128K, it WILL KEEP LOADING THE 64K SAVE FILE, thus preventing you to run the ROM propperly.

The solution is simple. After setting the emulator with 128K, delete the pre-existent Pokémon Emerald save file (it will have the .SAV termination) and load the emulator once again.

TADA!

Works beautifully. WITH NO NEED OF AN AMERICAN VERSION OF POKÉMON EMERALD!!!

I hope it helps!
NOW HAVE FUN!
:popcorn:

---

### Post by golem1989 on 2008-11-14
do you know, how to link 2 emulators with each other to be able to swap pokemons?!
i'm using VBA express too, because it works quite good ;)
isn't there any multi emulator patch or sth like that?!

---

### Post by golem1989 on 2008-11-16
i've read that VBA doesnt support linking 2 emulators and they don't look forward to make it possible...
so is there any other good linux emulator that supports linking?

---

