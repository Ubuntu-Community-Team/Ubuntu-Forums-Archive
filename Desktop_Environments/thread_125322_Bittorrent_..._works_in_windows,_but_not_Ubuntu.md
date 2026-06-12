---
title: "Bittorrent ... works in windows, but not Ubuntu"
date: 2006-02-03
forum: Desktop Environments
---

### Post by deadd on 2006-02-03
Hello, I have problem with using bittorrent clients in Ubuntu.  They work in Windows (XP w/SP2 and bitcomet)  but if I use either azureus or the default bittorrent program that was installed with Ubuntu, either I can't connect, or the downloads are very, very slow.  I know the proper ports on my router are open, I downloaded firestarter and specified which ports to allow, and also with Azureus I specified the correct listening port.  But I still don't know why the big difference in performance.  Any advice is appreciated.  Thank you.

BTW the hardware (except for the hard drive, which I swap every time I switch OS) is the same.  both OS have the same  static internal IP.

---

### Post by Khanater on 2006-02-05
i'm getting the same experience, any idea around?

---

### Post by kinseikun on 2006-02-05
I 3rd this. At first my torrents with Ubuntu were very slow, but now they won't connect at all. I am using Bittornado. Default won't connect either. Help us all!!!

---

### Post by ubuntu27 on 2006-02-05
Why don't you guys Try out OFFICIAL BitTorrent ? [http://www.bittorrent.com/](http://www.bittorrent.com/)

Download the Deb file
and install it  with sudo dpkg -i package_file.deb  [In this case it is sudo dpkg -i BitTorrent-Stable.deb if I am correct]

---

### Post by Khanater on 2006-02-05
i try with: azureus, bittornado, bittorrent, Anatomic, g3torrent and others...have a router and firewall, but the ports are open and forwarded. Also try changing the ports and dont works, cant get more than 5-8 kb/s when i get 40/50 in windows xp ... but, dont know what happens

---

### Post by dickohead on 2006-02-05
I too have isues with *torrent in ubuntu, in windows it will frequently get the max download rate, but not with ubuntu (or any other linux distro), I've even tries setting the DMZ, disabling firewall, multiple port forwarding, torrent on multiple machines.. but nothing!

---

### Post by Khanater on 2006-02-06
Can be this the solution? IPV6 problems?

