---
title: "How to run America Army 2.5 after i had installed it?"
date: 2010-04-19
forum: Gaming &amp; Leisure
---

### Post by Evilthrill on 2010-04-19
i click on the 'armyops' and it does nothing..I had already installed it and there is no problem occured..why is this happen? any solution?

---

### Post by Evilthrill on 2010-04-19
nothing happens when i click the game...why?

---

### Post by ibuclaw on 2010-04-19
What happens if you try to run it from the terminal?

If the game is installed, typing:
```
armyops
```
should be sufficient.

(edit): btw, this smells like you have insufficient libraries installed, do you run a 64bit system?

Regards

---

### Post by lukeiscool on 2010-04-19
is it a linux based program? If it isn't, it could be wine thats causing a problem. Just a thought

Cheers

Sir Luke

---

### Post by ibuclaw on 2010-04-19
> **lukeiscool said:**
> is it a linux based program? If it isn't, it could be wine thats causing a problem. Just a thought

Cheers

Sir Luke

Yes, it is Native Linux. Just assuming OP got the right one. ;)

---

### Post by Evilthrill on 2010-04-19
when i type armyops in terminal,it show like this..

./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

why?anyone can help?

---

### Post by ibuclaw on 2010-04-19
libstdc++5 has been removed from the repositories since the release of Karmic, as is a deprecated library.

As a workaround, instead you have to install it manually either via downloading from the Jaunty repository [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb)


Regards
Iain


PS: I am assuming you are using a 32bit OS.

---

### Post by Evilthrill on 2010-04-19
> **ibuclaw said:**
> libstdc++5 has been removed from the repositories since the release of Karmic, as is a deprecated library.

As a workaround, instead you have to install it manually either via downloading from the Jaunty repository [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb)


Regards
Iain


PS: I am assuming you are using a 32bit OS.

thanks ibuclaw..I can play it right now! thanks a lot..

---

### Post by lukeiscool on 2010-04-21
Hi

This games sounds interesting. Do you know where i can get it from? 

Cheers

Sir Luke

---

### Post by mastablasta on 2010-04-21
I guess at [COLOR=#228822][www.**americasarmy**.com]("http://www.americasarmy.com") [/COLOR][COLOR=black]in the downloads section.[/COLOR]

---

### Post by ibuclaw on 2010-04-21
Here: [http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654](http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654)

---

### Post by Evilthrill on 2010-04-22
best ever game in linux..
BUT,this game,if you wanna play on9,make sure u get all mission accomplished..
Tired meh..
BTW,there is cheatcode avaiable?? i been searching and i dont make it..
does anyone have the cheatcode for mission accomplish?? :)

---

### Post by SVEN1 on 2010-04-23
I installed the game, interesting to play the training. But, I could not authenticate and login in my profile online thru the game.

After reading the Linux AA forum posts, it's a common problem as the login website will not accept new players for the older game version. You need to play AA3 but, no Linux support, Windows only.
So I did what most new downloaders do..uninstall the AA2.5 version and go back and play other games.. In my case went back to Urban Terror, some new servers have newer unique maps that are fun to play on.

Oh, by the way. While doing basic training on AA at the firing range, got tired of hearing the the Instructor shout to move my butt to the ammo table and firing range... After unloading a clip at the targets. I turned around and shot a few rounds into the guy. Two seconds later, I was no longer on the firing range, I was locked up in prison. Nice cell to wander around in. LOL

---

