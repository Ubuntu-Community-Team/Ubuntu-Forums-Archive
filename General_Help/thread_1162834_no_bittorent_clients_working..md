---
title: "no bittorent clients working."
date: 2009-05-18
forum: General Help
---

### Post by jherskow on 2009-05-18
just did a full install of ubuntu on my old laptop 1 week ago.
used transmission for torrents-worked fine.
after a few days-transmission stopped working
showing "0 of 0 peers" even though many were available.
i tried to open the port like someone told me to- but im not sure i suceded.
i re-installed transmission- didn't help
i installed 4 other clients- all of them failed to download.

i am an experienced computer user, but not a programer or tweaker. i can follow instructions, though, if they are clear enough.

please help.

---

### Post by vahnx on 2009-05-18
I find Transmission a very bad client. I've used it on Mac and Linux, nothing but slow speeds and full of crashiness. You can obtain uTorrent for Windows and install it through Wine. Next, you might wanna check on the torrent file you are downloading. It just might not have any peers or seeds to download from. Google the torrent file's name and download the same torrent from other sites about 5 times and open them with the same torrent program. It will add more trackers to the torrent making it start/speed up.

---

### Post by zvacet on 2009-05-18
I'm not an expert but if Transmission worked then it is not port in question.Just reinstalling program is not enough,because you have detting saved.You will find them in home directory>view> show hidden files and you will find **.transmission** folder.Delete it and install Treansmission again.If still no luck jjst ppost here and somebody will help you.

---

### Post by hobo14 on 2009-05-18
I find Transmission to be a very nice, light, no frills client, I've never had any trouble with it.  
And if I didn't like it ther are many other options available before having to use a windows client on wine! (although utorrent is the client I use on windows)

It sounds to me like your most likely problem is port forwarding.  What is the setup of your network? ie, what is between your computer and the hole in the wall that is the internet?

eg my computer, wireless to router, cable to modem, cable to wall socket...

---

### Post by lovinglinux on 2009-05-18
> **vahnx said:**
> I find Transmission a very bad client. I've used it on Mac and Linux, nothing but slow speeds and full of crashiness. You can obtain uTorrent for Windows and install it through Wine. Next, you might wanna check on the torrent file you are downloading. It just might not have any peers or seeds to download from. Google the torrent file's name and download the same torrent from other sites about 5 times and open them with the same torrent program. It will add more trackers to the torrent making it start/speed up.

I don't think this is a good advice. Why running a proprietary software under Wine if you have several native torrent clients for Linux that work pretty fine?

Transmission is kind of simple to me, but it works. Deluge in the other hand is a full featured client, simple to configure, has a nice interface and is much better than uTorrent IMO. You can install it from the repositories. Just search for it in the "Add/Remove" manager or download the deb file from [here](http://www.getdeb.net/app/Deluge).

Anyway, there are a few possibilities to consider.

1 - The torrents you are downloading could be dead. Try downloading a popular torrent like an [Ubuntu release](http://www.ubuntu.com/getubuntu/downloadmirrors#bt). There are usually lots of people sharing it and the speed is very good. So if you don't get a good speed or no peers at all, then you might have a connection issue.

2 - The torrent [tracker](http://en.wikipedia.org/wiki/BitTorrent_tracker) included in your torrent file could be down, so your client is not capable of retrieving the peer list and thus request any connection. Connection to the tracker is done usually on ports 80, 6969 and others. It has nothing to do with the port forwarded, since it is an outgoing connection. Check the tracker availability to see if it is down, check the address to see if it includes a different connection port and then check if your firewall is blocking it.

3 - Your ISP might be blocking your connections now. Several ISPs reduces the bandwidth on common torrent ports (6881 - 6889) to reduce their costs and network clogging. Sometimes they block all torrent connections by analyzing the protocol of your connection. This is usually not a fair procedure, but you might want to check if they are allowed to do this according to your contract. Then, check if you have enabled connection encryption and try using a different port for incoming connections. Recommended ports are between 49152 and 65535.

4 - Your firewall might be blocking outgoing connections to the tracker or peers. If you use an ip filter like moblock or iplist, check if the tracker ip is not included in the blocklists.

5 - Correctly opening the port on your router will help you to get better speeds, but usually it would not prevent you from connecting to at least a few peers, since it will only affect incoming connections requested by outsiders. Your client will still be able to request connections to the outside, which has nothing to do with forwarding the port. This is done using random ports. Nevertheless, you might want to check if you have forwarded the port to your machine correctly. If you are connecting through DHCP, then your router might be assigning your computer a different IP from the one you are forwarding the port.

Check the site [PortForward.com](http://portforward.com/). It has instructions on how to correctly forward ports on several router models.

Also visit [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) and scan the port used by the torrent client (the one you forwarded). If you get the "Stealth" result, then you connection is not coming through.

If you find this overwhelming, then you might want to consider installing a simpler torrent client, like [Firetorrent](http://www.fireaddons.com/downloads/) extension for Firefox. It will allow you to download torrent using the built-in download manager.

---

### Post by jherskow on 2009-05-18
1) the torrents i am downloading are not dead. i have used amny different torrents, all of whom had many seeders and peers listed

2) i dont quite understand the whole tracking thig, i might need that in laymans terms.

3)i very much doubt my isp has begun blocking torrents, i live in israel and there is not even legislation for p2p and such, and there is only 1or 2 isp's i am sure iwould of heard of it had this been the case.

4) unless there is a built in ubuntu firewall i have not installed any

5)this is not a trasmission only problem; i have tried different torrents using transmission, ktorrent, bitstormlite, bittorent download client, and they all do not work. some simply list 0.0%  0kbps. k torrent said "stalled" as the status

