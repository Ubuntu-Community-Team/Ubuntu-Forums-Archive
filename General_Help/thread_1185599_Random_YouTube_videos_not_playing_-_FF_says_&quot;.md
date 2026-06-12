---
title: "Random YouTube videos not playing - FF says &quot;waiting ...&quot;"
date: 2009-06-12
forum: General Help
---

### Post by imbjr on 2009-06-12
Randomly, YouTube videos will not play and Firefox sits there going "Waiting for [www.youtube.com](www.youtube.com) ..."

Eventually, after visiting other videos and returning to the one I wanted to see, it works.

Wireshark does not reveal anything. I know that certain subdomains will not resolve right under Ubuntu, if they end in a dash for example, but I did not find anything like that.

I believe this has only been going on since Jaunty too.

Anyone else experience this?

---

### Post by jonobr on 2009-06-12
I would recommend you compare this against something like seamonkey or epiphany and see if you can narrow it down to a FF issue or other..

Also, with Wireshark, are you still seeing the stream being received when it has a problem?

I believe the streaming is TCP if thats the case and the stream is running, the transport layer must be acking the recieved packets as its recieving more -possibly highlighting a application issue?

---

### Post by imbjr on 2009-06-13
Youtube may have had a hiccup yesterday, but I did try Epiphany too and got similar results.

As for the stream, it's hard see what exactly was going on [1] - I mainly checked it to see that were no DNS lookups with a trailing dash in them.

[1] Thinking about this some more, there's no indication that any traffic was received - might have to check again tho.

---

