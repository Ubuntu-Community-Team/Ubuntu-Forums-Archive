---
title: "Evolution goes &quot;completely grey&quot; (or gray)"
date: 2011-02-22
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-02-22
I'm happily reading my IMAP connected email with Evolution v2.28.3
when all of the application windows "go grey" and stop responding.
[highlight]Q1.[/highlight] Can someone explain what is happening?
[highlight]Q2.[/highlight] Can someone direct me to corrective action
(so it stops happening) instead of work around (so symptoms go away this time)?

If I wait long enough, they wake up and I can resume whatever I was doing. Alternately, I can use **killall evolution** from a shell
and restart the program.

This is a real bear to deal with as it happens several times each day.

Merci d'avance,
~~~ 0;-Dan

---

### Post by grahammechanical on 2011-02-22
Something is using up all the system memory RAM. If you run System Monitor you will see that the CPU is working close to 100% swapping data in and out of the swap partition.

Regards.

---

### Post by deconstrained on 2011-02-22
The graying is a default behavior in Ubuntu's Compiz (window actions) -- it indicates that the program is hung/frozen. By default behavior I mean the graying (not the freezing) :p.

---

### Post by SaintDanBert on 2011-02-22
> **deconstrained said:**
> The graying is a default behavior in Ubuntu's Compiz (window actions) -- it indicates that the program is hung/frozen. By default behavior I mean the graying (not the freezing) :p.

Okay!! "hung program" makes a lot of sense.  **htop** and such don't show high CPU use or zero availble RAM.

Can anyone shed light on what would cause Evolution to "hang"?

Where do I find the associated Compiz settings so that I can see if some other behavior makes more sense to me?

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-02-28
Bump!!

The stall events are getting more frequent. While using Evolution v2.28.3:
[list]
[*] select and read a message, click delete ... evo stalls.
[*] try to move to the next message in a folder ... evo stalls.
[*] try to select an alternate folder ... evo stalls
[*] working in another application and try to reselect evo ... evo stalls
[*] working in a browser select a mailto link ... evo stalls
[/list]

Another part of the puzzle lies with the fact that I'm reading all of my email with IMAP connections. During these stalled evo events, I continue to have access to the internet and to the server hosting the IMAP.

Can anyone help me here?

Merci d'avance,
~~~ 0;-Dan

PS/ The rest of the workstation is Ubuntu Lucid with current patches.

---

### Post by SaintDanBert on 2011-02-28
Bump!! BUMP!!!

It seems that evolution spends a lot of effort "Pinging IMAP Server ..."
for some reason. There seems to be some correlation between these status messages and the stalling behavior.

Ideas?
~~~ 0;-Dan

---

### Post by Rasputin69 on 2011-02-28
> **SaintDanBert said:**
> I'm happily reading my IMAP connected email with Evolution v2.28.3
when all of the application windows "go grey" and stop responding.
[highlight]Q1.[/highlight] Can someone explain what is happening?
[highlight]Q2.[/highlight] Can someone direct me to corrective action
(so it stops happening) instead of work around (so symptoms go away this time)?

If I wait long enough, they wake up and I can resume whatever I was doing. Alternately, I can use **killall evolution** from a shell
and restart the program.

This is a real bear to deal with as it happens several times each day.

Merci d'avance,
~~~ 0;-Dan

I had the same problem.

I went to [Thunderbird]("http://www.mozillamessaging.com/en-US/thunderbird/"). The problem did not go away but was less frequent.

Only other suggestion is more ram if you have the capacity. It's cheap.

---

### Post by SaintDanBert on 2011-02-28
> **Rasputin69 said:**
> 
...
Only other suggestion is more ram if you have the capacity. It's cheap.

I have 3GB ram with 6GB swap (seldom used).  The box supports up to 4GB ram. I'm running the PAE variant of the 32-bit kernel.

I don't think this is a RAM issue. I suspect that Evolution makes some request that

takes



forever


to


get




completed.

---

### Post by Copper Bezel on 2011-03-01
I got frustrated with Evolution after it failed to recognize incoming messages, claimed to fail to send but sent anyway, and so on just a few too many times, but I've never had resource problems with it and I'm running on a netbook. And I was using IMAP, too. Very strange. I wonder if your particular server is doing something Evolution panics over?

> Alternately, I can use killall evolution from a shell
and restart the program.

Quick tip on this - if you don't want to have to hop into a shell to kill nonresponsive programs, you could always set a  Compiz command keybinding to xkill. Hit the keystroke, and you can just click on the program window; it'll kill it as dead as killall does.

---

### Post by mcduck on 2011-03-01
> **SaintDanBert said:**
> 
Where do I find the associated Compiz settings so that I can see if some other behavior makes more sense to me?

Thanks,
~~~ 0;-Dan
That wouldn't help you at all. The program would still be frozen, only you wouldn't et such visual indication of it's state, it just wouldn't respond.

Instead you should try to find out what causes the Evolution to freeze. Whatever the reason is, it's not Compiz, that's just telling you that Evolution is frozen (or taking very long time to respond)

---

### Post by beavis5551 on 2011-03-01
how big is your IMAP mailbox exactly?
I had instances where IMAP-clients would stall when handling very large amounts of emails...

just a point to think about...

---

### Post by SaintDanBert on 2011-03-02
> **beavis5551 said:**
> how big is your IMAP mailbox exactly?
I had instances where IMAP-clients would stall when handling very large amounts of emails...

just a point to think about...

That is a great question. I'll look and see what is going on over there.
I usually leave "last month" plus the "current month" online. What with heavy traffic and a few attachments, things could get large.

Cheers,
~~~ 0;-Dan

---

