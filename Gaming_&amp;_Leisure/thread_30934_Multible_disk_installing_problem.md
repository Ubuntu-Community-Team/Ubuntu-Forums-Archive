---
title: "Multible disk installing problem"
date: 2005-05-01
forum: Gaming &amp; Leisure
---

### Post by wasynyt on 2005-05-01
Im not able to chance disks when in tryingto install something with cvscedega...
so i cant install most of my games (simcity 4, mafia, hitman contracts, c&c generals to mention a few.. yes im former windows user) 
so if someone could point me the way to fix this problem i would appreciate that

---

### Post by defkewl on 2005-05-01
Unmount it first with 
$ umount /media/cdrom

---

### Post by wasynyt on 2005-05-01
thanks that helped...
only to find out that im not able to play anything....
as it cries for the missing truetype fonts (how and where to get them) 
and doesnt like mine scandinavian keyboard map

---

### Post by wasynyt on 2005-05-03
got some miracles happening here...
i stopped working... -> started to crash all the time
so i thought just to install it again...
total disaster
now icant umount anything
also
cvscedega app.exe
then it runs the first disk
installer asks put the other cd in drive
hmm
umount /media/cdrom
media in use
media in use
umount -f /media/cdrom
media in use......
...
..
. 
umount -l /media/cdrom
ok
disk 2 in drive
nothing happens
mount -t  iso9660 /dev/hda /media/cdrom0
ok
try to press ok in installer nothing happens
try to go to drive with konqueror it doesnt show anything, checed mtab it is listed as mounted

---

### Post by wasynyt on 2005-05-03
i know im frustrated, bu tthe thing is i want play..
and so when i get mystical error that prevents me from playig im going to be really pissed of... (poor computer of mine) 
but to the point
ive searched thru dozen of forums and tried various tricks, i can get the cd out and in and it gets automatically mounted/unmounted but yet that (infernal) installer of simcity 4 doesnt accept when i try to click ok... to accept the disk chage.... argh!!

so if anyone could say/tell/give me the link that would solve the problem
oh and i dont accept reinstalling kubuntu (hoary 5.04) as an solution
though none of you is going to suggest that anyway (just to be ure)

 ps i know someone of you will think "why doesnt he just buy licence?" but i need credit card for that and i dont have one and i cant get one (in here Finnland its darn hard to get one) so thats it (i could easily spend 15 euro to make my games work like dreams but no

---

### Post by wasynyt on 2005-05-04
this thread is transforming into my problem box..

but yet i starting to be little confused about this..
how come. i can ejetct the first, insert the second and see it mount.. creates an icon to desctop in kubuntu, but yet clicking installer ok does nothing...
id like to know how to debug this problem to see whats going on, and what can i do for it
allthough some may say that if the game is not native i should not play it as it supports windows... yet i cant buy that many linux games in here....
so can it truly be that i cant use my computer to anything non creativa aka playing (no those native free games arent enough, the quality isnt just the same and thats what matters)
yet again my cry for help

---

### Post by wasynyt on 2005-05-04
hmm trying to to install cedega again...
maybe it would work after reinstall

---

### Post by wasynyt on 2005-05-04
sisnt bring me any nearer to solution...
so i think the problem is cedega
so ive be leaving this as there i snothing i can do to it

---

### Post by wasynyt on 2005-05-04
yet im open to any help anyone may be able to give me

---