6) i tried to open the ports, but i dont know quite how, and im not sure i managed to do it. however, transmission was working fine before without the ports ahveing been changed

7) i did reinstall transmission completely via synapticpackagemanager, but like i sadi, this is not a transmission exclusive problem.

i will try firetorrent and utorrent under wine, but id like to fix the problem even if these alternatives work

setup is computer-splitter-router-wall (i think)

i dont think my dad will let me mess around with the router settings though (no worries, i am the admin of my pc, just not the router)

thatnks so much for the response!

---

### Post by jherskow on 2009-05-18
ok, looks like firetorrent isn't working either.

dont know what that implies, but it probably means that the problem has a bigger scope than i thought.

---

### Post by jherskow on 2009-05-18
ok. bittorrent in wine IS working. but it is VERY slow(0.2 kbps), VERY hard to figure out (wine and everything). (healthy torrent file)

so definitely not a real solution.

---

### Post by jherskow on 2009-05-18
ok, this is confusing.

opend a torrent in bitstorm lite -it works! although relatively very slowly (8 kps)

tried too see if the problem was gone, but torrent still wont work in transmission or ktorrent.

in the meantime, bittorrent/wine stopped working, and now lists no peers.

my god.

---

### Post by vahnx on 2009-05-18
OK, in lamens terms. Is this the only torrent going slow? If so, Google the torrent name and download more of the same file and run them. It will add more trackers and you'll get faster speeds.

Best way to test this is go to The Pirate Bay, search for Ubuntu, and begin downloading it temporarily. It should go at your max download speed, if not it's most likely a port forwarding issue (if you are behind a router). To port forward, set a [static IP]("http://www.google.ca/search?q=ubuntu+static+ip&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") then [port forward]("http://portforward.com/") the application.

> **lovinglinux said:**
> I don't think this is a good advice. Why running a proprietary software under Wine if you have several native torrent clients for Linux that work pretty fine?

That was advice based on my experience comparing with just Transmission and I believe KTorrent which are the "two" main Linux torrent programs that are built into a desktop environment. You don't have to go with my uTorrent solution, I just found it worked flawlessly and quicker than the Linux solutions. But there are many other alternatives, such as BitComet, Azures (_sp_), FrostWire, etc.

---

### Post by lovinglinux on 2009-05-18
For the purpose of troubleshooting, lets use only Transmission form now on. Since the problem occurs with all torrent clients, this will help to identify the culprit.

> **jherskow said:**
> 1) the torrents i am downloading are not dead. i have used amny different torrents, all of whom had many seeders and peers listed

Did you tried the Ubuntu torrents I told you you to try? I'm asking this because it is very unlikely that you have an issue with Ubuntu tracker or the lack of peers. So please try it. It doesn't matter if you are trying other torrents, because I don't know which tracker they use and can't know if it is a problem with the tracker or something else.

