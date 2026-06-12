---
title: "No sound in Firefox Flash Player"
date: 2005-08-21
forum: Desktop Environments
---

### Post by porkwarbler on 2005-08-21
Hey Guys, I have been messing around with Ubuntu again. I am using it primarily for running game servers and just to learn linux. I successfully installed macromedia flash player for firefox, but I get no sound when I go to Homestarrunner or any other flash based media site. I have a cmedia pci 8738 card. I hesitate to change sound cards because I finally have windows running the way I want it on a different partition    after running into sound problems with the onboard sound in windows. Is this a known issue with this sound card and Firefox. Is this a software problem or a hardware problem? I have seen other people having this problem, but my research has been inconclusive. Its not particularly important for the sound to work with flash player as the sound works for everything else. I have the sound working for flash player on a different box with different hardware (an older dell) using ubuntu firefox and I installed the player the same way. Any help would be greatly appreciated.

---

### Post by Hairy_Palms on 2005-08-21
did u install it from the repositories or the macromedia website? i installed it from the repos and it works fine in opera and firefox,

---

### Post by racecat on 2005-08-21
Don't know if this is a clue, but mine does the same thing...under gnome. With xfce, I get audio. The beeps and startup audio work fine in gnome.

Bill

---

### Post by Toddy on 2005-08-21
To add sound to flash:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

restart firefox

---

### Post by racecat on 2005-08-21
Thanks, Toddy. Any reason for that? I did install mine from the site.

Bill

---

### Post by porkwarbler on 2005-08-21
Toddy, thank you very much. I copied and pasted your command into the terminal and now it works perfectly. The question is why? Linux has me extremely happy at times when I figure something out and extremely frustrated when things don't work. I am thankful for this forum and the kind people that help us new linux users out.

---

### Post by Meurglys on 2006-04-07
[QUOTE=Toddy]To add sound to flash:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

restart firefox[/QUOTE]

Thaaaaaank you! :D

---

### Post by Jaymo on 2006-04-17
I too am having similar problems but Toddy's fix didn't work for me :(.

](*,) .

Any suggestions?

---

### Post by skwashd on 2006-04-18
[This](" http://ubuntuforums.org/showthread.php?t=147991") works for me

I should mention that you need to change 1000 to you current user id

---

### Post by btnheazy03 on 2006-04-19
[QUOTE=Toddy]To add sound to flash:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

restart firefox[/QUOTE]
Well that was fast :|

Thank you

---

### Post by hmahadik on 2008-04-22
> **Jaymo said:**
> I too am having similar problems but Toddy's fix didn't work for me :(.

](*,) .

Any suggestions?

wget [http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb](http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb)

That worked for me...:guitar:

---

