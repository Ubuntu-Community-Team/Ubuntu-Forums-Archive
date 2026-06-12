---
title: "Ubuntu 12.04 &amp; Cinnamon"
date: 2012-09-18
forum: Desktop Environments
---

### Post by GeForce 9500GT on 2012-09-18
Hi everyone,  Did anybody tried this combination? Or has this combination working on his/her system? And what is the general opinion about Ubuntu with Cinnamon?

---

### Post by hawthornso23 on 2012-09-18
I am interested in the answer to this question also. My understanding is that this is can be done by just  adding a ppa. Is it that simple. I want Cinnamon as it looks like the right approach, but if it is going to be difficult on ubuntu I'll have to look at installing mint.

---

### Post by vasa1 on 2012-09-18
> **GeForce 9500GT said:**
> Hi everyone,  Did anybody tried this combination? Or has this combination working on his/her system? And what is the general opinion about Ubuntu with Cinnamon?
Has the pulldown arrows problem been solved by switching to Cinnamon? That was quite a puzzle.

---

### Post by GeForce 9500GT on 2012-09-19
> **vasa1 said:**
> Has the pulldown arrows problem been solved by switching to Cinnamon? That was quite a puzzle.
 
Nope.

---

### Post by Buntu Bunny on 2012-09-19
I tried it but Cinnamon seemed buggy. I eventually uninstalled it and tried something else.

---

### Post by GeForce 9500GT on 2012-09-20
> **Buntu Bunny said:**
> I tried it but Cinnamon seemed buggy. I eventually uninstalled it and tried something else.
 
What kind of problems did you had?

---

### Post by bouncingwilf on 2012-09-20
Been using Mint Maya 13 for a few weeks now which is basically 12.04 + cinnamon ( and a few other mods)  - yet to find a problem.


Bouncingwilf

---

### Post by GeForce 9500GT on 2012-09-20
> **bouncingwilf said:**
> Been using Mint Maya 13 for a few weeks now which is basically 12.04 + cinnamon ( and a few other mods) - yet to find a problem.
Linux Mint is created to be even more user friendlier than (..)buntu. It looks good and feels good, i used it for a while, but for me somehow it feels also a bit bleary. And after a while it also give me the impression of not being that stable at all. Can't really point out exactly what is was, but it didn't felt that rocksteady as (..)buntu does.
 
But my overall opinion is that is is a good operating system, easy to use and easy to learn. Linux Mint is more for novice users than for experienced users.
 
There are 2 good things with Mint i really do like: Mate and Cinnamon. Really good and easy to use desktop environments! Better than Unity.

---

### Post by Buntu Bunny on 2012-09-21
> **GeForce 9500GT said:**
> What kind of problems did you had?

Right click didn't work. Made it difficult to do anything. I could have tried to have that solved in the forums I suppose, but I was just trying out alternatives to Unity. I really liked Xfce, so I just stuck with that.

---

### Post by Buntu Bunny on 2012-09-21
> **GeForce 9500GT said:**
> 
There are 2 good things with Mint i really do like: Mate and Cinnamon. Really good and easy to use desktop environments! 

I wondered about Mint. What is the difference between Mate and Cinnamon?

---

### Post by vasa1 on 2012-09-21
> **Buntu Bunny said:**
> I wondered about Mint. What is the difference between Mate and Cinnamon?
[http://www.linuxbsdos.com/2012/06/02/mate-vs-cinnamon/](http://www.linuxbsdos.com/2012/06/02/mate-vs-cinnamon/)

---

### Post by GeForce 9500GT on 2012-09-21
> **Buntu Bunny said:**
> I wondered about Mint. What is the difference between Mate and Cinnamon?
 
You can read everything [here]("http://en.wikipedia.org/wiki/Cinnamon_(user_interface)") and [here]("http://en.wikipedia.org/wiki/Mate_desktop").

---

### Post by Buntu Bunny on 2012-09-21
Vasa1 and GeForce 9500GT, thanks!

---

### Post by RikoW on 2012-09-23
Coming back to the original question, I suppose you could just add the Mint repos and install Cinnamon into your Ubuntu installation:

```
deb http://packages.linuxmint.com/ maya main upstream import

```

```
sudo apt-get install cinnamon
``` 

should do the trick. The base system of Mint 13 is Ubuntu 12.04 anyway. You will then be able to select Cinnamon from the session section windows on the login screen.

The above would install Cinnamon 1.4 while 1.6 was recently released. That may fix some of the problem/bugs/instabilities people see or feel :)

V1.6 of cinnamon can be installed via this repos:

```
 sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
```

Of course, you can go the other way to (in fact, that's what I did):

1) install Mint 13
2a) install unity
2b) install gnome-shell

Work with all of them until you know which one you like best :)

Cheers,
      Riko

---

### Post by SuperFreak on 2012-09-23
I have been using Cinnamon 1.6 on my Ubuntu 12.04 machine for about a week. I have had no instability problems (which I had with 1.4). I really like the interface which is much more crisp and professional compared to xfce (which is my previous DE)

---

### Post by wheeze on 2012-09-23
> **RikoW said:**
> The above would install Cinnamon 1.4 while 1.6 was recently released. That may fix some of the problem/bugs/instabilities people see or feel :)

V1.6 of cinnamon can be installed via this repos:

Actually you can install Cinnamon 1.6 using Mint's repos by adding the **romeo** branch to their source list.

```
deb http://packages.linuxmint.com/ maya main upstream import **romeo**
```

Update apt and you'll have inn 1.6 available. Obviously, this works for Mint 13 as well :D

PS - Don't forget to install Mint's keyring, too, for error-free updates.

```
sudo apt-get install linuxmint-keyring
```

---

### Post by hwyckoff on 2012-09-23
I installed Cinnamon on Ubuntu 12.04 and like the result.  I was able to install it in a matter of minutes.  So should you [be able to install it quickly], assuming you have a decent Internet speed.  

Here's the method I followed: go into Terminal and enter these commands.

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```


It's that easy.  When you're done with the code, log out. When you log back in, change the default desktop from whatever you have to Cinnamon.

---

