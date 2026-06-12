---
title: "cant get online with ubuntu and vmware in xp -- please help this is my first day!"
date: 2006-01-16
forum: General Help
---

### Post by nauticalsland on 2006-01-16
I just loaded up ubuntu with vmware on my t23, and man it rocks so far... what a beauty!


I cant get online though, I am connected with a linksys wireless card, and what is the first thing I should do to get it to work?


please help me, I want to use ubuntu sooo bad!

---

### Post by Gowator on 2006-01-16
[QUOTE=nauticalsland]I just loaded up ubuntu with vmware on my t23, and man it rocks so far... what a beauty!


I cant get online though, I am connected with a linksys wireless card, and what is the first thing I should do to get it to work?


please help me, I want to use ubuntu sooo bad![/QUOTE]

If you network is working in the host OS (presume you are using XP) then you need to configure the session to used bridged networking (easiest) 

You can also config NAT but its more complex ...

---

### Post by nauticalsland on 2006-01-16
[QUOTE=Gowator]If you network is working in the host OS (presume you are using XP) then you need to configure the session to used bridged networking (easiest) 

You can also config NAT but its more complex ...[/QUOTE]


ok, I found the bridged... how do I configure it?


also it shows my ethernet card as functioning.. and its sending and recieving packages, but FF is not working?

any help would be awesome!

---

### Post by Gowator on 2006-01-16
[QUOTE=nauticalsland]ok, I found the bridged... how do I configure it?


also it shows my ethernet card as functioning.. and its sending and recieving packages, but FF is not working?

any help would be awesome![/QUOTE]
OK bear in mind Im doing this in reverse ....(vmware in linux running virtual machines)

So how does your win machine get its IP address and routing ... 
basically bridged networking will just make it appear like you have one extra PC on the network ...

If this is a home router then its probably using DHCP ... you can therefore use the same in Ubuntu (in admin/network admin) ... 
However if your router will only accept one IP then it will be easier to use NAT which will fool the router to thinking iots all from the XP box.  

if you can open a terminal/xterm etc. from the menu then 
ifconfig eth0 

(try and type back the output)
route
(again try and give the output)

If you have a shared drive on the Windows machine or network you can check stuff by trying to find the shares (this will confirm its actually working not just pretty lights) 

if you know the IP of your win machine try a ping from linux direct to the ip

---

### Post by nauticalsland on 2006-01-16
[QUOTE=Gowator]OK bear in mind Im doing this in reverse ....(vmware in linux running virtual machines)

So how does your win machine get its IP address and routing ... 
basically bridged networking will just make it appear like you have one extra PC on the network ...

If this is a home router then its probably using DHCP ... you can therefore use the same in Ubuntu (in admin/network admin) ... 
However if your router will only accept one IP then it will be easier to use NAT which will fool the router to thinking iots all from the XP box.  

if you can open a terminal/xterm etc. from the menu then 
ifconfig eth0 

(try and type back the output)
route
(again try and give the output)

If you have a shared drive on the Windows machine or network you can check stuff by trying to find the shares (this will confirm its actually working not just pretty lights) 

if you know the IP of your win machine try a ping from linux direct to the ip[/QUOTE]



SWEET!!!  that worked!


Man I cant wait to get Ubuntu onto a dual boot on my desktop... I was just trying it out on vmware tonight, and what a beauty!

do you know the easiest way to set it up as dual boot?  I dont want to backup and re-install my xp box... maybe just format with partition magic and install on the second partition?  will that work as a dual boot?  and not **** up my xp install?

---

### Post by Gowator on 2006-01-17
[QUOTE=nauticalsland]SWEET!!!  that worked!


Man I cant wait to get Ubuntu onto a dual boot on my desktop... I was just trying it out on vmware tonight, and what a beauty!

do you know the easiest way to set it up as dual boot?  I dont want to backup and re-install my xp box... maybe just format with partition magic and install on the second partition?  will that work as a dual boot?  and not **** up my xp install?[/QUOTE]
Pretty much as long as you follow the instructions during install. 
Make sure you know which partitions are which BEFORE you start and then at the end when iot configures the boot loader it will automatically find the Windows install and stick it on the menu :D  

You can also use boot magic if you wish though I stick with the installed one since I don't have any Windows partitions only linux and bsd ones.  

good luck .. and just take the install slowly .. most bad installs are just peope to eager to get it all going who misread something in haste (IMHO)

---

### Post by nvez on 2006-01-17
For a new person to ubuntu and a wireless linksys card, not a very good combination, in general linux+wireless isn't the easiest thing to setup.

---

### Post by Gowator on 2006-01-17
[QUOTE=nvez]For a new person to ubuntu and a wireless linksys card, not a very good combination, in general linux+wireless isn't the easiest thing to setup.[/QUOTE]
Good point ... I had forgotten that part after getitng it to used bridged NW from the vmware session ... however it did find my netgear wg511 and config it first time :D

---