[http://ubuntuforums.org/showthread.php?t=126221](http://ubuntuforums.org/showthread.php?t=126221)

Can't probe now because im at work, ill try later.

---

### Post by Jedeye on 2006-02-06
I installed Azures with automatix and have no problems here.

---

### Post by newuser111 on 2006-02-06
install firestarter

sudo apt-get install firestarter

unblock ports 6881-6889 in "allow service" in policy section of firestarter gui

---

### Post by Khanater on 2006-02-06
[QUOTE=newuser111]install firestarter

sudo apt-get install firestarter

unblock ports 6881-6889 in "allow service" in policy section of firestarter gui[/QUOTE]

[QUOTE=Khanater]
i try with: azureus, bittornado, bittorrent, Anatomic, g3torrent and others...have a router and firewall, but the ports are open and forwarded. Also try changing the ports and dont works, cant get more than 5-8 kb/s when i get 40/50 in windows xp ... but, dont know what happens
[/QUOTE]

i use firestarter and the ports (6881-6889 and also try with anothers ports range) are open and forwarded from the router, but still with the same speed problems in Ubuntu and not im WinXP.

---

### Post by kinseikun on 2006-02-06
same problem--I used firestarter and i THINK (because I dont know how to open the ports) for 6881-6889 AND 10000-60000 (the random ports that Bittornado uses) and I still get nothing except a note saying that I couldnt connect to the tracker. This problem seems to have happened at the time that I updated from Hoary to Breezy. If someone can tell me how to disable the internal firewall or open ports (if that is the problem) I would be so happy. I am so frustrated by everything either not working or being slow. At this point i would be happy if my BT was slow....but it's not functioning at all. Thanks.

---

### Post by kinseikun on 2006-02-08
Hello--more news:

In firestarter, in "active connections", firefox and ayttm show up, but when I start a torrent, bt does not show up. It still says "Cannot connect to tracker--timeout exceeded.  Also, my internet is extremely slow. It took me an hour to get to this forum. I have a shared T1 connection (between about 100 people).

I put the ports 6881-6889 and 10000-60000 under the "policy" tab, "inbound traffic policy" , "allow service". Is this the correct setup? If so, why can I still not connect?

---

### Post by kinseikun on 2006-02-08
As you can see, I double posted. The internet hates me....I didn't click twice....did take 5 minutes to post twice tho....amazing....please help me....

---

### Post by kingsidy on 2006-02-08
first thing to try is to totally disable firestarted and see whether that improves the speed. if so then the issue is with firestarter. all you need to do then is create a new policy and allow the necessary ports. the other thing is that you have to test it with a torrent that has enough seeds so that you can make sure that you'll get a good speed. 

most important if you are using a router, you need to enable port fowarding. foward the ports used by your torrent client, yo have to also make sure that you are using the correct ip address. if it changes all all the time because of dhcp assiging different address then you need to increase the lease time to like a month or even longer. also some router have a built in firewall feature, you need to make sure that it does not block anonymous internet request (it depends on which router you are using). 

i used to have the same issue with torrents in ubuntu, after i fowarded the ports and allows the ports in firestarter, i get the same speeds i get in windows. i also max out by bandwidth down if i have enough seeds for a particular torrent. also it does not really matter which torrent client you are using, if the ports are not fowarded properly or if firestarter is blocking the communication, the speed would be low anyways.

so 1: check the port fowarding on router using correct ip address and also disable the "block anonymous internet request" if your router has that option

2: set up the same ports that are fowarded in the router so that firestarter would allow them as well. (you can start by disabling firestarter to see if it is the culprit)

3:get a torrent with a lot of seeds to test.

i also recommend using higher port number like 65533 for example. something high instead of the default 6881. it is said that some isp's sort of reduce the bandwidth used by torrent. so switch to a port number other than the ones commonly used.


good luck, hope this helps at all

---

### Post by kinseikun on 2006-02-08
Hello,
Eh, I don't know if I have a router. Because I don't really know what that is. i live in a na apartment building and share the connection. I hope that answers to whether or not I have a router. 
I wasn't connecting to trackers even before i installed firestarter. And I opened 10000-60000 for the bt ports. One of the things I would like to download someday,  if possible, has 130 seeds right now. Still cannot connect. Even while firestarter is disabled, even when I opened ports 60000-70000....do I have some kind of hidden firewall i dont know of since i installed Breezy? Do I actually have a router? And where would I go to configure it on my computer>? 
I thank you guys for the help....every day I feel like I'm getting closer to the problem....It's been so long since I've been able to connect to bt.....i_i.....

---

### Post by bored2k on 2006-02-08
[http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)

Do and advanced port scan. When asked, insert the ports your BT client is working with at the moment. It will tell you/us the exact problem of your connection (blocked/stealthed  ports, etc).

Note: your torrets must be running.

[http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)

---

### Post by deadd on 2006-03-29
Hello, and thanks to all the replied to my original post.  I have looked into why my torrents work in windows and not in linux, but I couldn't find the culprit.  I do want to mention (or maybe I shouldn't) I have installed another distro of linux on another hard drive and installed azureus using the built-in automated software installer.  This time the torrents work better (though still intermittent).  I may have installed azureus on Ubuntu incorrectly, as I manually installed azureus using make install instead of the add software option in the GUI.  

I will try bittorrents again with Ubuntu eventually, as the current installation is on a temp hard drive.

---

### Post by Ailis on 2006-03-30
I'm having the same problem, but I was under the impression that my internet-provider decides wether or not I'm having a static ip-adress. I may be wrong, but anyway, I have no idea where to even start to try to configure my router. I didn't do it myself when it was set up. I have a Linksys WRT54GC-router. 

Also I don't get why it should be such a big problem in linux when everything works perfectly in windows (xp). What I've ended up doing is plugging in my old slow (and probably virus-infested) windows-pc whenever I want to download something. Not really an option in the long run as I installed linux on my new pc hoping that I'd seen the end of microsoft-products in my home.

---

### Post by Quinthius on 2006-04-06
I was having this same problem. Ports were forwarded properly, and I even tried disabling ipv6 as someone else suggested earlier in this thread, still no luck.

Then I found some article on the web, here:
[http://www.evilducky.net/2005/10/07/ubuntu-linux-azureus-problems/](http://www.evilducky.net/2005/10/07/ubuntu-linux-azureus-problems/)

Apparently some system update somewhere switches the default java version to gjc, which was the case for me also. I switched it back to sun's java using "sudo update-alternatives --config java", restarted Azureus, and voila, connections started coming in and everything works fine now. So try that out if you guys haven't yet, cause it worked for me!

---

