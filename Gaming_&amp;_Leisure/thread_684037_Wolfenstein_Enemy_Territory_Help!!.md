---
title: "Wolfenstein: Enemy Territory Help!!"
date: 2008-01-31
forum: Gaming &amp; Leisure
---

### Post by ondo311 on 2008-01-31
Ok, i am an extreme noob i guess, because I looked at all the stuff on this and still cant figure it out

its bad i dont even know where to begin, so far all i've done is download the *et-linux-2.55.x86.run* I've tried opening by clicking, and through the terminal

it is located on my desktop if that helps ya.. Thanks!

---

### Post by nat6138 on 2008-01-31
In the terminal:

chmod +x et-linux-2.55.x86.run

./et-linux-2.55.x86.run

You also need libgtk1.2.

---

### Post by ondo311 on 2008-01-31
```
matthew@matthew-laptop:~$ chmod +x et-linux-2.55.x86.run
chmod: cannot access `et-linux-2.55.x86.run': No such file or directory
matthew@matthew-laptop:~$ ./et-linux-2.55.x86.run
bash: ./et-linux-2.55.x86.run: No such file or directory
matthew@matthew-laptop:~$ 

```

thats what i get, i dont know if thats right or not

also i did install the *libgtk1.2.*

---

### Post by nat6138 on 2008-01-31
If it's on your desktop, change to that directory.

cd /home/matthew/Desktop

---

### Post by ondo311 on 2008-01-31
oooh thats what everybody ment by changing that ok.. bu tnow I get this....

```
matthew@matthew-laptop:~/Desktop$ chmod +x et-linux-2.55.x86.run
matthew@matthew-laptop:~/Desktop$  ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
Sorry.
/home/matthew/.setup10513: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting

```

I guess i could go to that website? or ... i'm just confused lol thanx for ur help btw

---

### Post by ondo311 on 2008-01-31
i guess the problem is the:
```
/home/matthew/.setup10782: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

```

---

### Post by iceportal on 2008-01-31
You need to install as root. Type the following:

```
sudo su
```

Type in your password, and it'll make you root. Then:

```
./et-linux-2.55.x86.run
```

That should get you on your way.

---

### Post by ondo311 on 2008-01-31
naw still getting the same thing

```
matthew@matthew-laptop:~/Desktop$ sudo su
root@matthew-laptop:/home/matthew/Desktop# ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup11225: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting
root@matthew-laptop:/home/matthew/Desktop# 

```

---

### Post by ondo311 on 2008-01-31
OH OH!! lol how bad i just realized while re-reading those that i didnt install the whole libgtk package, only part of it

sorry about all that guys and thanks for your help!!

i'm sure I will be back for more :(

---

### Post by iceportal on 2008-01-31
You need to install libGTK.

```
sudo apt-get install libgtk1.2
```

---

### Post by ondo311 on 2008-01-31
cool thankyou... now i just have to fix my sound :(

---

