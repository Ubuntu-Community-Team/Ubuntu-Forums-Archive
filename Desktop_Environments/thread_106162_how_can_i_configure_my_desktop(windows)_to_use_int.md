---
title: "how can i configure my desktop(windows) to use internet with my linux laptop?"
date: 2005-12-20
forum: Desktop Environments
---

### Post by JoonHeo on 2005-12-20
Hi!
I just installed Ubuntu for the first time.
which means i'm not used to anything in this linux system T.T

I have a desktop connected to this laptop with a lan cable which has windows on it.
I used 'connection wizard' to set up the network so that my desktop has connection to the internet when i had windows on my laptop, but obviously, i cannot use a wizard to configure that now.  (oh, i use wireless connection for my laptop , so it has internet connection but my desktop doesn't that's why i did that)

how am i supposed to configure my laptop and my desktop? T.T
thanks in advance.

---

### Post by briancurtin on 2005-12-20
why exactly do you want to pipe your connection through the laptop and on to the desktop? im not even sure if i understood that correctly

if you want to split the net between two computers, you could buy a router/switch/hub to more effectively do this

---

### Post by JoonHeo on 2005-12-20
it's because i use a wireless connection for my laptop and that's the only way to get on the internet, and i want my desktop to have connection to the internet.

thanks for reading my thread :) & plz help me T

---

### Post by alamba on 2005-12-20
Joon, I have a similar setup at my home, this is how I do it:
1. My ISP connects over a DSL modem to my desktop that is running XP
2. I have a LAN card on my desktop that connects to a WiFi Access point
3. My ubuntu laptop connects to this access point

Now, I connect to the internet with the connection icon on XP and have share this internet connection enabled. I use private IP's within my home network so ofcourse have NAT enabled. 

You dont need a seperate router, etc. for this setup.

Akshay

---

### Post by alamba on 2005-12-20
Here are the answers to some of your questions:
1. The DSL connection is a USB modem over the regular phone lines. So it connects to the desktop via a USB port.
2. There is a regular LAN cord between my LAN card on the desktop and the access point (wireless router/box/etc)
3. My laptop connects over wifi (wireless connection) to the access point.

Akshay

---

### Post by JoonHeo on 2005-12-20
thanks for your kindness alamba TT_TT
after reading your post again and again, i am thinking that maybe you have your connection on your desktop(through lan cable) and you configured everything so that you can use your laptop, too, through wireless lan, right?
My problem is that i have a wireless AP in my home and that is the only connection that i could use in my room. (the lan cable is too far to connect it to my desktop) that's why i want to configure everything so that my desktop is able to have internet connection too, 

I am just a beginner in everything (including windows and internet connection) could you please tell me step by step on how to configure this ? 

I am so thankful for your kindness, again and again

---

### Post by alamba on 2005-12-20
So you want your desktop on a AP that connects to the internet, right? Does your desktop have a wireless LAN card? And how is this question then a ubuntu related question?

I think it would be easier to figure out a solution if you posted a rudementary network diagram about the setup you want.

And u're more than welcome. No need to thank me...thank the community. God knows how many times i've shouted out for help myself.

Akshay

---

### Post by Ocxic on 2005-12-20
i know what you ant to do.

1st: enable internet connection sharing in ubuntu in Firestarter, selecting the proper internet connection(your wifi) and network connection(the eithernet cable) in each of the dropdown menus, and enable DHCP, all this is in the preferences

2nd: Connect your ethernet cable to both of your boxes (unless your using a hub/router you WILL need to us a Crossover cable, check radio shack/staples or any computer store)

3rd: use the wizard to setup a net connection on winXP making sure you select the proper connection option.

that should be all unless I'm missing something, you should now have a net connection on XP and your laptop.

---

### Post by JoonHeo on 2005-12-20
wireless ap : connected to no computer -> just spreading signals out to any wireless connections

laptop : connected to wireless ap and able to use the internet (using ubuntu) (has a wireless lan card and a lan card )

desktop : connected to nothing (the ap is too far away to connect it via lan cable) (windows xp)    (has a lan card only)


connection :          ISP
                              ||
                              ||
                          (lancable)
                              ||
                              ||
                      [ wireless AP ]
                           /                                      
                        /
          (wireless connection)
                     /
                    /
             laptop   =======(lan cable)=========desktop




i don't know what rudemetric (?) is that's why i just wrote it down T.T

as you can see, my laptop has connection but there is no way my desktop can use internet because it doesn't have wireless lan card..  that's why i connected a lan cable between  laptop and desktop..

when i used windows on my laptop, i used this 'network configuration wizard' that just did it by magic, but ubuntu doesn't have that and that's why i posted it on ubuntu desktop forum (is it not in the right forum??)


thanks alot again in advance ^^

---

### Post by Ocxic on 2005-12-20
[QUOTE=Ocxic]i know what you ant to do.

1st: enable internet connection sharing in ubuntu in Firestarter, selecting the proper internet connection(your wifi) and network connection(the eithernet cable) in each of the dropdown menus, and enable DHCP, all this is in the preferences

2nd: Connect your ethernet cable to both of your boxes (unless your using a hub/router you WILL need to us a Crossover cable(this is not a normal cable), check radio shack/staples or any computer store)

3rd: use the wizard to setup a net connection on winXP making sure you select the proper connection option.

that should be all unless I'm missing something, you should now have a net connection on XP and your laptop.[/QUOTE]


do this and it should work

---

### Post by JoonHeo on 2005-12-20
thanks alot ocxic.. i'm trying that right now... i figured that i don't have this firestarter ( google told me that it's a firewall program...) and i'm installing it right now. I'll tell you if it works!

thanks alot everyone T.T

---

### Post by JoonHeo on 2005-12-20
I tried that but it doesn't work TT_TT
the firestarter says 

"the device eth0 is not ready.
Please check your network device settings and make sure your Internet connection is active"

I configured both eth0 (wireless) and eth1 as 'enable DHCP'...

what is wrong? T.T
even the main window says that eth0 has activity when i use the internet!!

I just don't get why.. please help me and thanks again..

---

### Post by alamba on 2005-12-20
Are you using a patch or a cross cable? OCxic is right, based on your description all you need to do is get firestarted to NAT and forward your packets.

Incase this does'nt work they changing /etc/interfaces/config 

ip_forward=no to yes.

Akshay

---

### Post by JoonHeo on 2005-12-20
but... the ordinary lan cable worked when my laptop was windows...

so there isn't any way that i can make it work with an ordinary lan cable if my laptop is ubuntu?

well, then i'll just have to stick to windows T.T

---

### Post by JoonHeo on 2005-12-20
Thanks everybody I appreciate it alot especially alamba :) have a nice day everybody

---

### Post by JoonHeo on 2005-12-20
i got it to work!!!!!!!
I don't know how but it just is working !!

i just configured my eth1(lan card of my laptop) as static ip, not dhcp and 
configured its ip as 192.168.0.1, subnetmask 255.255.255.0 gateway (blank)

and my client computer (desktop) as also static ip,
192.168.0.2 subnet 255.255.255.0 gateway : 192.168.0.1 and 
dns the same as my eth0 dns of my laptop...
it works!!!

thankx alot everybody

---

