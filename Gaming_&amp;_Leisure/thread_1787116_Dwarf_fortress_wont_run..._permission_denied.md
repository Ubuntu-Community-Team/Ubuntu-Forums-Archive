---
title: "Dwarf fortress wont run... permission denied?"
date: 2011-06-20
forum: Gaming &amp; Leisure
---

### Post by Animator87 on 2011-06-20
Hello everyone,

I am a new Ubuntu user, so go easy on me. i was sick of my mac  and decided to switch. so far I love it. however I the one game i cannot get running that im addicted to is Dwarf fortress. i have downloaded the Linux version of the game, but when i try to run the df file in terminal it says Permission denied. i have allowed read and write, and checked the box Allow executing file as a program. but still no luck.  can anyone help me out? i am running Ubuntu 11.04 (natty) on a macbook pro

Thanks

---

### Post by icaho on 2011-06-20
Hi Animator87,

are you running the file using sudo and also if running in a terminal are you putting ./ before the executable?

for example

icaho@example:~$ sudo ./file.bin

That should work, if not try using gksu instead of sudo since it's a graphical app.

I hope that helps you

---

### Post by Animator87 on 2011-06-20
yea i used ./ before df, sudo nor gksu worked either.

---

### Post by snowpine on 2011-06-20
Don't run Dwarf Fortress with "sudo"--games don't need "root" permission to change anything/everything on your system!

Here's how I run Dwarf Fortress on my computer, works every time:

```
cd df_linux
./df
```

---

### Post by Animator87 on 2011-06-20
Nope i still get a permission denied... is there anyway to gain this permission?

---

### Post by snowpine on 2011-06-20
You need to be in the correct folder with the "df" file. You can use the command "ls" to verify this. For example:

```
cd /home/snowpine/downloads/df_linux
ls
chmod +x ./df
./df
```

You don't ever need to use "sudo" or "gksu" at any point in the process. :)

---

### Post by Animator87 on 2011-06-21
Wow this is really frustrating... still not working. this is what it spit back

justin@justin-MacBookPro:~/Downloads/df_linux$ ls
command line.txt  df                g_src  raw           readme.txt         sdl
data              file changes.txt  libs   README.linux  release notes.txt
justin@justin-MacBookPro:~/Downloads/df_linux$ chmod +x ./df
justin@justin-MacBookPro:~/Downloads/df_linux$ ./df
./df: 7: ./libs/Dwarf_Fortress: Permission denied
justin@justin-MacBookPro:~/Downloads/df_linux$ 

What am i doing wrong

---

### Post by snowpine on 2011-06-21
Try:

```
sudo chown -R justin ~/Downloads/df_linux 
```

"chown" is short for "change owner" and the -R option applies the change Recursively to an entire folder. This command should make you the owner of the entire /df_linux folder and everything in it. :)

---

### Post by Animator87 on 2011-06-21
Nope didn't work. thanks for all your help though:(

justin@justin-MacBookPro:~$ sudo chown -R justin ~/Downloads/df_linux
[sudo] password for justin: 
justin@justin-MacBookPro:~$ cd Downloads/df_linux
justin@justin-MacBookPro:~/Downloads/df_linux$ ./df
./df: 7: ./libs/Dwarf_Fortress: Permission denied
justin@justin-MacBookPro:~/Downloads/df_linux$ 

I arboreal tried re downloading Dwarf Fortress, even found older versions, nothing worked. 
should i try reinstalling Umbuntu?, i haven't put much on the computer yet...

---

### Post by Thewhistlingwind on 2011-06-23
You downloaded the game, go to properties, and flip the executable bit.

---

### Post by Animator87 on 2011-06-25
What do you mean flip the exe bit. i have checked the run executing file program checkbox. it still wont allow permission to run. i just wanna play this bloody game. i tried the windows virsion with wine but it runs extremely slow. what am i doing wrong

---

### Post by mistyautom on 2011-06-25
There is a deb package of Dwarf Fortress [here]("http://www.dotdeb.com/strategy.php").  It works great for me.

---

### Post by picpic66 on 2011-06-30
I am another new ubuntu user who has this problem.   Snow, when I try your execute command I get this 

```
./libs/Dwarf_Fortress: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

---

### Post by Perfect Storm on 2011-06-30
> **picpic66 said:**
> error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

Instal libsdl-image

---

### Post by JGT on 2011-08-06
I'm on very vanilla Lubuntu. I set the shell scripts to executable, the found I needed to install libsdl-ttf2.0-0. Worked fine after that.

---

