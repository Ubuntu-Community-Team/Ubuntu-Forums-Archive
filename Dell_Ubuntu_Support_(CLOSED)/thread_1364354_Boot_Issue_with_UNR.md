---
title: "Boot Issue with UNR"
date: 2009-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ramathorn on 2009-12-25
I currently have a dell mini 10v running ubuntu netbook remix 9.10. The computer came with xp but i switched it over to ubuntu. When I try and boot up the computer it passes the post then the ubuntu logo appears then shortly after cancels out and opens up a maitanence shell. after hitting ctrl-d in the shell it says that the drive can not be mounted. So i made a flash drive boot drive to try and reinstall. First i tried to preview without installing but it locks up and nothing happens. I then tried to just reinstall but after selecting it the computer just shows a black screen and doesnt advance past that. This is making me believe that there is something wrong with the hard drive of the computer. But what is odd is it shows the ubuntu logo and thats it so the hdd must have some activity.

I also contacted dell support by doing an online chat. I belive the person was confused by the fact i had ubuntu instead of xp. After explaining the issue and saying how i think it may be a hdd issue she simply said contact ubuntu. 

Hopefully this will be more helpfull

---

### Post by Ramathorn on 2009-12-28
Bump

---

### Post by mikewhatever on 2009-12-30
Hi and welcome,

I think the fact that you can't load the live environment, which is the same as preview without installing, is not indicative of an hdd problem. I'd advise checking the installation media for integrity, using the appropriate option from the live media menu.

---

### Post by pfranks on 2009-12-30
Everything you say is suggesting you have at least one software configuration issue - or maybe a missing file. It sounds like your drive is working, but you are getting single user as root(?) rather than a GUI.

Can you enter any regular linux commands in the maintenanace shell? Try:
uname
ls
dmesg
 
(the output of dmesg might have a few clues)

I suggest you go back to your Ubuntu CD and try it in demo mode (live CD) to prove the hardware and give you confidence. Then post back to report progress, and describe exactly what the "maintenance shell" says.

---

