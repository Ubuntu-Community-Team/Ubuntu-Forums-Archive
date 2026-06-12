---
title: "America's Army armyops won't open??"
date: 2010-07-07
forum: Gaming &amp; Leisure
---

### Post by oleink on 2010-07-07
I installed AA today (I didn't know till now that it was on linux although its just 2.5) but the armyops file won't open...?

In terminal my output is as follows:
```
jordan@jordan-laptop:~/Documents/AA$ ./armyops
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
jordan@jordan-laptop:~/Documents/AA$ 

```

---

### Post by oleink on 2010-07-07
oh and btw I just found out I don't have that package but it isn't in synaptic???!!

---

### Post by ELD on 2010-07-08
> **oleink said:**
> oh and btw I just found out I don't have that package but it isn't in synaptic???!!

Erm try searching for it...would be the first obvious thing to try.

libstdc++.so.5

---

### Post by oleink on 2010-07-11
> **ELD said:**
> Erm try searching for it...would be the first obvious thing to try.

libstdc++.so.5

Yeah I got it but now it just won't open.  It freeezes

---

### Post by crjackson on 2010-07-12
I googled it, downloaded the deb and it fixed the problem. I completed all the training but cant participate in a game deployment because punkbuster is out dated.  I downloaded/installed the updates but they wont validate so PB kicks me. AA doesn't support Linux any more.  Here is the link to download the missing files.

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb)

I finally got it to validate by downloading / installing pbsetup.  I then ran the program and it asked me to add a game. I browsed to ~/.armyops250 folder and it added the game and updated PB.  It now authenticates and runs just fine.

The problem now is that only 2 servers can be found and neither of them have ANY players.  Not to mention only one mission is available.  It could be that you have to complete a mission before the others become available, or it could be that this version is so out dated it's a complete waste of time.

At least I got it installed and working.  It was bugging me but...

---

### Post by ELD on 2010-07-13
It is a waste of time, the version is so out date and unsupported it's simply not worth anyones time, you are better off playing Enemy Territory or one of the other maaaany FPS games that actually work and work well.

---

### Post by oleink on 2010-07-15
> **ELD said:**
> It is a waste of time, the version is so out date and unsupported it's simply not worth anyones time, you are better off playing Enemy Territory or one of the other maaaany FPS games that actually work and work well.

Actually that was for the newest version.

---

### Post by ELD on 2010-07-15
> **oleink said:**
> Actually that was for the newest version.

You said 2.5, that is the last version they did for Linux, it is not supported.

To quote youreself
"although its just 2.5"

---

### Post by oleink on 2010-07-15
> **ELD said:**
> You said 2.5, that is the last version they did for Linux, it is not supported.

To quote youreself
"although its just 2.5"

actually i said i didn't know until after i installed the new one under wine that 2.5 was a linux useable version

---

### Post by ELD on 2010-07-15
*sigh* your not getting me at all.

2.5 may be for linux but it is unsupported and probably 0 players as it's so old.

Edit > About the actual error you get i only really just noticed you said you have the lib now but the game freezes, if you run it via the terminal their might be an error you can catch.

---

### Post by crjackson on 2010-07-19
Don't waste your time my friend. The latest Linux version is 2.50, then you have to search for and install libstdc++5 from an older version of Ubuntu to make it even start in Lucid.

Next you will find that punkbuster won't let you log into a server because you version is out dated (and manual updates don't work), THEN.... you can find/download/install/run pbsetup and browse to your ~/.armyops250 folder (from pbsetup) and it will update punkbuster.

After you have completed all the training and corrected all the other issues, you will find 2 servers for ONE working deployment. Neither server will have ANY players because they are using MS-Win and newer versions of AA.

It's just not worth the hassle.

---

### Post by oleink on 2010-07-20
> **ELD said:**
> *sigh* your not getting me at all.

2.5 may be for linux but it is unsupported and probably 0 players as it's so old.

Edit > About the actual error you get i only really just noticed you said you have the lib now but the game freezes, if you run it via the terminal their might be an error you can catch.

I wasnt using 2.5 but i soon realized what the problem was and feel pretty ridiculous for not checking this before:  Wine coding doesn't support integrated cards

---

### Post by ELD on 2010-07-20
> **oleink said:**
> I wasnt using 2.5 but i soon realized what the problem was and feel pretty ridiculous for not checking this before:  Wine coding doesn't support integrated cards

You said in your original post "2.5", maybe you needed to be a bit clearer? What version where you actually using?

Where you using 2.5 for Linux as your post states or where you using a Windows version in Wine?

---

### Post by Uber-Nut on 2010-07-21
While America's Army 2.5 has very few populated servers left, there are still:
Clans
Tournaments
New Players
An Independent Stats Tracker
A Fun Community

As it was the last linux/mac port there will still be players, old and new, playing.

Also, in regards to the server list; you may want to check the 'Filters' button to make sure you aren't filtering out some of the servers.

Post your gamer name and I'll look out for you :D

---

