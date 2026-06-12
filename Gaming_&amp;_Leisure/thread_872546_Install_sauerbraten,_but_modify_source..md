---
title: "Install sauerbraten, but modify source."
date: 2008-07-28
forum: Gaming &amp; Leisure
---

### Post by r0b0t1 on 2008-07-28
How would I go about installing the sauerbraten game, using apt-get or syntaptic, while allowing me to make changes to the game's source? I visited #ubuntu but instructions from them did not work (It was probably me messing up).


I'd be glad if you could help :D

---

### Post by ad_267 on 2008-07-28
You can use "sudo apt-get build-dep sauerbraten" to install everything required to compile it then "sudo apt-get source sauerbraten" will download the source code into the current directory. Then you should be able to run "./configure", "make" "sudo checkinstall" to compile the code and install it as a debian package so you can use a package manager to remove it later.

You might have to install the checkinstall package first.

---

### Post by r0b0t1 on 2008-07-28
Odd, no './configure'. I hope it still works.

EDIT: No, there is no .deb package created.

```

cp sauer_client	../bin_unix/native_client
cp sauer_server	../bin_unix/native_server
strip ../bin_unix/native_client
strip: Warning: '../bin_unix/native_client' is not an ordinary file
make: *** [install] Error 1

```

---

### Post by Sockerdrickan on 2008-07-28
I'm just curious, why compile it? What did you change
trying to cheat? :)

---

### Post by r0b0t1 on 2008-07-28
I'm not "trying" to hack, I'm successful. Although, I am unable to use sauerbraten at the moment, as there is this wierd error/bug/setting-I-unknowingly-enabled that makes it so I cannot see the console. Thus, I am trying to reinstall. (Which apparently doesn't work, I still can't see it)

---

### Post by Unanimated on 2008-07-28
Just get it from their website.

[http://www.cubeengine.com]("http://www.cubeengine.com")

---

### Post by r0b0t1 on 2008-07-28
Thats what I was doing, but I thought it would be convienient to get it via apt-get. Turns out it isn't :p


Although, now I need to take care of that error with the ingame console. Thanks everyone.

---

