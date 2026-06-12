---
title: "Problems with Frostwire and JRE"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Maheriano on 2006-08-10
I ran ```
sudo update-alternatives --config java
```but I don't have the SUN java installed yet. I need to start from scratch, where do I download it, how do I download it, how do I install it, how do I enable it? I've been searching since last night, been at it for about 2 hours in total. Thanks.

---

### Post by cstudent on 2006-08-10
Make sure you have the universe and multiverse repos enabled.
Install sun-java5-bin.
Run update-alternatives again.

---

### Post by Maheriano on 2006-08-10
Sorry, all I heard was 

[IMG]http://images.google.ca/images?q=tbn:gsiO14nTJH2isM:http://www.gamesblog.it/uploads/pacman.jpg[/IMG]

WOCKA! WOCKA! WOCKA!

How do I do that?

---

### Post by navymom on 2006-08-11
First go here:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu)

Then do this:

> sudo update-alternatives --config java

Select the 3rd option

---

### Post by cstudent on 2006-08-11
You don't need to use Automatix or Easy Ubuntu to do this.

Open Synaptic. (System menu > Administration > Synaptic Package Manger)
Select the Settings menu in Synaptic and then the Repositories menu.
Make sure all the repositories listed have a check beside them.
Close the Repo menu.
Hit the Reload button near the upper left.
After it finishes do a search for sun java.
Install the pacakge sun-java5-bin.
Close Synaptic when it's finished installing and open a terminal.
Run update-alternatives again and select the number for sun-jave. Hit Enter.

---