When you say the torrents have peers listed, do you mean Transmission is displaying this information or you saw this on the web page where you downloaded the torrent file? I'm asking this, because the peers listed on a web site not necessarily reflects the truth. The site must grab the number of peers from the tracker and they don't do this all the time. If you visit some popular torrent sites, you will notice that there are many torrents that are not even updated anymore, so their number of peers are completely irrelevant. 

> **jherskow said:**
> 2) i dont quite understand the whole tracking thig, i might need that in laymans terms.!

When you download a torrent, you connect to several peers and they connect to you right? How do they know you have the file they want? The answer is: the tracker. Your torrent client (Transmission) sends your IP to the tracker to let it know that you want to share a specific file. It also retrieves from the tracker a list of IPs of other peers that are sharing the same file, so your client can connect to them. There are several trackers on the Internet. The tracker used depends on what you are sharing and it's address is embedded in the .torrent file.

If something is blocking the connection with the tracker, then you can't connect to peers.

> **jherskow said:**
> 3)i very much doubt my isp has begun blocking torrents, i live in israel and there is not even legislation for p2p and such, and there is only 1or 2 isp's i am sure iwould of heard of it had this been the case.

This has nothing to do with legislation. They block torrent because of money. Several ISP's worldwide have been selling unlimited bandwidth plans without properly predicting it's real usage. They basically sell the plan considering that the average user won't use the bandwidth limit most of the time. But they created "millions of little hungry monsters" with these expensive unlimited plans and the "monsters" want to use the bandwidth they are paying for. So everyone goes to torrent sites and download everything they can get the hands on. What happens next? The ISP network becomes clogged with huge amounts of data being downloaded 24/7, so not even the e-mails work properly anymore due to heavy traffic. Since they didn't planed the infrastructure to support the demand, they slow down torrent traffic. You wouldn't even know. The most famous case was the Comcast ISP, which went to court because they insisted on denying they were using [traffic shaping](http://en.wikipedia.org/wiki/traffic shaping) to slow down the torrent downloaders.

As I said, the way to try avoiding this is using encryption. Have you enabled encryption on the torrent client as I said? Have you changed the ports to avoid common torrent ports as I said?

I might not believe, but your situation is very likely to be a case of traffic shaping. Specially because it was working before. Another possibility is that your ISP is blocking the tracker address, that's why I told you to download the Ubuntu torrent. We need to know if the problem is the tracker.

> **jherskow said:**
> 4) unless there is a built in ubuntu firewall i have not installed any

There is a built-in firewall, but it allows all traffic by default. Just in case, let's check your iptables. Open "Applications >> Acessories >> Terminal", then paste the code below, then hit enter, the select the results displayed on the terminal, select "Edit >> Copy" from the terminal menu and paste it here.

```
sudo iptables -L
```

Additionally, have you visited the firewall scanner I told you to visit? If not, then start downloading a torrent, then go to [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) then click "Start Test", then click "Continue" after confirming the IP number displayed is yours, then click "Continue" again, then select the option "Scan desired ports and/or the range of ports" and put the number of the port you are using for torrents on the field and click "Continue". Wait for the results and paste it here.

Additionally, disable Transmission blocklist feature. Open "Edit >>> Preferences" then select the "Peers" tab and untick the "Enable blocklist" option.

> **jherskow said:**
> 6) i tried to open the ports, but i dont know quite how, and im not sure i managed to do it. however, transmission was working fine before without the ports ahveing been changed

Since you are not familiar with port forwarding, open Transmission preferences again, then click the "Network" tab, the select the option "Use UPnP or NAT-PMP port_forwarding" from my router. Then open the router administration page and find the option to enable UPnP. I can help you with that without knowing your router model.

This will make Transmission open the port automatically on the router. You can even change the port used on Transmission, between sessions. It will be opened on-demand.


> **jherskow said:**
> i dont think my dad will let me mess around with the router settings though (no worries, i am the admin of my pc, just not the router)

If you are not the router admin, you must ask your dad to change the settings. Otherwise there not much we can do to solve the problem. Knowing this now, is very likely that your dad changed the router settings without you knowing. He could have disabled the UPnP support or the port forwarding.

> **jherskow said:**
> ok, this is confusing.

opend a torrent in bitstorm lite -it works! although relatively very slowly (8 kps)

tried too see if the problem was gone, but torrent still wont work in transmission or ktorrent.

in the meantime, bittorrent/wine stopped working, and now lists no peers.

my god.

How many peers you were connected to when it successfully downloaded with just 8 Kbps?

