---
title: "Upgraded and now failed to connect to the internet"
date: 2009-06-02
forum: General Help
---

### Post by gamesnepal on 2009-06-02
I have upgraded from my ubuntu 8.10 to 9.04 . First I want to connect to the internet. I want to connect to my adsl connection. In my previous version of ubuntu I connected to the internet by first setting it up using sudo pppoeconf. I did the same this time too because after upgrading I could not use the internet. After setting up the internet it does not work at all. 

I tried "sudo pon dsl-provider" and it says:
> Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
and the internet does not work

I tried the "plog" command and this is what I get

> Jun  2 18:41:31 ashish-desktop pppd[3780]: CHAP authentication failed: Account is occupied
Jun  2 18:41:31 ashish-desktop pppd[3780]: CHAP authentication failed
Jun  2 18:41:31 ashish-desktop pppd[3780]: Connection terminated.
Jun  2 18:41:45 ashish-desktop pppd[3821]: PPP session is 1529
Jun  2 18:41:45 ashish-desktop pppd[3821]: Connected to 00:30:88:10:df:b2 via interface eth0
Jun  2 18:41:45 ashish-desktop pppd[3821]: Using interface ppp1
Jun  2 18:41:45 ashish-desktop pppd[3821]: Connect: ppp1 <--> eth0
Jun  2 18:41:45 ashish-desktop pppd[3821]: CHAP authentication failed: Account is occupied
Jun  2 18:41:45 ashish-desktop pppd[3821]: CHAP authentication failed
Jun  2 18:41:45 ashish-desktop pppd[3821]: Connection terminated.

So how do I connect to the internet? Before upgrading this way used to work :(

---

### Post by Soul-Sing on 2009-06-02
```
sudo pppoeconf
``` please post the outcome

```
/etc/ppp/chap-secrets
```
do you have the correct/syntax username and pass in this file?

---

### Post by diwas on 2009-06-02
Hey great to find someone from Nepal!

Anyways, I get this problem too. Actually, this is like analogous to the error in XP like when the remote server fails to respond (oh this is so common in Nepal!) or when username is wrong. 
BTW the above conclusion is just my analysis.

Now, when i get this message (the above quoted one by you) i try several times...pon and plog. I try poff too. And when everything fails, i restart the router. Usually, when i try the first thing many times, the internet is connected, but u never know. 

Good luck.

---

### Post by diwas on 2009-06-02
> 
Jun 2 18:41:45 ashish-desktop pppd[3821]: CHAP authentication failed: Account is occupied

See this? 
Have u noticed in XP ( I am sayin XP just to make it simple if ur using one) ok ...have u noticed in XP that when sudden power failure happens...or u disconnect it forcefully (ie not by the usual disconnect way), you get error "Username and/or password is incorrect" or smthg. This is the same scenario. (Again from my speculation). 

Try this, connect internet in XP (if u have dual boot) and disconnect it properly..then boot Ubuntu and ```
 sudo pon dsl-provider 
```

---

### Post by gamesnepal on 2009-06-03
Well I checked /etc/ppp/chap-secrets and everything was ok there. My username and password was right.

I found out that it was a problem with my internet service provider. I tried "sudo poff dsl-provider" and then "sudo pon dsl-provider" a couple of times and then it worked. Thanks !

Now the only problem that I have with my ubuntu 9.04 update is the [**_screen resolution problem._**]("http://newyork.ubuntuforums.org/showthread.php?t=1176384")

---

### Post by diwas on 2009-06-03
> **gamesnepal said:**
> Well I checked /etc/ppp/chap-secrets and everything was ok there. My username and password was right.

I found out that it was a problem with my internet service provider. I tried "sudo poff dsl-provider" and then "sudo pon dsl-provider" a couple of times and then it worked. Thanks !

Now the only problem that I have with my ubuntu 9.04 update is the [**_screen resolution problem._**]("http://newyork.ubuntuforums.org/showthread.php?t=1176384")
Great

---

