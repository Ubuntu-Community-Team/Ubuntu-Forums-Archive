---
title: "Used Automatix (and some newbie fittling) now no network connection"
date: 2006-03-05
forum: Desktop Environments
---

### Post by greenmaji on 2006-03-05
[color=red]**Resolved**[/color]

I used Automatix well to do the things it does for you. :rolleyes: 

I ran it from the terminal if that makes a diffence.

Now I cant reach the internet (though my LAN)
Ubuntu did fine finding its way through the LAN durring the install process so Im kinda lost as to why it lost this durring the Automatix package installs.

is there a list of needed packages to connect to the LAN?

now that I think about it I tried to uninstall and then reinstall firefox before I used automatix though synaptic (and I might have not caught all the packages that need to be reinstalled :( )

I feel well :-? dumb at this point. :(

---

### Post by alamba on 2006-03-05
Run the following and paste their outputs please:

1. ifconfig 
2. Ping <your gateway ip>
3. netstat -rn
4. Ping 4.2.2.2
5. Ping oracle.com
6. cat /etc/resolv.conf

A

---

### Post by greenmaji on 2006-03-05
well I cant exactly paste them.. I have to post this on a diffent computer.. but Ill try to do what your asking..

I do run those from the terminal right?

---

### Post by greenmaji on 2006-03-05
ok.. hope this helps..
if not Ill try to copy it all down.. :(

1. it seemed to work fine.. no overunns, drops or errors. (this could be enexperince talking though. :( )

2. it shows some information that looks kinda normal but it seems to be missing some results ( more inexperinced logic going on here :( )

3. network is unreachable

4. unknown host oracle.com

5. cat /etc/resolv.conf: no such file or directory

number 5 jumps out at me as being VERY wrong (I screwed up kind of wrong :( )

---

### Post by greenmaji on 2006-03-05
my bad on #5
I got the normal info I see from my ISP (the DSN server from the looks of it and the nameservers IP address)

---

### Post by greenmaji on 2006-03-05
Do you need more complete results?

Could someone point me to were to look for a log file of synampitc's activities?
I understand this is kind of lame but Im having a hard time navigating this file system, It doesnt relly "like" me to look around. :(

---

### Post by alamba on 2006-03-06
How about ifconfig? Are you even getting an IP address? Do you have DHCP running on your network? Try system>>admin>>networking>>disable and enable your ethernet card again.

A

---

### Post by greenmaji on 2006-03-06
I tried disabling and reinabling the network card and rebooting and shuting down the computer before posting this question.
DHCP is running on my router.
Im running it wired.
The cable testing utility in the router says the cable is runing 100% full duplex.
But.. my router isn't assigning the ubuntu box a IP address for some reason (Or in my screwing around trying to uninstall and reinstall firefox with synamtic I didnt reinstall a package or packages that is/are nessisary to connect the computer to the network)

I have a feeling I need to find the log fine..
I really want to fix this rather then reinstalling.. I messed it up and the only way Im going to learn is going about it the hard way. :D 

and thanks HEAPS alamba

---

### Post by greenmaji on 2006-03-06
Im not too superstisious.. But I needed to post again. (yikes last post was #13).

---

### Post by alamba on 2006-03-06
Look for logs in - /var/log/

Installing/Uninstalling should have nothing to do with not being able to get an IP. Incase you're not able to pull an IP from your router, can you give it a static IP in your subnet and check if you are able to get online?

A

---

### Post by greenmaji on 2006-03-06
Uhh.. Im so sorry for posting this question.. :rolleyes: 

I had restricted the number of IP's my DHCP could assign because my router is wireless (I didn't want any extra hitch hikers getting on) and my roomate used his Nentendo DS last night and snaged the last IP. ROFL

so it's back online \\:D/ 

Ill give the title an edit to let everyone know the issue is resolved..

thanks again alamba. :D

---

### Post by alamba on 2006-03-06
lol...you're welcome

---

### Post by greenmaji on 2006-03-06
All I can say is GREEF.. 24 hours with no intenet on a box over that :rolleyes:
Oh well.. could have been worse.. :-D

---

