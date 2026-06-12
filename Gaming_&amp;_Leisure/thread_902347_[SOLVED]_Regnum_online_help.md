---
title: "[SOLVED] Regnum online help"
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by dew5 on 2008-08-27
Hey

I have downloaded and ran through the install. The install created a quick launch icon on my desk top.

How ever I can not launch Regnum.

Please help.

When I click on the quick launch icon nothing happens.

dew5

---

### Post by EdThaSlayer on 2008-08-27
Please post the terminal results:


How to do that:
1.Open the terminal
2. Type "cd $home"
3. Type "cd Desktop"
4. Type "./rolauncher"


and post the results.

Knowing your graphics card model would also be useful.

---

### Post by dew5 on 2008-08-27
david@david-desktop:~$ cd $home
david@david-desktop:~$ cd Desktop
david@david-desktop:~/Desktop$ ./rolauncher
bash: ./rolauncher: No such file or directory
david@david-desktop:~/Desktop$ 

Here the out put 

Grafix card id nvidia geforce
fx5200xt

---

### Post by EdThaSlayer on 2008-08-27
> **dew5 said:**
> david@david-desktop:~$ cd $home
david@david-desktop:~$ cd Desktop
david@david-desktop:~/Desktop$ ./rolauncher
bash: ./rolauncher: No such file or directory
david@david-desktop:~/Desktop$ 

Here the out put 

Grafix card id nvidia geforce
fx5200xt

Oh sorry it might have been my fault since I have a ./rolauncher on my desktop(which might not be the default location). Where is this launcher of yours located? (you could try searching for it through the terminal: "locate rolauncher").
If so-try repeating the same step as above with the terminal. 

If that doesn't work, then try
1. right-clicking on the rolauncher
2. pressing on properties
3.checking if there is a check in the box next to "is executable"

---

### Post by dew5 on 2008-08-27
/david/home/regnum/rolauncher

---

### Post by EdThaSlayer on 2008-08-27
> **dew5 said:**
> /david/home/regnum/rolauncher

Just paste that into the terminal and check if it works.
If not, try checking if it's actually executable by
 a.right-clicking
 b.checking properties
 c. going to permissions
 d. checking the box next to "is executable"

---

### Post by dew5 on 2008-08-27
na it says no such file.

still need help.

If i search in places home regnum the rolaunch icon  is there. How ever it won't launch the game.

dew5

---

### Post by EdThaSlayer on 2008-08-27
> **dew5 said:**
> na it says no such file.

still need help.

If i search in places home regnum the rolaunch icon  is there. How ever it won't launch the game.

dew5

Did you do it the way I did it?
```
ets@ets-laptop:~$ /home/ets/regnum/rolauncher
```

Btw-have you checked the actual launcher if it's executable?
There is a nice gui app. that makes it easy to do...

---

### Post by EdThaSlayer on 2008-08-27
Hope this will solve the problems once and for all since-> I have to go sleep now :)

[IMG]http://i83.photobucket.com/albums/j303/startrekeddy888/Regstep1.jpg[/IMG]

[IMG]http://i83.photobucket.com/albums/j303/startrekeddy888/Regstep2.jpg[/IMG]

Sorry about it if it's a bit big though.

---

### Post by dew5 on 2008-09-15
Ok i figured it out.

I had dl the 64 bit version , however I am running a 34bit version sothats what the problem was.

how do i mark as solved again?

dew5

---

