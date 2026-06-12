---
title: "Why is setting up a socks5 server so hard?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by natan- on 2006-08-09
Okay so after 6 hours of playing around with 3 different programs which claim to support socks5, i'm nearly ready to reformat and go back to xp.  Okay I will explain what I did so far and maybe someone can find my error. My basic goal is this. I have a headless box at my house that I'm running ubuntu on. I can nx into the box to setup this socks5 server.  I am at school at the moment and I need to run a program through sockscap via a socks5 server to get through a blocked port on my school network.  In windows this was an easy job, maybe 30 minutes max finding a decent server, fill out a config file or just fill in some blanks and pull downs on a gui. No problem.  I figure linux should be the same, but all I have is a headache.

First program I used was SS5. It seems to install as well as can be expected. I setup the config as follows (69.43.65.28 is my school network's ip address):

auth 69.43.65.28 - -
permit - 69.43.65.28 - 0.0.0.0/0 - - - -
permit - 0.0.0.0/0 - 69.43.65.28 - - - -


I then run it from console and bind it (my computers ip address locally is 192.168.1.111):

sudo ss5 -b 192.168.1.111:13022

And then I foward port 13022 to my computer.  No luck, everything seems alright but nothing happens when I attempt to connect.  The log doesn't state anything even tho i see it opening up new ss5 processes and then the connection fails with no prompt.  But after i end all the processes it spits this into the log which doesn't make sense because i allowed these connections in the config:

[09/Aug/2006:10:55:00 EDT] [13554] [ERRO] $ConnectServing$: (Connection timed out).
[09/Aug/2006:10:55:00 EDT] [13554] 69.43.65.28 "" "CONNECT" CONNREFUSED 0 0 - (69.43.65.28:13093 -> 216.98.58.100:6000)

Ofcourse this works fine with random free proxy servers I find online but no luck with this one i'm trying to setup, I tried a few other peices of software such as nylon and still no luck.

---

