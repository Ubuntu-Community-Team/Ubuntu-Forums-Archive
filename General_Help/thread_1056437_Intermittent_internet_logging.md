---
title: "Intermittent internet logging"
date: 2009-01-31
forum: General Help
---

### Post by akwusmc on 2009-01-31
All,

I need to document an intermittent internet connectivity problem so I can present to my provider.

I'm running Fiesty (ok, I know, I know ...) on my laptop through a Linksys WRT54 wireless router, and my wife is connected by wire. We often lose connectivity at the same time, and magically get it back at the same time. Needless to say, tech support is less than helpful.

Is there any program I can use to constantly check for connectivity (even just a ping will do) and log the results?

Any help is appreciated!

TIA,

Anthony

Acer Aspire 5400/ Turion64
Ubuntu 7.04

---

### Post by tom66 on 2009-01-31
Run *ping* with the -i parameter (interval in seconds). Then pipe it to a text file. For example, this would ping google.com every 60 seconds and log it to a text file:

```

ping google.com -i 60 > pingtest.txt

```

However, that doesn't timestamp the results, but if you know the file is created at a certain time and every 60 seconds a ping is executed, you can work it out quite easily.

---

### Post by kavon89 on 2009-01-31
Open up Terminal and enter this command:

> ping google.com -c 20 -i 3

Here is how it works so you can modify it however you want. Essentially the ping program will request a response from google.com every 3 seconds (-i flag means interval) 20 times (-c flag means count). So this command will actively ping google for a minute, feel free to change the 20 to 40 if you want it to last 2 minutes or increase the interval time to 5 seconds etc.

Note any lost packets or no responses and show your provider (especially if there is a big section saying that it lost many packets, thats a sign that your connection just went dry). Remember that right-click is the only way to copy in Terminal, you can't use Ctrl+C, that does something different.

---

### Post by akwusmc on 2009-01-31
> **tom66 said:**
> Run *ping* with the -i parameter (interval in seconds). Then pipe it to a text file. For example, this would ping google.com every 60 seconds and log it to a text file:

```

ping google.com -i 60 > pingtest.txt

```

However, that doesn't timestamp the results, but if you know the file is created at a certain time and every 60 seconds a ping is executed, you can work it out quite easily.

Tom,

That helps a bunch!

I ran that code for about 5 minutes ..... I assume that if my milliseconds are the amount of time for the pinged site to respond, and if it's more than 60,000 ms, then I've got a loss of connectivity.

Anthony

---

