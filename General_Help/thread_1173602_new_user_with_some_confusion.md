---
title: "new user with some confusion"
date: 2009-05-29
forum: General Help
---

### Post by candymanmike on 2009-05-29
i've had ubuntu installed within windows for several months now. and i decided to just get rid of xp altogether and go strictly linux. i'm running 8.10 and so far i love it. just one annoyance/confusion. i have been trying to install limewire for 3 days now. everytime i do, i get an error message telling me i can only run one admin tool at a time and to shut down the other one. however i don't see another one running when i open system monitor. a friend suggested i do a restart and go straight to the install without touching anything. but i still get the same error. it's driving me insane! is there a name i should be looking for in the process list that i may not know, or a prompt command of some sort. perhaps an alternate way to install limewire? anything will help at this point. i'm starting to lose my mind! here's a screenie of the error message..
[IMG]http://i4.photobucket.com/albums/y103/miketheevil1/installer-error.png[/IMG]

---

### Post by JohnB-nbr on 2009-05-29
Welcome to the forum,

You could try "sudo dpkg --configure -a" in a terminal..

---

### Post by LepeKaname on 2009-05-29
Any process named "apt*" may be related... I'm not sure, but It may be the automatic update notifier...

---

### Post by pastalavista on 2009-05-29
I'd try in terminal ```
sudo apt-get update
``` and then ```
sudo apt-get dist-upgrade
``` and when they are finished (when the update icon is gone from the notification area) then run your installer.

---

### Post by candymanmike on 2009-05-30
> sudo dpkg --configure -agot it to allow limewire to start installing. now my problem is, after waiting for all of the java stuff to install it tells me that the limewire file is either corrupt or i don't have permission to install it. since i am the only user on this pc i know for a fact i'm the admin. so that would leave the option of a corrupt file....which i downloaded directly from limewire, the only linux version of the current software.

i just got frostwire to load just fine though. so i'm good now. thanks for the help. it's truly appreciated.

---

