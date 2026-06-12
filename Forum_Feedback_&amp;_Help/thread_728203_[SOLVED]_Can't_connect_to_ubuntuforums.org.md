---
title: "[SOLVED] Can't connect to ubuntuforums.org"
date: 2008-03-18
forum: Forum Feedback &amp; Help
---

### Post by POW R TOC H on 2008-03-18
I can't connect to ubuntuforums.org with my browser. It gives me the "Unable to connect" error (firefox). I surf from my home, and have no firewalls or browsing limitations whatsoever... Even more strange, is the fact that I can't even ping ubuntuforums.org from console!!!

I have registered and posted on the forum by using online-proxy.net

Any idea on how to fix this?
Please, help :(

---

### Post by p_quarles on 2008-03-18
Can you try pinging the numerical IP address? It's possible that this is a DNS resolution issue. The address is:
```
91.189.94.186
```
Let us know what results you get.

Also, what operating system are you currently using?

---

### Post by POW R TOC H on 2008-03-18
Ping says the destination is unreachable, even if I ping the IP:
From 91.185.96.177 icmp_seq=2 Destination Host Unreachable

I'm using Ubuntu 7.10
Kernel version :
2.6.22-14-generic

I can't connect to any ubuntu server (forum, main site) for about 20 days...

Need any more info?

---

### Post by p_quarles on 2008-03-18
Can you paste the output of this?:
```
traceroute ubuntuforums.org
```
Please wrap the output inside the [noparse]```
...
```[/noparse] tags, since the output will likely be long. This may help isolate the point at which the connection problem is occurring. 

Aside from that, just a couple questions: 1) Are you having problems accessing any other sites? 2) Are you in a country which may be blocking some internet traffic?

---

### Post by POW R TOC H on 2008-03-18
Ok, here it is : (i tried with numerical adress - same result!)
```

traceroute to ubuntuforums.org (91.189.94.186), 30 hops max, 40 byte packets
 1  172.18.0.1 (172.18.0.1)  10.718 ms * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  91.185.96.177 (91.185.96.177)  3050.764 ms !H * *
```

I have no problems with other sites :(
As far as I know, there are no restrictions in my country (Serbia).
I also asked my ISP, they said they aren't blocking anything...

---

### Post by POW R TOC H on 2008-03-18
Also, I can't connect to ubuntu repositories (I can use only third party ones)...

---

### Post by p_quarles on 2008-03-18
Hmm. This is very strange. It makes sense that both the forums and the repositories would get the same result, since they are part of the same server farm. What's strange is that -- based on the results of the traceroute test -- the problem seems to occurring at your own router/gateway. 

I'm not 100 percent sure that I'm reading those results correctly, but could you check the settings on any modem or router you are using? Is it possible that they are somehow blocking this specific IP range?

---

### Post by POW R TOC H on 2008-03-18
I'm using CISCO's Scientific Atlanta, but there are no such settings. I used OpenSUSE and Windows before, and I could access ubuntu forums, and ubuntu sites... It was with the same router, same ISP, everything was the same :(

Thank you for helping :D !

---

### Post by p_quarles on 2008-03-18
Well, then, I'm officially puzzled. Maybe someone else here will have ideas for further investigation.

---

### Post by POW R TOC H on 2008-03-18
By the way, the model of the router is EPC2100R2, if it matters...
Sorry for not editing my posts, for some reason this online proxy won't let me do that...

---

### Post by LaRoza on 2008-03-18
Is there a chance, admins, that an IP block is doing this?

---

### Post by mips on 2008-03-19
please post output of **ifconfig -a**

next restart your networking with:
```
sudo /etc/init.d/networking restart
```

After the network restart do things work or do they stay the same?

If you reboot your pc what does it say in  **/var/log/messages**

Another thing you can try is to disconnect the lan cable and switch of your cable modem for a few minutes. After reconnecting and switching on it might work.

I've seen this before. If you search here for scientific atlanta and EPC2100R2 you will find other people with similair problems.

---

### Post by POW R TOC H on 2008-03-21
I called my ISP again, and this time I was a bit more unpleasant... They fixed it, whatever that "it" might be. Sorry for posting the problem here, as it has nothing to do with this forum or ubuntu servers (as it seems)...

---

### Post by LaRoza on 2008-03-21
> **POW R TOC H said:**
> I called my ISP again, and this time I was a bit more unpleasant... They fixed it, whatever that "it" might be. Sorry for posting the problem here, as it has nothing to do with this forum or ubuntu servers (as it seems)...

Quite alright. Glad it has been worked out.

---

### Post by Forrest Gumpp on 2008-03-21
@POW R TOC H

Can you mark your thread as [SOLVED]?  Only you can do it.  (Just for the convenience of other users of the Forums.)

If this should itself appear to be a worry, think 'Stickies':)

BTW, Yours was a good question.  I have to admit that the thought has crossed my mind at times that there would be some who would be quite pleased should there be problems for users in accessing the UF site.  But then again, I'm probably paranoid!

---

### Post by POW R TOC H on 2008-03-22
Sorry, I didn't see your post soon enough :(

---

