---
title: "adding new file to /usr/share/backgrounds"
date: 2010-04-24
forum: Desktop Environments
---

### Post by idrivefast on 2010-04-24
I would really love to add a different picture to the usr/share/backgrounds folder so I can change the login screen picture. How do I do that?

---

### Post by SnickerSnack on 2010-04-24
I'll give instructions for moving the picture below, but first, I don't think that will allow you to change the login picture.  For that, you need to open a terminal and do

```
user@computer:~$ sudo -u gdm dbus-launch gnome-appearance-properties
```

This opens the appearance manager under the user "gdm" (which controls the login screen), and you can change the picture.  The picture need not be in /usr/share/backgrounds; it can be any picture on your system, I think.

But, if you don't know how to move a file from the command line, now's a good time to learn:

From a terminal, go to the place where the picture you want is:

```
user@computer:~$ cd Pictures
```

Then copy (or move) the picture to the new directory:

```
user@computer:~/Pictures$ sudo cp picture.jpg /usr/share/backgrounds

or

user@computer:~/Pictures$ sudo mv picture.jpg /usr/share/backgrounds
```

(Use sudo only because you need root privileges to copy to that folder.  That also makes root the owner of that new file.  You will usually not use sudo to move files around in your home directory.)

Now it's there.  Verify that with

```
user@computer:~/Pictures$ ls /usr/share/backgrounds

or

user@computer:~/Pictures$ ls /usr/share/backgrounds | grep picture.jpg
```

---

### Post by ronnielsen1 on 2010-04-24
I usually do sudo nautilus and then work in gui

---

### Post by idrivefast on 2010-04-24
And this is why this OS is so great. Those are both perfect answers. I love to learn the command line and I love short cuts. Thanks guys.

---

### Post by jonny163 on 2010-04-27
The first option worked for me, about time I learned how to move with the command line as well. Thanks

---

### Post by xmanx on 2010-10-16
> **SnickerSnack said:**
> But, if you don't know how to move a file from the command line, now's a good time to learn:

From a terminal, go to the place where the picture you want is:

```
user@computer:~$ cd Pictures
```Then copy (or move) the picture to the new directory:

```
user@computer:~/Pictures$ sudo cp picture.jpg /usr/share/backgrounds

or

user@computer:~/Pictures$ sudo mv picture.jpg /usr/share/backgrounds
```(Use sudo only because you need root privileges to copy to that folder.  That also makes root the owner of that new file.  You will usually not use sudo to move files around in your home directory.)

Now it's there.  Verify that with

```
user@computer:~/Pictures$ ls /usr/share/backgrounds

or

user@computer:~/Pictures$ ls /usr/share/backgrounds | grep picture.jpg
```
It works.
Thanks

---

