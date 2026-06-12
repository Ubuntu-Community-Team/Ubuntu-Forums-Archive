---
title: "startup help"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Deathcon_1 on 2005-10-18
Ok, first of all something keeps resetting my root password; this is the 3rd time i've had to reset it, any ideas there?

second:, i want to set it so that the GUI does NOT load defualt, it goes to a bash prompt.  

third: i'd like to set it so that either ROOT is the defualt login and will automatically login when booted.

fourth: i need to add '/etc/lampp/lampp start' somwhere to startup lampp when the whole sysem is booting up, as well as some other programs (i can use the lampp one as a refernce to set these up however)

fith: i need to find a program to predict the winning lottery numbers to win the lottery;) 

thanks to all who help in advance, its much appreciated

---

### Post by Murgle on 2005-10-18
1: I have no idea
2: edit your /etc/inittab and find the section that says 
```
l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6

```

to say 
```
l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
#l3:3:wait:/etc/init.d/rc 3
#l4:4:wait:/etc/init.d/rc 4
#l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6

```

and I think that should do it, anyone confirm or have a more eloquent way?

3:if you use my method for 2 you might defalut login root otherwise im not sure
4: not sure.
5:try fortune

---

### Post by adwait on 2005-10-18
1)Wierd...how are you setting the root password?
You can use
```
sudo passwd
```
2)Use
```
sudo rcconf
```
Uncheck the box against gdm using the spacebar and and ok your way out.
3)That's not a very good idea and I am not sure how that can be done in bash. In the GUI login you can do that throught
```
sudo gdmsetup
```
4)Add the line
```
/etc/lampp/lampp start
```
to a file. Make the file executable using
```
chmod +x <filename> 
```
Copy it to the /etc/init.d/ directory. 
Again run rcconf (as described above) and check the box against the filename of the file you just created
5)I'd be having my secretary writing this while I enjoy with my extremely sexy girfriend and a chilled drink. if I had that. There are somethings OSS can't do, for everything else......there's Ubuntu ;)

---

### Post by wylfing on 2005-10-18
[QUOTE=Deathcon_1]
third: i'd like to set it so that either ROOT is the defualt login and will automatically login when booted.
[/QUOTE]

No, you don't. There is no reason for this other than you wish to make a mess of your box as quickly as possible. In that case, our help is moot :)

> 
fourth: i need to add '/etc/lampp/lampp start' somwhere to startup lampp when the whole sysem is booting up, as well as some other programs (i can use the lampp one as a refernce to set these up however)


Try looking at this thread: [http://www.ubuntuforums.org/showthread.php?t=40680](http://www.ubuntuforums.org/showthread.php?t=40680)

---

### Post by Deathcon_1 on 2005-10-18
ok this is weird.  if i do a 'single' boot mode the root password works, but in Ubuntu the root password doesnt work.  how do i fix this?!

---

### Post by Deathcon_1 on 2005-10-18
what would be the command to add it to ~.bashrc

---

### Post by Deathcon_1 on 2005-10-18
[QUOTE=adwait]1)Wierd...how are you setting the root password?
You can use
```
sudo passwd
```
2)Use
```
sudo rcconf
```
Uncheck the box against gdm using the spacebar and and ok your way out.
3)That's not a very good idea and I am not sure how that can be done in bash. In the GUI login you can do that throught
```
sudo gdmsetup
```
4)Add the line
```
/etc/lampp/lampp start
```
to a file. Make the file executable using
```
chmod +x <filename> 
```
Copy it to the /etc/init.d/ directory. 
Again run rcconf (as described above) and check the box against the filename of the file you just created
5)I'd be having my secretary writing this while I enjoy with my extremely sexy girfriend and a chilled drink. if I had that. There are somethings OSS can't do, for everything else......there's Ubuntu ;)[/QUOTE]

sorry for the massive quote, ignore my other posts please as i've solved those on my own.  
```
sudo rcconf
```
     returns:
```
sudo: rcconf: command not found
```
 what do i do from here? i tried putting it in the bash.bashrc and it worked - provided i was logged in as root and didnt mind each terminal i opend up to have lamp try to start up again.  i just need it to start when the computer is first turned on

---

### Post by adwait on 2005-10-19
Instal rcconf
```
sudo apt-get install rcconf
```

---

