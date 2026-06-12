---
title: "How to install a racing game torcs from a package"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by Taras on 2008-05-10
Basically how can i install this game from a package, i have already extracted the files, in my screen print you can see it. 

Can anyone please guide me through the terminal or give me the commands in turns so that i can make a easy install thank you

---

### Post by Ozor Mox on 2008-05-10
That looks like you're trying to compile the source code. This version of TORCS is in the repositories, simply do:

```
sudo apt-get install torcs
```

If you really want to compile what you have there, you need to cd to the torcs-1.3.0 directory and run these three commands one after the other:

```

./configure
make
sudo make install

```

The configure command might throw errors of missing dependencies, and you will need to install what it asks you to install.

Using the repositories is much easier though, I only compile if there is a newer version I want that isn't in the repos.

---

### Post by Perfect Storm on 2008-05-11
Aye, it's in the synaptic package manager.

Here's a guide (should also work with 32-bit), if you want to compile it: [http://gaming.gwos.org/doku.php/guides:64bit:torcs](http://gaming.gwos.org/doku.php/guides:64bit:torcs)

---

### Post by Taras on 2008-05-11
Cheers guys

---

### Post by ejaz.sayyed@gmail.com on 2009-03-11
Hi,
I had to face lots of errors during installtion of TORCS.
It was a very painful process.

I had downloded the the "torcs-1.3.1.tar.bz2" file from my office, since internet connection at my home is very slow.

Then I started the installtion using 
./configure
make 
make install
make datainstall

but during the first two steps, I faced lot of issues
i..e. 
./configure asked me to install lot of other packages/programs

such as OpenGL, alut, freelut , cmake , plib etc..

and then make had a problem of shared libraries libplibssg.a

I issued the 
sudo apt-get install libx11-dev libxmu-dev xserver-xorg-dev libxxf86vm-dev freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev plib1.8.4-dev libalut-dev  libpng12-dev


pointed out in the 

[http://gaming.gwos.org/doku.php/guides:64bit:torcs](http://gaming.gwos.org/doku.php/guides:64bit:torcs)

this is very useful while compiling and making the TORCS game.

Now, I am able to race , but after lot of lot of research since I was new to linux.

This is sometimes very frustrating......
I think there should be the facility to install the related packages automatically when we configure the TORCS using the .bz2 file.

or there should be the script provided to install all the related packages and should be documented.
this will help users who migrated from windows in installing this game in one day, otherwise it wil take longer.

BTW, game is really good and I think I will enjoy it.
Its free!!


Thanks
- Ejaz

---

### Post by jacksaff on 2009-03-11
> **ejaz.sayyed@gmail.com said:**
> Hi,
I think there should be the facility to install the related packages automatically


That's what apt does...
sudo apt-get install torcs

You can also use apt-build to download the source code and compile it and any dependencies automatically.

Both of these require you to use the repository version of torcs which may not be the latest.

The torcs people can't do this for you with their latest version because they don't know which linux distro you will be using.

---

### Post by drsek2 on 2009-05-03
Guys, can anyone tell me what could be wrong with the torcs I have installed? I can't control any of the cars; when I start a new race, either I get the car running alone and the others crash at the very beginning (I saw them in lap#2 :)) or the cars are on starting grid, then I get the ready/set/go stuff and the cars simply start without me having any control on any of them. It's quite strange because when I played for the first time it was working; then I started to change cars, races and so on and at some point I could not control any cars. What could be wrong? I have 1.3.0 version of torcs.
Thanks!

---

### Post by Coolraj on 2009-07-25
Hi,

  I am absolutely new to Ubuntu. I have download torcs_1_3_1_setup.exe (around 130MB) and not sure how to install and run. Can anyone help please?

Regards

---

### Post by Shazaam on 2009-07-25
Coolraj...
An .exe will only run on Windows or with a program such as Wine. You need to dowload the correct LINUX torcs installation file or install it through Synaptics (or with the terminal using the apt-get command as posted earlier).

---

### Post by Coolraj on 2009-07-26
Thanks Shazaam. Any advise on how do we include in Synaptics?

---

### Post by Shazaam on 2009-07-28
Version 1.3.0 IS currently available in Synaptic.
1. Open Synaptics (System>Administration>Synaptics Package Manager).
2. Go to Settings>Repositories and make sure the Main, Universe, Restricted and Multiverse boxes are checked in the Ubuntu Software tab.
3. Click the reload button.
4. Either search for torcs or scroll down the list for it.
5. Enjoy!

---

### Post by Coolraj on 2009-08-01
Thanks Shazaam for your help again. This seems to be a wonderful community

---

### Post by Solrac924 on 2009-08-31
how long does it take for new versions to be in Synaptic?
for example, TORCS 1.3.1 has been out since December 16, 2008 yet my Synaptic Manager says the latest is 1.3.0. will it be anytime soon?

---