Please test with the official Ubuntu torrents. Then tell me the download speed, how many peers you are connected to and the total number of peers available.

---

### Post by jherskow on 2009-05-18
i feel so stupid. used the official ubuntu torrents. works fine 80 kbps, 4/11 peers. 
i geuss this means i shouldent take the numbers on tpb for granted.

im so sorry for the trouble.

thanks so much for your help. apologies for noobieness.

---

### Post by lovinglinux on 2009-05-18
> **jherskow said:**
> i feel so stupid. used the official ubuntu torrents. works fine 80 kbps, 4/11 peers. 
i geuss this means i shouldent take the numbers on tpb for granted.

im so sorry for the trouble.

thanks so much for your help. apologies for noobieness.

No problem.

):P

---

### Post by yuli_capone on 2009-05-25
I have the same problem,i use deluge,transmition and utorrent.
(utorrent not working,the torrents not start)
The download is fine ,but no upload.I'm behind a router,i make port forwarding,but no results.
how to open a port for deluge?

when type sudo iptables -L,i get this:

yuli@yuli-laptop:~$ sudo iptables -L
[sudo] password for yuli: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
yuli@yuli-laptop:~$

---

### Post by lovinglinux on 2009-05-25
> **yuli_capone said:**
> I have the same problem,i use deluge,transmition and utorrent.
(utorrent not working,the torrents not start)
The download is fine ,but no upload.I'm behind a router,i make port forwarding,but no results.
how to open a port for deluge?

when type sudo iptables -L,i get this:

```
yuli@yuli-laptop:~$ sudo iptables -L
[sudo] password for yuli: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
yuli@yuli-laptop:~$
```

Please put terminal outputs between *code* tags.

Port forwarding should not affect your upload. It only allows you to accept requested connections from remote peers, which means they can start a NEW connection with you. Once the connection is ESTABLISHED, by request of your client (not affected by port forwarding) or by request of remote peers (affected by port forwarding), the download/upload rate is only affected by your speed limits, client configuration or firewall. 

There is nothing I could identify on our firewall settings that could prevent your uploads. As far as I know, ufw allows all outgoing NEW connections and also ESTABLISHED and RELATED, as you can confirm below:

```
Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
```    

There is nothing that would prevent you form starting to download a torrent, because outgoing NEW connections are also allowed. Additionally, once you are connected to some peers, there is nothing that would prevent you from uploading, because ESTABLISHED and RELATED connections are also allowed.

So, it could be your ISP blocking torrent traffic. It has been reported that in cases were the ISP interfere with torrent traffic you can't seed (upload) torrents. The upload could be also being limited by your own client, so check if you have setup upload limits. Another possibility is that you are connecting only to seeders, which do not require you to upload, since they already have 100% of the file.

