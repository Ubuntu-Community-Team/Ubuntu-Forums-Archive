---
title: "Root? and ME?"
date: 2005-12-30
forum: General Help
---

### Post by s_spiff on 2005-12-30
Hey, I had posted about this , but now simply can't find the thread, so posting again, with a hope that it won't cause so much inconvinience. I installed Ubuntu BB 5.10 yesterday night. I put only one user on it. Now to setup my net connection I have to install a package called rp-pppoe, and I have to extract this into the /usr/local/src. Everytime I try to extract it into that folder, I end up getting an error saying I do no have permission to write into that folder. I have the package on a cd, its a 207kb package. Write now I'm mailing via MS XP. Wanted to know, where can a newbie actually get a through explanation of Ubuntu? As simple it is compared to the few other distro's I've tried, its nonethelss difficult for a total noob like me.

---

### Post by Jammy_Stuff on 2005-12-30
If the package is on a CD, go to System > Administration > Synaptic Package Manager and it will ask for the root password (same as the default user's). Then go to Edit > Install from CD (or similar) and it should work.

---

### Post by erikpiper on 2005-12-30
You need root permissions. Root is the administrator. NEVER do anything non neccisary as root. You can bork your system, and webbrowsing as root is a BIG no-no. 
In ubuntu become root by putting "sudo" before the command you want to run as root, and entering your password. I am not sure how to start a program in gnome as root.. You can log on to gnome as root by typing in a console:

passwd root

And entering a root password. Then you can log in as root using that password. HOWEVER, most do not reccomend that, but if you do the minumum amount of things posible as root, you are fine.



Did any of that make any sense at all??

---------------------------

EDIT: Try the above, or type into a terminal:

sudo apt-get install rp-pppoe

They are the not the same thing- Mine would install from the internet. You can do the same in synaptic, exept the typing way is faster. A LOT simpler than compiling..

---

### Post by s_spiff on 2005-12-30
LOL, no. But the second reply did. I have no clue about command prompt, though I would like to learn. Anychance wher I can get this stuff? as in learn about this? And thanks for the ultra quick reply! this is gives me one reason to shift off into Linux, MS Beta people/users took 2 to 3 days to reply to my queries! How noob! Thnx anyways

---

### Post by erikpiper on 2005-12-30
It worked?? Wow.. I tried and didnt find the package, but my system seems to be hoplessley broken anyway.. :P

You want to learn command line?? Cool! Read this post. It gives a short intro.
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)


Reading forums is how I learned all I know about linux!

---

### Post by ren wins on 2005-12-30
i recently learned that if you want to browse your filesystem as root you type
sudo nautilus
which will pop open a nautilus window for you to browse files in
i dont know if it works for other programs that way... i dont really wanna screw with it :)

---

### Post by erikpiper on 2005-12-31
Go here. A thread I asked for guides. :P
[http://www.ubuntuforums.org/showthread.php?t=110509](http://www.ubuntuforums.org/showthread.php?t=110509)


sudo programname will open it in root. (Knocks self on head) Duh!

---

### Post by s_spiff on 2005-12-31
[quote=ren wins]i recently learned that if you want to browse your filesystem as root you type
sudo nautilus
which will pop open a nautilus window for you to browse files in
i dont know if it works for other programs that way... i dont really wanna screw with it :)[/quote]
I tried that, and could finally extract the package into the urs/local/src folder, by modifying the properties of the folder. Anyways, this was simple, but now in the terminal I gotta go into the folder which is urs/local/src/rp-pppoe-3.7 via the terminal, and when i use the cd commant, it says no such directory exists, where as in the gui, I can clearly see the folder and its contents [ which were put there as a root ] How do I get into this folder?

---

### Post by soulestream on 2005-12-31
cd /usr/local/src 

you probably left off the first /

check you spelling or tab complete

soule

---

### Post by s_spiff on 2005-12-31
Nopes, didn't forget the first /. Thanks.

---

### Post by erikpiper on 2005-12-31
If there is only one possible file or directory with the letters you have already typed, hit tab. It will complete them for you. Great for long filenames!

---

