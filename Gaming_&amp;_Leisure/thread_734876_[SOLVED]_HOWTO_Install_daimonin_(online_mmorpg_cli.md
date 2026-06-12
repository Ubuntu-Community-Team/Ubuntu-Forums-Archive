---
title: "[SOLVED] HOWTO: Install daimonin (online mmorpg client)"
date: 2008-03-25
forum: Gaming &amp; Leisure
---

### Post by Tomatz on 2008-03-25
Below is a guide to compile daimonin an online mmorpg game.


[http://www.daimonin.com/](http://www.daimonin.com/) (link to home page)


1. Download daimonin

2. Extract and put the **client** folder in your **home** folder

3. Copy and paste the following in a terminal and press enter:

[B]sudo apt-get install libsdl1.2debian libsdl1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-image1.2 libsdl-image1.2-dev libphysfs-dev libcurl3-gnutls-dev
[/B]
5. Copy and paste the following in a terminal and press enter:

**cd ~/client/make/linux**

6. In the terminal type:

[B]./configure
[/B]
7. Then

**make**

8. And finally (**without** sudo):

**make install **

You should now have a fully working daimonin client :)

Just browse to your **home** folder then open the **daimonin-0.9.7** folder then double click/execute the **daimonin** executable.

You can add a menu entry accordingly.

:guitar:

---

### Post by hiro nakamatty on 2008-03-25
oh my goodness!!!!!! it works!!!! Tomatz, you are amazing!!!!!!

thank you so much!!!!!!! thank you thank you thank you!!!!!!


but 1 last thing lol... it won't allow me to connect to the server lol, but i can try figure that out myself...... lol

---

### Post by Tomatz on 2008-03-25
I got your pm :)

But im confused now :confused:

You can connect now cant you?

---

### Post by Tomatz on 2008-03-25
Now SOLVED

---

### Post by llamakc on 2008-03-25
It should also be noted that these instructions are provided by the package in the README.debian file.

---

### Post by Tomatz on 2008-03-25
> **llamakc said:**
> It should also be noted that these instructions are provided by the package in the README.debian file.


Not really as the dependency's in the readme aren't ubuntu specific (eg libsdl1.2 / libsdl1.2debian)
and if you did use the readme (eg libcurl3-dev instead of libcurl3-gnutls-dev) you could run into problems with other applications. Also the readme is kind of confusing for a new user.

Cheers

:mad:

(i can see why you have only been thanked twice :( )

---

### Post by Hello_World on 2009-06-01
well, if you should run into problems (like i did), try to

1) copy the client folder in YOUR home, meaning
/home/<user>

2) use sh ./configure if ./configure doesn't work

---

### Post by Viau on 2010-05-26
> **Tomatz said:**
> Below is a guide to compile daimonin an online mmorpg game.


[http://www.daimonin.com/](http://www.daimonin.com/) (link to home page)


1. Download daimonin

2. Extract and put the **client** folder in your **home** folder

3. Copy and paste the following in a terminal and press enter:

[B]sudo apt-get install libsdl1.2debian libsdl1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-image1.2 libsdl-image1.2-dev libphysfs-dev libcurl3-gnutls-dev
[/B]
5. Copy and paste the following in a terminal and press enter:

**cd ~/client/make/linux**

6. In the terminal type:

[B]./configure
[/B]
7. Then

**make**

8. And finally (**without** sudo):

**make install **

You should now have a fully working daimonin client :)

Just browse to your **home** folder then open the **daimonin-0.9.7** folder then double click/execute the **daimonin** executable.

You can add a menu entry accordingly.

:guitar:

thank you so much my friend!!

---

### Post by GeneZ on 2010-05-27
i dont understand. how do i install a .package file. @_@ noob here.

---

