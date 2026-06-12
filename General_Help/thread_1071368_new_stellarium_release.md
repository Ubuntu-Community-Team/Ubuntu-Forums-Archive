---
title: "new stellarium release"
date: 2009-02-16
forum: General Help
---

### Post by MichaëlVD on 2009-02-16
[Stellarium]("http://www.stellerium.org/") is a great program to help you navigate the sky. It helps me learn the constellations when I go out and watch the stars.

A new version was just released, and this version is (obviously) not yet in the repo's. You can download the source on the website.

However, I do not have sufficient harddrive space left on my eee pc to install all dependencies to compile stellarium.

Therefore, I would really appreciate it if someone could share a PPA or a .deb of this program.

Thanks!

---

### Post by rmls on 2009-02-20
Hi There

edit: I've updated/created a deb package for the new 0.10.2 available here about 34 mb:

[http://www.ramblingmind.com/ubuntu/stellarium_0.10.2_u8.10_i386.deb]("http://www.ramblingmind.com/ubuntu/stellarium_0.10.2_u8.10_i386.deb")

I followed the instruction posted here (thanks to dinsdag):

[http://ubuntu-install.blogspot.com/2009/02/how-to-create-deb-file-for-stellarium.html]("http://ubuntu-install.blogspot.com/2009/02/how-to-create-deb-file-for-stellarium.html")

you'll have to add a menu short cut & if you might wish to add to PATH in 
your home .bashrc described here:

[http://ubuntuforums.org/showthread.php?t=1059949&highlight=Stellarium]("http://ubuntuforums.org/showthread.php?t=1059949&highlight=Stellarium")

The .deb file should install to /usr/share/stellarium/  
 /bin & /share

It is my second attempt at creating a .deb package so I hope it works 
for you :) or at least until 0.10.2 is added to the official repos.

cheers
rml

---

### Post by Rhubarb on 2009-02-20
> **MichaëlVD said:**
> [Stellarium]("http://www.stellerium.org/") is a great program to help you navigate the sky. It helps me learn the constellations when I go out and watch the stars.

This is the correct URL for the site:-
[http://www.stellarium.org/](http://www.stellarium.org/)

Thanks for the info, I'll have to try this new version out :)

---

### Post by Rhubarb on 2009-02-25
Wow, the new stellarium release does indeed look very nice.
The new interface looks very nice and smooth, and the night mode also changes the atmosphere a reddish colour too :)

I am impressed, I think I'll have to take a 360 degree panorama at my place and import that into stellarium soon :D

---

### Post by Gizenshya on 2009-02-25
i386? :'(

can you make an x86 version :D

---

### Post by Rhubarb on 2009-02-25
> **Gizenshya said:**
> i386? :'(

can you make an x86 version :D

i386 is x86
... unless you mean x64, in which case you'd be better off compiling it yourself (or find someone to do it for you).

I don't have a 64bit computer here with me at the moment, so I can't make up a nice deb package for you.

---

### Post by jespdj on 2009-02-25
The older version of Stellarium (0.9.1) is in the Ubuntu repository for 32-bit as well as 64-bit.

There is already a [version 0.10.0 for Jaunty](https://launchpad.net/ubuntu/jaunty/+source/stellarium).

Also see this: [Installing Stellarium 0.10.0 from source](http://ubuntuforums.org/showthread.php?t=936998).

---

### Post by dotancohen on 2009-02-26
> **rmls said:**
> I created a deb package for 0.10.1 available here about 34 mb:

Thank you! This seems to include the Qt dependency! Great!

---

### Post by rmls on 2009-03-01
Thanks dotancohen, I'm glad it worked for you :)
it is a amazing piece of software, the developers have
done a great job.

---

### Post by Lupi on 2009-03-11
> **rmls said:**
> Hi There

I created a deb package for 0.10.1 available here about 34 mb:

[http://www.ramblingmind.com/ubuntu/stellarium_0.10.1_u8.10_i386.deb]("http://www.ramblingmind.com/ubuntu/stellarium_0.10.1_u8.10_i386.deb")

I followed the instruction posted here (thanks to dinsdag):

[http://ubuntu-install.blogspot.com/2009/02/how-to-create-deb-file-for-stellarium.html]("http://ubuntu-install.blogspot.com/2009/02/how-to-create-deb-file-for-stellarium.html")

you'll have to add a menu short cut & if you might wish to add to PATH in 
your home .bashrc described here:

[http://ubuntuforums.org/showthread.php?t=1059949&highlight=Stellarium]("http://ubuntuforums.org/showthread.php?t=1059949&highlight=Stellarium")

The .deb file should install to /usr/share/stellarium/  
 /bin & /share

It is my first attempt at creating a .deb package so I hope it works 
for you :) or at least until 0.10.1 is added to the official repos.

cheers
rml

I reached this point but I don't know what to do to run the program or how to put a shortcut in the menu.

---

### Post by Rhubarb on 2009-03-13
> **Lupi said:**
> I reached this point but I don't know what to do to run the program or how to put a shortcut in the menu.

Firstly, we should make a link to the binary executable directory, to make the application easier to run.

Open up a terminal:-  Application --> Accessories --> Terminal
```
sudo ln -s /usr/share/stellarium/bin/stellarium /usr/bin/
```
It'll prompt you to enter in your password.

Now to run stellarium, just run:-
```
stellarium
```

This can be added to your menu by using the Main Menu Editor:
System --> Preferences --> Main Menu

---

### Post by Lupi on 2009-03-13
Thank you. It works. :)

---

### Post by rmls on 2009-04-03
Just to let you know I've update the deb package for stellarium to 
0.10.2 & edited the my first post link.

Cheers
rml

---

