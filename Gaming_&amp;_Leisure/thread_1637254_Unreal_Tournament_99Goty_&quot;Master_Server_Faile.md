---
title: "Unreal Tournament 99/Goty &quot;Master Server Failed&quot; error"
date: 2010-12-04
forum: Gaming &amp; Leisure
---

### Post by Sylos on 2010-12-04
Hello and thanks for looking.

I recently reinstalled my UT GOTY and am trying to get some online gaming on the go. Unfortunately, every time I try to look for online games I get the above error saying the connection to the server has timed out. I assume this is because the master server is not the same as when the game was packaged (it is quite a while ago).

Does anybody know where the master servers are now located and how I change the game script to look in the right place (I looked in the .ini but it didnt seem obvious to me where it should go).

Many Thanks

---

### Post by Sylos on 2010-12-04
Update:
I have tried to connect to some IP addresses and have had some success - I get a connection and then get booted for not having the ACE stuff installed (which it is!) but thats another issue. I suppose this shows that its not a firewall issue or anything like that - the problem definitely seems to be with the master server not being accessible to get the list.

I tried adding another entry for the master server in the .ini file but that hasnt worked.

If anyone knows of a current master that works please post me the entry for it.

---

### Post by Sylos on 2010-12-05
...Kerbump!

---

### Post by R33D3M33R on 2010-12-05
ServerActors=IpServer.UdpServerUplink MasterServerAddress=unreal.epicgames.com MasterServerPort=27900
ServerActors=IpServer.UdpServerUplink MasterServerAddress=master0.gamespy.com MasterServerPort=27900
ServerActors=IpServer.UdpServerUplink MasterServerAddress=master.mplayer.com MasterServerPort=27900

Default servers, work great. Check your firewall/DNS settings.

---

### Post by Sylos on 2010-12-05
Hello Redeemer, thanks for the post.

Im not using any extra firewall protection or unusual network set up - just connected via ethernet to router. I also play ut2003 and that isnt having any problems - nor is saurbraten or Alien Arena. Also, I would have thought that if I can connect directly to a server then that would show that it isnt a firewall/network issue. I know very little about networks so maybe Im wrong on that.

Im at a bit of a loss as to how to diagnose the problem. Do you have any suggestions?

---

### Post by Sylos on 2010-12-06
My router (BTHomeHub) does have a firewall that I assume could be blocking the port. Could somebody confirm if the following is correct:

1. The unreal tournament.ini file states that master servers should be on port 27900 so if I set my firewall to forward all trafick for this to my 27900 PC port as TCP will this ensure that the connection is allowed?
2. Am I opening myself up to a world of pain by opening this path? I know any hole in the firewall is a weakness but I wonder what damage can be done from allowing access on this one additional port?

Many Thanks

---

### Post by R33D3M33R on 2010-12-06
There is no need to open this port. I'm also behind the router and everything works without opening ports. Try to ping the master server.

```
ping unreal.epicgames.com
```

---

### Post by Sylos on 2010-12-06
Thanks Reedemeer.
I get no response when trying to ping the epic games address. Something appears to be preventing my connection. Im looking at the output of iptables -L but nothing seems to be specifically blocked.
Im confused!

EDIT: might be worth mentioning I do use IPBlock from time to time but I havent had it running when trying to connect. As it is a front for iptables I suppose it is possible I could have unwittingly altered the iptables rules.

---

### Post by Sylos on 2010-12-06
I just tried to ping one of the other server addresses from my unrealtournament.ini and got a positive response so I thought I'd try getting rid of unreal.epicgames.com from the .ini - it worked! I now have a healthy looking server list.

Many Thanks Reedemeer.

---

### Post by R33D3M33R on 2010-12-06
Glad I could help :).

---

### Post by Sylos on 2010-12-09
Sad to say this problem has returned. I had one night where it was ok - then the last two have been the same as before - master server times out. 

I still dont get a ping response from most of the servers - qtracker gave one but still no population of the server list in game.

Any help would be very much appreciated.

---

### Post by Sylos on 2010-12-10
Humpty Bumpty....

---

### Post by rizzeh on 2010-12-10
Resolves here after second attempt: 

```
Resolving unreal.epicgames.com...
Resolved unreal.epicgames.com (199.255.40.180)
Resolving utmaster.epicgames.com...
Resolved utmaster.epicgames.com (216.27.56.5)
UBrowserGSpyLink: Master Server is utmaster.epicgames.com:28900
UBrowserGSpyLink: Couldn't connect to master server.
Resolving master0.gamespy.com...
CheckConnectionAttempt: Error while checking socket status.
Resolved master0.gamespy.com (69.10.30.248)
UBrowserGSpyLink: Master Server is master0.gamespy.com:28900
```

---

### Post by Sylos on 2010-12-11
Cheers for the post.

Im dont seem to get a response no matter how many times I try. Also, for me, attmepting to ping the master0.gamespy address just gets "destination port unreachable". This is really winding me up. Im gonna try installing on a different machine in a couple of days and see if I get the same error.

Any other suggestions gratefully received.

---

