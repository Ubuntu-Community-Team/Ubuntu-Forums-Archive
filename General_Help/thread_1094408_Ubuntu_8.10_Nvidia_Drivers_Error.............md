---
title: "Ubuntu 8.10 Nvidia Drivers Error............"
date: 2009-03-12
forum: General Help
---

### Post by brandon1393 on 2009-03-12
Ok first off im a complete linux noob D;. i used my install dish for 8.04 desktop to instal ubuntu take in mind thast i am dual booting with vista i upgraded 8.04 to 8.10 during installition i got some error that some feature may not work or somthing any way the real problem is iv tried all kinds of ways to get my nvidia drivers for 3D rendering but i keep getting the Low Graphics error ........ Any kind assistance will be much appreciated i really like ubuntu i just need my drivers :'( :(

---

### Post by wolfen69 on 2009-03-12
sounds to me that your "upgrade" went bad. which is why i always do fresh installs. sometimes just reinstalling is quicker than trying to figure out the problem, especially when an upgrade has been done.

---

### Post by brandon1393 on 2009-03-12
im not sure how to reinstall since i dual booted can you tell me how? Ubuntu seems awsome but this is disappointing :(

---

### Post by Neo_The_User on 2009-03-12
via livecd is how you reinstall.

---

### Post by brandon1393 on 2009-03-12
um soory for a noobish question but is the live cd diffrent and also what all do i have to do please bare with me :'(


also would i use 8.10?

---

### Post by Neo_The_User on 2009-03-12
you install via live cd. its not the nvidia driver installer.

---

### Post by brandon1393 on 2009-03-12
i mean is the live cd diffrent form the desktop version and do i need to delete anything ?

---

### Post by king EZi on 2009-03-12
> **brandon1393 said:**
> i mean is the live cd diffrent form the desktop version and do i need to delete anything ?

its the same thing...just pop it in and then do a normal install procedure... format all the linux(Ubuntu) partitions you have made in earlier installations then mount to respective folders i.e. / or /home...etc.  
PS: Do not format any partition with a filesystem NTFS coz that is your vista partition.. 

Hope i answered your question.

---

### Post by brandon1393 on 2009-03-12
will the install format it? is it in the menu when you load or will i have to use vista's disk manager

---

### Post by Neo_The_User on 2009-03-12
Install will format whatever you tell it to format.

---

### Post by brandon1393 on 2009-03-12
so i pop in live cd tell it to reformat ubuntu partition and install it there?

---

### Post by brandon1393 on 2009-03-12
so i load live Cd tell it to install and reformat the ubuntu partition then it should work?

---

### Post by king EZi on 2009-03-12
> **Neo_The_User said:**
> Install will format whatever you tell it to format.

Its the "colorful menu' of your hard disk, just go to "Manual".

this link might be useful 

[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

---

### Post by brandon1393 on 2009-03-12
my dual boot will still work?

PS: thx for the help

---

### Post by king EZi on 2009-03-12
> **brandon1393 said:**
> my dual boot will still work?

PS: thx for the help

normally it should work because you'd be installing grub all over again...and it can detect your vista. 

PS:you're welcome.

---

### Post by brandon1393 on 2009-03-12
so this should fix my driver problem?

---

### Post by king EZi on 2009-03-12
hopefully, if the problem was caused by upgrading...or you can downgrade...i tried 8.10 and had some problems with it then downgraded to 8.04 and it's working fine except for a few minor glitches.

---

### Post by brandon1393 on 2009-03-12
ok i will report back when im done

---

### Post by king EZi on 2009-03-12
good luck :P

REMEMBER NOT TO FORMAT ANY NTFS FILESYSTEM

---

### Post by ed-koala on 2009-03-12
If re-install still gives the same issue, you may be experiencing what a lot of us went through with nvidia drivers before the latest ones came out.

Lots of posts here about it, but I think it's all been fixed with the latest drivers (so check to be sure you have those up to date).

---

### Post by brandon1393 on 2009-03-12
ok im at the install menu but i cant figure out what to do in the partitioner you said manual but i cant figure out what to do in manual  please help

---

### Post by brandon1393 on 2009-03-12
please i really need help

---

### Post by brandon1393 on 2009-03-12
ok i got it re-installed the driver still will not install properly 
any suggestions?

---

### Post by king EZi on 2009-03-13
> **brandon1393 said:**
> will the install format it? is it in the menu when you load or will i have to use vista's disk manager

check out this link.... ```
http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml
```

in the formatting section don't select "guided", select "manual" if you want to format some partitions...

Does that answer the question??

---

### Post by king EZi on 2009-03-13
> **brandon1393 said:**
> ok i got it re-installed the driver still will not install properly 
any suggestions?

mhhh...go to administrator in the menu and click on "hardware" i think...there should be the model of your video card and a box to tick, tick the box and try. I've had issues with my nvidia graphic card too...that kinda solved the problem in my 8.04. 
Hope it works.

---

