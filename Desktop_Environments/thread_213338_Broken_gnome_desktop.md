---
title: "Broken gnome desktop"
date: 2006-07-11
forum: Desktop Environments
---

### Post by shazbot on 2006-07-11
Have broken gnome and when I boot to it just get a blank screen and the mouse arrow, I get the small nautilus window starting, showing the start up programs  and the music but then just the blank screen

gnome works in another account so its due to my setting somewhere, 

Have tried re installing all gnome files to no avail, can anyone help me please

KDE works fine under my account but I would prefer to go back to gnome

have tried fail safe, same problem and fail safe terminal using gnome-session which gives me badDevives, invalid or uninitialized imput device 166

---

### Post by shazbot on 2006-07-11
Okay seemed to have half fixed it did a apt-get install gnome abd seemed to works ok BUT

When I looke under the themes 'system, admin, themes) they all have a question mark over them, so I dont dare touch anything, how do I get all the themes to be active and installed complety ?? reinstalling the thru synapics doesnt do anything

---

### Post by kaamos on 2006-07-11
You could try logging out and doing this:
[http://ubuntuforums.org/showpost.php?p=712740&postcount=2](http://ubuntuforums.org/showpost.php?p=712740&postcount=2)

Hope it helps.

---

### Post by shazbot on 2006-07-11
This seem a littl difficult as am a newbie, I just need to re install the themes as they seem to be broken, but synapices doesnt do it it even if I do a complet delete and reinstall again, I get the same thing the icon of the thme with a big question mark in it, in which folder are they installed in

I also tried a apt-get instal gtk engine but no avail


thanks

---

### Post by Meersie on 2006-07-11
Just out of curiosity.
Did you remove/install some programs before this happened?

I ask because I had the same thing yesterday.
I could log in with username and passworrd and then got stuck on a blank screen with just the mousecursor.

I reinstalled eventually because I couldn't find a solution, which wasn't bad since I only started working with Ubuntu over the weekend - more like annoying because I had everything set up like I wanted to.

---

### Post by shazbot on 2006-07-11
well I dont think so, the last I installed was KDE so I belive that it aws that ....

---

### Post by shazbot on 2006-07-11
At last got it all fixed (I hope) as disinstalled and re installed just about everything and update came along for lasted kernel in Ubuntu, so all works fine, now my question is My default boot is Gnome but when I switch of and the computer the logo Kububtu show firts before the log in screen which annoys me, how do i get  the Ubuntu log in / out screen

---

### Post by panurge77 on 2006-07-11
For getting rid of the blue boot screen:
sudo apt-get remove kubuntu-usplash-artwork

---

### Post by shazbot on 2006-07-11
thats a no go :(
Get a E: Couldn't find package kubuntu-usplash-artwork

---

