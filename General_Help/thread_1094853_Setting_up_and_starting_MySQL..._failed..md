---
title: "Setting up and starting MySQL... failed."
date: 2009-03-13
forum: General Help
---

### Post by Roasted on 2009-03-13
I'm trying to install FOG... a popular open source imaging solution for businesses and school districts. 

When I try to install FOG on Intrepid 8.10, it goes through it's little questionaire thing and I answer accordingly. Then it checks all of the packages and hits "configuring services." 

* Setting up fog user... Exists
* Setting up and starting MySQL... Failed!

I don't know anything about MySQL, but I've reinstalled MySQL client + server and rebooted and also restarted the MySQL service via /etc/init.d/whateverthiscommandwas, I forget it now.

What can I do?

---

### Post by ju2wheels on 2009-03-13
Based on the way the installer looks like its working, its expecting that MySQL will not have been installed by you before hand and that it would kick off the install and configuration of MySQL. So I would recommend fully uninstalling MySQL and running your install script again. Its most likely failing because it has no way to determine that you already have it installed so when it attempts to install it, the MySQL instal fails.

Note that ive never used FOG, im just looking at their wiki to see how it works...

---

### Post by CanHasDIY on 2009-04-16
I had the same problem, until I realized that I was trying to install FOG without root privileges.


To fix the MySQL issue, I uninstalled MySQL, then reinstalled FOG w/ sudo.

> sudo apt-get remove mysql 
sudo apt-get autoremove
sudo ./installfog.sh

let me know if it works for you.

---

### Post by Roasted on 2009-04-16
Somehow I didn't have it installed already and the installer wasn't picking it up, so it just errored out.

I ran sudo apt-get install mysql.

Re-ran the installer, it passed mysql, but the next thing wasn't installed. So I ran apt-get install for the next thing.

I think something was borked with Ubuntu all together because I currently have FOG running on 3 computers, and all 3 of them didn't give me any errors. I have fog on my laptop, kind of as a mobile server, a desktop for the mass storage of images, and my home computer for when clients bring their computer over to me - I make an image of their computer before I touch it so I can restore it to its original state if I goof something up.

But I've been using FOG for quite some time and I'm very impressed. Tomorrow is the "official test" of it though. Up until now the max amount of computers I've cloned was 8 laptops, to which I pushed a 35 gig image to 8 laptops over a gigabit switch via unicast in a half hour flat.

Tomorrow I have to image 30 computers, so I can do about 2 dozen at a time tomorrow, so I'm excited to see how FOG does when my switch is maxed out.

Thanks for the input, though!

---

