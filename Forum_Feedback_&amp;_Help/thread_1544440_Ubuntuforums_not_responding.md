---
title: "Ubuntuforums not responding"
date: 2010-08-02
forum: Forum Feedback &amp; Help
---

### Post by worksofcraft on 2010-08-02
When I try to access these Ubuntuforums.org I get a 'page not found' timeout. So I can suddenly only access them using a proxy server :shock:

What on earth could be causing this? It's very annoying because searches won't work over the proxy :(

 Why would this have started happening and what can I do to use these forums directly again?

---

### Post by TheNerdAL on 2010-08-02
Did you try another browser?

---

### Post by worksofcraft on 2010-08-02
> **TheNerdAL said:**
> Did you try another browser?
Both Google Chrome and FireFox. I also cleared the cache, history and all the cookies... to no avail.

They were working just fine yesterday with direct connexion. It\'s weird because I have had no problems on any other sites!

---

### Post by corrytonapple on 2010-08-02
Happened to me then it worked again. Strange..........

---

### Post by cdenley on 2010-08-02
```

getent hosts ubuntuforums.org
nc -z -v -w 5 ubuntuforums.org 80

```

---

### Post by worksofcraft on 2010-08-02
> **cdenley said:**
> ```

getent hosts ubuntuforums.org
nc -z -v -w 5 ubuntuforums.org 80

```


$> getent hosts ubuntuforums.org
91.189.94.12    ubuntuforums.org
$> ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=41 time=300 ms
...
--- ubuntuforums.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 300.068/301.811/303.501/1.665 ms
$> nc -z -v -w 5 ubuntuforums.org 80
nc: connect to ubuntuforums.org port 80 (tcp) timed out: Operation now in progress

I don\'t know what the nc command is supposed to do yet, meanwhile I also tried rebooting to Windows and also there I can only get on the forums using a proxy like [http://freeproxyserver.net](http://freeproxyserver.net)

yet as you can see I can ping ubuntuforums.org without problems.
It\'s as if they are rejecting my IP address for reasons unknown :shock:

---

### Post by cdenley on 2010-08-02
> **worksofcraft said:**
> 
yet as you can see I can ping ubuntuforums.org without problems.
It's as if they are rejecting my IP address for reasons unknown :shock:

I doubt they are dropping your packets on their end. It works fine for me. The nc (netcat) command simply establishes TCP connection and pipes stdin/stderr to/from the connection. You fail to establish a TCP connection, even though I can connect to that same IP fine. I would suspect either something in your network or your ISP is filtering that traffic. You can connect to any other server fine, though? That is unusual, but the server is online.
```

nc -z -v -w 5 91.189.94.12 80
nc -z -v -w 5 canonical.com 80

```

---

### Post by cariboo on 2010-08-02
> **worksofcraft said:**
> When I try to access these Ubuntuforums.org I get a 'page not found' timeout. So I can suddenly only access them using a proxy server :shock:

What on earth could be causing this? It's very annoying because searches won't work over the proxy :(

 Why would this have started happening and what can I do to use these forums directly again?

I had the same problem last weekend. I contacted my ISP and provided all the pertinent info, it apparently was a routing problem, the rep I talk to passed the problem upstream, and it was repaired less than 24 hours later.

I did mention that I was a moderator on the forum, and the rep actually treated me as if I knew what I was talking about, she didn't ask what os I was using, just asked if I would run tracert to the forums and post the output in the chat session.

Overall I was quite happy with the session.

---

### Post by worksofcraft on 2010-08-02
Hum... suddenly now it's working while a few hours ago it wasn't, so it's still a mystery to me and I suppose it could reoccur anytime.

If I do find out what caused it I'll post again

Thanks for confirming others have seen it too :)

---

