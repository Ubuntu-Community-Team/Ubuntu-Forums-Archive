---
title: "[SOLVED] How _do i_ install (America's Army 2.5)"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by kh1116 on 2007-08-07
Can someone please tell me, step by step, how to install America's Army.  I just downloaded the latest version available for Linux (I know they discontinued it for linux).  The file name is armyops250linux.run. This is my first game I have tried to install on Linux and I have no idea what to do.
Thanks, Kevin

---

### Post by hikaricore on 2007-08-07
Assuming you downloaded the file to your desktop, open a terminal and run the following one by one:

```

cd Desktop
chmod +x armyops250linux.run
sudo ./armyops250linux.run

```

Be sure not to run the game from the installer after it completes or it will own the game's config directory to root (well known bug in many installers).

---

### Post by kh1116 on 2007-08-07
ok thank you for the help! one more question, is that how you would install all .run files or will those commands (besides the file name) only work for americas army?

---

### Post by hikaricore on 2007-08-07
Yes this is the proper way to install most .run and .bin files that you'll find as packaged installers.  ^_^

---

### Post by kh1116 on 2007-08-08
thank you very much

---

### Post by hrvooje on 2007-11-03
> **hikaricore said:**
> Assuming you downloaded the file to your desktop, open a terminal and run the following one by one:

Be sure not to run the game from the installer after it completes or it will own the game's config directory to root (well known bug in many installers).

than how to run the game? i cant change  brightness

---

### Post by de_valentin on 2007-11-25
I have tried in 2 different ways now but I get the same error everytime
[https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy)
and the way described above.

and here is the error I get

valentin@valentin:/media/sda4/Downloads$ sudo ./armyops250linux.run
Verifying archive integrity...Error in MD5 checksums: fecac0db78c8a092635af59fa8761528 is different from dc7ebb581249712f797c6d283a8e98a5
valentin@valentin:/media/sda4/Downloads$ 

how can I fix this?

---

### Post by the_fury on 2008-11-18
I don't know about anyone else, but this is what I get:

thefury@Upstairs-Laptop:~$ cd Desktop
thefury@Upstairs-Laptop:~/Desktop$ chmod +x armyops250linux.run
thefury@Upstairs-Laptop:~/Desktop$ sudo ./armyops250linux.run
./armyops250linux.run: 2: Syntax error: newline unexpected

Ideas?

---

### Post by joepa518 on 2009-01-16
ive installed it and in usr/local/bin and there is an executeable file but it wont run

---

### Post by JonnyM on 2009-01-16
See [http://25Assist.com](http://25Assist.com)
This software should help you.

---

### Post by grosskem21 on 2010-07-06
how  do download it to desk top, when i download it it doesn't give me any options?

---

### Post by Kriskar on 2010-07-17
What do you mean: "Be sure not to run the game from the installer after it completes or it  will own the game's config directory to root (well known bug in many  installers)." because I think that's my problem

---

### Post by Perfect Storm on 2010-07-17
It means if you installed the game systemwide (with 'sudo') and you launch the game from the installer (that still runs with 'sudo'), you'll end up with messed up permission settings for that game/application.

---

### Post by crjackson on 2010-07-19
Don't waste your time my friend. The latest Linux version is 2.50, then you have to search for and install libstdc++5 from an older version of Ubuntu to make it even start in Lucid.

Next you will find that punkbuster won't let you log into a server because you version is out dated (and manual updates don't work), THEN.... you can find/download/install/run pbsetup and browse to your ~/.armyops250 folder (from pbsetup) and it will update punkbuster.

After you have completed all the training and corrected all the other issues, you will find 2 servers for ONE working deployment. Neither server will have ANY players because they are using MS-Win and newer versions of AA.

It's just not worth the hassle.

---

