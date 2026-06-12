---
title: "Weird network issues ( 400 kb/s but 2MB's takes 5 minutes )."
date: 2009-06-10
forum: General Help
---

### Post by ActiveFrost on 2009-06-10
Don't know from where I should start, so .. Recently ( a week or so ) I've mentioned that my network is acting weird.
When I'm downloading something, it's like, umm .. start/pause/start/pause !
Basically, I'm downloading at 400 kb/s and 2MB file should not take as much as it takes now ( +/- 5m. ).
After taking a closer look at the download process, seems that something is pausing my download .. 2 sec. downloading, 5 sec. waiting, etc.

Any thoughts ?

---

### Post by Het Irv on 2009-06-10
Who is your ISP?
Do you do alot of Downloading? or maybe there is someone else on your connection that is doing alot of downloading?

I sounds like you connection is clogged, there isn't anyone that is doing alot of downloading, or there isn't a high amount of traffic, you may want to try restarting your router and see if that helps

---

### Post by ActiveFrost on 2009-06-10
Yeah, I have another PC, but - I don't use it for downloading ( I do programming stuff on it ).
Speed is good and wireless signal strength is even better ( 1-2 meters distance between my PC and router ).

1 minute ago :
[IMG]http://www.speedtest.net/result/493003109.png[/IMG]

Are there any ways to check my connection for illegal activities ( like illegal connections, etc. ) ?

---

### Post by compiledkernel on 2009-06-10
You can use a variety of tools to determine this. 

I would use slurm and iptraf. 

sudo apt-get install slurm iptraf 

slurm and iptraf are both command line tools, but should be easy enough to figure out how to use once you get them installed. They will certainly give you the information you need to know. 

For slurm -- open up a terminal and type slurm -i (eth0,wlan0,or whatever interface your using). 

For IPtraf -- open up at terminal and type sudo iptraf

---

