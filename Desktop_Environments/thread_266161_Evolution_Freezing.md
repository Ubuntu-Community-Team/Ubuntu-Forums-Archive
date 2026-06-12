---
title: "Evolution Freezing"
date: 2006-09-26
forum: Desktop Environments
---

### Post by ramjet_1953 on 2006-09-26
Hi, Guys :) 

I have a problem with Evolution freezing.
I have 3 email accounts configured on it. Two POP and one IMAP.
When it freezes, there is a message in the bottom left saying Pinging IMAP Server.
The screen can't be minimised or the progrqm terminated. Only a re-start clears the problem.
It doesn't happen all of the time, but happens often enough to be an annoyance.

Any ideas?

Roger 8)

---

### Post by Mr Frosti on 2006-09-26
To begin, restarting is a very drastic step. It should only be used as a last resort. Next time this happens, try running the command "killall evolution" from a terminal, or in the run field. 

Also, you can run Evolution from a terminal that may help to answer some of the questions about what is happening in the background. Please post the results of running Evolution in a terminal to see if anything indicates an issue.

As a word of caution, Evolution seems to lock up for me pretty frequently, so you are not alone in this department. If you are just using POP and IMAP, you are probably better serverd using Mozilla Thunderbird. Evolution's power comes in its connections to GroupWise and Exchange, which you don't need anyway.

---

### Post by ramjet_1953 on 2006-09-27
Thanks for the advice.
I'd like to stick with Evolution, if possible, as I like the calandar and time scheduling. Very similar to what I had with Outlook in Windows.

Roger :)

---

### Post by mun3kh on 2006-10-11
I too am having trouble with Evolution freezing in various
 manners. As you have said though, the only people who _need_
 evolution are those connecting to GroupWise or an Exchange
 server.

I am the latter, Exchange is the email server setup at my job.
 After the initial trouble with having to mannualy adjust the
 server names in gconf, I thought I'd cracked it.

Soon I was to be dissappointed. Evolution seems to be doubleplus
 bad. 

It consumes over 45 threads whilst running, not including the
 backend items like evolution-exchange. This has caused me to
 encounter this sometimes, when opening a terminal:

/usr/bin/lesspipe: fork: Resource temporarily unavailable

This is very bad. I had hoped that maxing out on the ability to
 fork a new process in, of all things, a debian based distro,
 would have been covered for basic operation.

It's just happened again when I tried to look at the manual for 
ps. I only have about 130 processes running when this happens.

Why is evolution so resource hungry, or am I missing something?

---

### Post by Mr Frosti on 2006-10-16
I know it has been a while but I have some great feedback. I have been running Evolution 2.16 for about a month now and I have YET to have it lock up on me. *knock on wood*.

It is fast, stable, and a lot prettier to look at. Specifically, the Exchange plugin has been really improved. It is faster, and does more in less time, with less resources.

I can say that I will probably never go back. Now if it would come with the power of Thunderbird's junk controls, I couldn't ask for anything else...

---

### Post by mun3kh on 2006-10-17
I'm using evolution 2.6, as reported by:

```

ian@ian-desktop:~$ evolution --version
Gnome evolution-2.6 2.6.1

```

Does this mean you are using an earlier version of evolution? How do you downgrade the version of evolution on dapper?

---

### Post by Mr Frosti on 2006-10-18
> Does this mean you are using an earlier version of evolution? How do you downgrade the version of evolution on dapper?

I apologize, I meant Evolution 2.8.1

---

### Post by mun3kh on 2006-10-18
I'm in the middle of a dist-upgrade to the Edgy Eft. If all goes well I should have a fast and stable Evolution in 5 mins.

Did you have any issues with evolution due to the upgrade, or did it work correctly straight off?

---

