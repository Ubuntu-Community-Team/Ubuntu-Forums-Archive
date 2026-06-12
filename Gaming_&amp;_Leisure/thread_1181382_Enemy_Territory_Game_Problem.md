---
title: "Enemy Territory Game Problem"
date: 2009-06-07
forum: Gaming &amp; Leisure
---

### Post by Matt_Johnson on 2009-06-07
I have recently downloaded this game called wolfensteins: Enemy Territory.
it's a .run file so I went to properties and clicked allow executing file as a program and then ran it. It says
```
 It is recommended to install as the super user please enter the root password or hit enter to continue as is.
Password:
```
so I entered my password and it said:
```
 su: Authentication Failure
```
I'm really confused on what to do. Please help!

---

### Post by Jeneral22 on 2009-06-08
There is a great tutorial on installing Enemy Territory. Just search for Enemy Territory.

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

Use the above link to get it installed.

---

### Post by crazyfuturamanoob on 2009-06-08
Edit: nvm

---

### Post by K.Y.A on 2009-06-08
> **Matt_Johnson said:**
> I have recently downloaded this game called wolfensteins: Enemy Territory.
it's a .run file so I went to properties and clicked allow executing file as a program and then ran it. It says
```
 It is recommended to install as the super user please enter the root password or hit enter to continue as is.
Password:
```so I entered my password and it said:
```
 su: Authentication Failure
```I'm really confused on what to do. Please help!

It will still work. Just go along with it. Does it crash after that? If it does, run:

```
sudo apt-get install libgtk1.2 libgtk1.2-common
```Then run the .run file again. It will still fail at password, but it will work anyway..... I think the solution is to just run the .run as root.


EDIT:
You will also have problems with sound. To run the game with sound, run sudo -i , then run this:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by Matt_Johnson on 2009-06-08
thanks for the help

---