To learn how to forward the port from the router, visit [http://portforward.com/](http://portforward.com/)

You should forward the same port you choose to use in the torrent client configuration and it should be forwarded to the internal IP of your machine. You also need to configure the firewall to accept incoming connections on the same port.

---

### Post by yuli_capone on 2009-05-25
I make port forwarding in my router with the same oprts i am using in deluge
i also make this test  [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)
am result this:
"Stealthed" (by a firewall) -Means that your computer is invisible to others on the Internet and protected by a firewall or other similiar software;

what should i do?that means i don't have any ports open,no?

---

### Post by lovinglinux on 2009-05-25
> **yuli_capone said:**
> I make port forwarding in my router with the same oprts i am using in deluge
i also make this test  [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)
am result this:
"Stealthed" (by a firewall) -Means that your computer is invisible to others on the Internet and protected by a firewall or other similiar software;

what should i do?that means i don't have any ports open,no?

The "Stealth" result in this case is probably because the port is not open on the firewall level. So, the router forwards the connections on that port to your machine correctly, but the firewall blocks it. That's why you get a "Stealth" result in the firewall scanner test.

You need to create a firewall rule to accept incoming connections on the same port your router is forwarding and used by Deluge.

---

### Post by yuli_capone on 2009-05-25
and how i make this?
sorry,am very newbie(sorry for my english,I'm from romania)

---

### Post by lovinglinux on 2009-05-25
> **yuli_capone said:**
> and how i make this?
sorry,am very newbie(sorry for my english,I'm from romania)

Go to "System >>> Administration >>> Firewall configuration"  and add a new rule for the port.

---

### Post by yuli_capone on 2009-05-25
i know this,but how?
what should i put in Preconfigured?:
Allow/Program/Deluge
in Simple:
Allow/Both/port number?
in Advanced:
Allow/Both/?

---

### Post by lovinglinux on 2009-05-25
> **yuli_capone said:**
> i know this,but how?
what should i put in Preconfigured?:
Allow/Program/Deluge
in Simple:
Allow/Both/port number?
in Advanced:
Allow/Both/?

Select Simple, Allow, TCP and put the port number on the field. Click "Add".

---

### Post by yuli_capone on 2009-05-25
and in Advanced ?

---

### Post by lovinglinux on 2009-05-25
> **yuli_capone said:**
> and in Advanced ?

You don't have to use the Advanced. The options "Simple", "Preconfigured" and "Advanced" are not complimentary, they just provide different methods/levels of rules creation.

For example, you could use "Preconfigured >> Allow >> Program >> Deluge" or "Simple >> Allow >> (Port Number) >> TCP". They will create the exact same rule. The only difference is that the preconfigured will grab the port number from deluge settings file automatically. If you use both, you will have a duplicated rule.

---

### Post by yuli_capone on 2009-05-26
Thanks very much,but it's no difference...
anyway,i have instaled utorrent through wine and not working,
the download it's not started....
any help with this please?

---

### Post by lovinglinux on 2009-05-26
> **yuli_capone said:**
> Thanks very much,but it's no difference...
anyway,i have instaled utorrent through wine and not working,
the download it's not started....
any help with this please?

For troubleshooting, please use deluge instead of uTorrent and test with an [Ubuntu release](http://www.ubuntu.com/getubuntu/downloadmirrors#bt) instead of any other torrent file.

Visit [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) again and check if the port is still "Stealth".

Post the contents of ~/.config/deluge/core.conf and the output of *sudo iptables -L* again.

---

### Post by yuli_capone on 2009-05-26
The port is still "Stealth"
I tested utorrent with an ubuntu release and it's start.I install utorrent anly to check the speed
A few hours ago i observe that the speed it's up to 400k,but sometines
came down to 20k,up again and so on.
Anyway ,thanks,it's better now
This is the content of core.conf and sudo iptables -L

(dp1
S'info_sent'
p2
F0
sS'lsd'
p3
I01
sS'send_info'
p4
I00
sS'state_location'
p5
S'/home/yuli/.config/deluge/state'
p6
sS'move_completed_path'
p7
S'/home/yuli'
p8
sS'enc_in_policy'
p9
I1
sS'queue_new_to_top'
p10
I00
sS'ignore_limits_on_local_network'
p11
I01
sS'rate_limit_ip_overhead'
p12
I01
sS'daemon_port'
p13
I58846
sS'natpmp'
p14
I01
sS'max_active_limit'
p15
I8
sS'utpex'
p16
I01
sS'max_active_downloading'
p17
I3
sS'max_active_seeding'
p18
I5
sS'allow_remote'
p19
I00
sS'max_half_open_connections'
p20
I50
sS'download_location'
p21
S'/media/Download/Download'
p22
sS'compact_allocation'
p23
I00
sS'max_upload_speed'
p24
F-1
sS'prioritize_first_last_pieces'
p25
I00
sS'auto_managed'
p26
I01
sS'enc_level'
p27
I2
sS'max_connections_per_second'
p28
I20
sS'dont_count_slow_torrents'
p29
I00
sS'random_outgoing_ports'
p30
I01
sS'dht'
p31
I00
sS'new_release_check'
p32
I00
sS'enc_out_policy'
p33
I1
sS'max_upload_slots_global'
p34
I200
sS'seed_time_limit'
p35
I100
sS'share_ratio_limit'
p36
F2
sS'max_download_speed'
p37
F-1
sS'torrentfiles_location'
p38
g8
sS'stop_seed_at_ratio'
p39
I00
sS'peer_tos'
p40
S'0x00'
p41
sS'upnp'
p42
I01
sS'max_download_speed_per_torrent'
p43
I-1
sS'outgoing_ports'
p44
(lp45
I0
aI0
***'enabled_plugins'
p46
(lp47
sS'random_port'
p48
I00
sS'autoadd_enable'
p49
I00
sS'max_connections_global'
p50
I500
sS'enc_prefer_rc4'
p51
I01
sS'listen_ports'
p52
(lp53
I56881
aI56890
***'max_upload_slots_per_torrent'
p54
I-1
sS'stop_seed_ratio'
p55
F2
sS'seed_time_ratio_limit'
p56
F7
sS'max_upload_speed_per_torrent'
p57
I-1
sS'copy_torrent_file'
p58
I00
sS'move_completed'
p59
I00
sS'proxies'
p60
(dp61
S'peer'
p62
(dp63
S'username'
p64
S''
sS'password'
p65
S''
sS'type'
p66
I0
sS'hostname'
p67
S''
sS'port'
p68
I8080
ssS'web_seed'
p69
(dp70
g64
S''
sg65
S''
sg66
I0
sg67
S''
sg68
I8080
ssS'tracker'
p71
(dp72
g64
S''
sg65
S''
sg66
I0
sg67
S''
sg68
I8080
ssS'dht'
p73
(dp74
g64
S''
sg65
S''
sg66
I0
sg67
S''
sg68
I8080
sssS'add_paused'
p75
I00
sS'max_connections_per_torrent'
p76
I-1
sS'remove_seed_at_ratio'
p77
I00
sS'autoadd_location'
p78
g8
sS'config_location'
p79
S'/home/yuli/.config/deluge'
p80
sS'plugins_location'
p81
S'/home/yuli/.config/deluge/plugins'
p82
s.

yuli@yuli-laptop:~$ sudo iptables -L
[sudo] password for yuli: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere

---

### Post by lovinglinux on 2009-05-26
Again, please use the *code* tags for large amount of text pasted.

I doesn't help me pasting deluge configuration if you are still using uTorrent for troubleshooting. uTorrent is not native and needs Wine, which has it's own sets of issues. I asked you to do the tests with deluge, so I can eliminate unnecessary variables, facilitating the process of troubleshooting, but if you keep changing torrent clients all the time, then will be difficult to help you. Stick with deluge until you solve the problems, then other clients should also work.

> **yuli_capone said:**
> The port is still "Stealth"

The port is "Stealth", which means is not open. There is nothing in the firewall output indicating that you have opened any port.

> **yuli_capone said:**
> I tested utorrent with an ubuntu release and it's start.I install utorrent anly to check the speed

You shouldn't use uTorrent for troubleshooting, because it has it's own issues, since needs Wine to run.

> **yuli_capone said:**
> A few hours ago i observe that the speed it's up to 400k,but sometines came down to 20k,up again and so on.

This is normal, but could also be due to the fact that your port is not open. Sometimes you connect to peers on countries in which the average bandwidth is very high, like Japan, and a single peer could be responsible for the 400K speed. When this peer disconnect or stops uploading to you, then your speed drops to 20k.

---

### Post by yuli_capone on 2009-05-26
Sorry,I express myself wrong.I used utorrent once when i saw deluge not working,all the time i use deluge,and for troubleshooting
now i see it's working well,i tested other torrents also
What should i do with the Stealth isue?

Sorry for the exprimation problem...

---

### Post by lovinglinux on 2009-05-26
> **yuli_capone said:**
> What should i do with the Stealth isue?

Make sure you are forwarding the correct port from the router and that the firewall has the rule for accepting connections on the same port before starting the torrents.

---

### Post by Paradoxfox93 on 2009-07-21
So I've been having the same problem more or less for some time now.  I've enabled a port in the suggested high range for incoming connections in my router and modem (which also functions as a firewall/router) I don't have a firewall in use on my system (and iptables allows all). i've tried multiple clients and all come to the same issue: No incoming traffic.

This is the reason i quit using comcast and I'm still being throttled =(

I've called the provider before and when I try to explain my problem the only thing I get from them is 'we don't support linux users.' WTF?

I also tested the port scanner above and it reports them closed as well.

Speed tests give me 3Mb/s and U/L of 600Kb/s

On a good torrent, with lots of available seeders I will get speeds of 300-350k/s but I still don't have *incoming connections* because eomsehow the port forwarding isn't working.

It's not because I use DHCP because if that were the case then I would get incoming connections till the next time my computer renewed its IP.

I don't haev this problem in XP.  Interestingly enough this bit of the issue coincides with the issues I have Wining Ragnarok Online.  I can get a connection in Windows easily.  But in Linux I can't connect to the server and when the host traceroutes to me he loses it in one of my ISP's chicago networks.

---

