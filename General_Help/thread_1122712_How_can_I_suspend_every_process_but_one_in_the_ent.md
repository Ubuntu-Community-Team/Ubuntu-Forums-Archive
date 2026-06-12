---
title: "How can I suspend every process but one in the entire computer?"
date: 2009-04-11
forum: General Help
---

### Post by Cadeyrn on 2009-04-11
The strangest thing just happened to me--I began a Firefox download of 500MB last night and let it run. With my 14KB/sec download speed and 112K, it only got to 300 by this morning. Bored, I opened up a game that ended up freezing the entire system with occasional sounds and mouse movements, or so I thought. And all the while, my !DownThemAll window said 9.73MB/sec, which I thought was a mistake.

After a half-hour of every trick in the book not working, I force-restarted the computer. When it turned back on I continued to resume the download, but it said it was done. I thought it was a size mismatch, but Firefox said the result was the exact size of the file--581.4 MB. I looked at the file through many ways; through the Terminal, through the Properties, and it all checked out. It was truly that big.

When I tried running it it worked flawlessly. There was no 200-MB fill-in of nothingness; it was all there. Long story short, one video game allowed Firefox to automatically turn itself into a super CPU-hogger, and it downloaded 200MB in 30 MINUTES OR LESS on an internet with an average download speed of 14KB/sec. And what's more is the server's cap is 500KB/sec. Or so they say.

I've discovered the secret to super-downloading and I intend to use it. Although I'm definitely not the first, however, I can't find anything about how to manually repeat what happened to me through a Google search. So I've come here--how can I suspend every single process, vital ones and all, except Firefox and/or make Firefox magically have a Nice value of a wayyyyy negative number (past -20)?

---

### Post by spupy on 2009-04-11
> **Cadeyrn said:**
> ...and/or make Firefox magically have a Nice value of a wayyyyy negative number (past -20)?

You can use the **renice** command. But this will only affect the processor time firefox gets, not how much of the bandwidth it hogs.

---

