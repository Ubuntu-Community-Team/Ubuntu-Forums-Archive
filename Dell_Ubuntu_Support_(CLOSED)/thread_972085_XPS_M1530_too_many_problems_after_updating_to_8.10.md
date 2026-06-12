---
title: "XPS M1530 too many problems after updating to 8.10"
date: 2008-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by entroix1 on 2008-11-05
It has been one week since I updated my XPS M1530 laptop to 8.10 and i am facing a lot of problems. I tried searching the net for solutions but all the solutions come to a dead end.

1) One of my major problems is that my wifi is not accessible.Some of this turnouts could be helpfull.

entroix@entroix:~$ lspci | grep Network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
entroix@entroix:~$ lshw -C network 
     capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.4 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
entroix@entroix:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"*******"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: *********
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-45 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

entroix@entroix:~$ 

I tried many ways for resolving the problem but a face even more problem such as.
I try opening hardware drivers and the only hardware driver I get is nVidia drivers asking me to choose which one to activate, I choose , everything works fine, but still I get no other drivers.I don't know if this is how it is supposed to be! I already tried ndiswapper.Nothing works!! Anything I do leads me to the same point. NOTHING!!
 
2) Another major problem is when I try opening applications asking for the superuser password, such as synaptic package manager and software sources, the application never opens after I enter the correct password. I always have to open the application from the command line using sudo command so the application wont ask me for the authentication! any help here?

3) The problem that a lot of people solved but me! When you have wireless button off, system wont boot up! even recovery mode stucks at the point of searching wireless.I read a thread and people said that with linux-headers-2.6.27-7-generic this problem will be solved, and indeed was solved for them. When I installed my 8.10 linux-headers-2.6.27-7-generic was already updated,but still I have this problem.any help here?

4) Sessions have changed. I cannot stop gnome-panel from restarting. Therefore I cannot use Avant Window Navigator in full as I used to on 8.04.

5) My sound buttons wont work ( still haven't searched for a thread based on that but it is still a problem I face with my XPS M1530 ) 

6) Fingerprint reader stopped working ( but still there and asks for my fingerprint ) 

7) I also have the impression that my software updates are not working at the moment due to problem number 2 because I haven't gotten any updates since I installed 8.10. Weird because before I had updates almost daily.


I hope I can find help on this issue and help others as well facing the same problems.

---

### Post by Gausian on 2008-11-05
Could it be that you had a botched update?  have you tried putting in an 8.10 live cd and seeing how things work?

If things look good on the live cd, then maybe a clean install is what you need.

---

### Post by accesshater on 2008-11-05
@topicstarter
Did you installed 8.10 with a clean install or with updates?

I also have ubuntu 8.10 on my 1530 and wireless works better than ubuntu 8.04.

The only problem i have is the hdd load cycle problem. (didnt test webcam and fingerprint)

---

### Post by scotthammy on 2008-11-05
Hi there, I have also had afew issues with my 1530 install but mostly with the mouse, id have to also suggest you have a bad install and to test on live cd and or do a fresh install.

---

### Post by entroix1 on 2008-11-05
thanks for the usefull information. I will try reinstalling from live cd and let you know if there are further problems or if the problems insist. Starting from scratch would be a good idea but still a few problems remain. Sessions have changed and I can't stop gnome panel from restarting. Is there any other solution?

---

### Post by Coort on 2008-11-06
> **entroix1 said:**
>  

6) Fingerprint reader stopped working ( but still there and asks for my fingerprint ) 

With upgrading i'm pretty sure that pam configuration files were changed.
At least during upgrade it ask you if you want to change the files, btw i have the same problem but i've not checked if all configuration needed for fingerprint auth are in place.

---

### Post by jwalker on 2008-11-06
Oh it's good to be upgraded. 

I have just upgraded (cleanly) and my wireless is imperfect. I can see networks but as yet I have been unable to connect. Keeps spitting back the password. Reminds of the the Edgy Eft days! 

The restricted drivers thing is simply not working either. dunno what that's about. When I click on activate it asks for my password then something quickly flashes by but no downloads take place. shiku shiku. 

And the track pad is screwed as usual, but I can find existing posts where I can get that fixed. 

But any help with the first two would be great! WAR Ubuntu!

---

### Post by jwalker on 2008-11-06
OK nvidia driver has downloaded, had to open up some repos. I'm large and in charge! But seriously if wireless is broken I'm going to have a major tantrum then break down in tears.

---

### Post by jwalker on 2008-11-06
and for what it's worth i just ran some updates and it totally killed my network interfaces. all of them. was stressed out but a boot into the live cd and then a restart fixed the problem, can only assume the live cd initialised the interfaces or something. damn this is fun.

---

### Post by Gausian on 2008-11-06
try these in the terminal for restarting you wifi driver whe it bugs out...
```
sudo modprobe -r iwl4965
sudo modprobe iwl4965
```

---

### Post by entroix1 on 2008-11-07
ok now we have updates. i managed to update and my wireless now works!! the rest of the problems are still there. and one of the problems still bugs me a lot!!! i can not run applications that ask for superuser password on GUI. i had a hard time installing my updates!

---

### Post by entroix1 on 2008-11-16
everything solved!! installing from live cd is the solution to all the problems for XPS M1530 everything works PERFECTLY. thanks for your help

---

### Post by accesshater on 2008-11-16
I think there are lots of issues with upgrading from 8.04 to 8.10.
I know a few people who have upgraded as well, and it went wrong for all of them.

Good thing it worked :) (dont forget to look a t the HD issue [http://brainstorm.ubuntu.com/idea/15153/](http://brainstorm.ubuntu.com/idea/15153/) )

---

