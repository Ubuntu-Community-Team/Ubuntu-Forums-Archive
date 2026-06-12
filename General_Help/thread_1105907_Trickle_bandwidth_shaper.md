---
title: "Trickle bandwidth shaper"
date: 2009-03-25
forum: General Help
---

### Post by tripthethird on 2009-03-25
Hi guys, I have a few questions about Trickle bandwidth shaper at [http://monkey.org/~marius/pages/?page=trickle](http://monkey.org/~marius/pages/?page=trickle)

Is this tool the best bandwidth shaper for Linux? It's feature set is all I need and it's basic/simple enough for me. I don't need it to do anything complex and am very happy with it, just curious if it's the best.

Second, what are the possible use cases for a bandwidth limiter. I've only ever used Trickle for wget, torrent, ftp and firefox. What other apps do you limit using Trickle or any other bandwidth shaper?

That's it :)

TIA

---

### Post by RansomStark on 2009-03-25
Its usefull for apache, if you don't want users accessing your site and consuming all the bandwidth.

---

### Post by tripthethird on 2009-03-25
> **RansomStark said:**
> Its usefull for apache, if you don't want users accessing your site and consuming all the bandwidth.

Sounds interesting! How would you go about doing this? I know one can set priority for HTTP in the /etc/trickled.conf file. Would you do this there?

---

### Post by binbash on 2009-03-25
If you are going to use it with apache there are better options.But trickle is the easiest to use

---

