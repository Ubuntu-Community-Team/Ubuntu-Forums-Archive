---
title: "Please help me with deluge :Some sort of bug I presume"
date: 2009-05-18
forum: General Help
---

### Post by smokyink on 2009-05-18
This is my first tread so I'm sorry if it is in the wrong section (Im new at this)...

My problem is:

I start deluge from the start menu, and everything seems to be ok...

But after a couple of minutes it says "Error: connection timed out" (in tracker status field)

the deluge page becomes blank (as if I don't have any torrents) and

in the bottom of the screen it says "Not Connected":shock:

In order to get it working again i have to go to System monitor and stop the process, and start it over again. 

Also when i look at the status in System Monitor it says "sleeping"


Could anyone please help me?

---

### Post by dhughes on 2009-05-18
I'm not sure, did you try to reinstall it?

 I use Deluge 1.1.6 on 9.04 Jaunty and I find it far better than Transmission (crashes a lot, memory hog).

---

### Post by michy99 on 2009-05-18
If you save your screenshots as .jpg instead of .xcf, people can look at them without having to open gimp.

---

### Post by smokyink on 2009-05-18
no i haven't tried by reinstalling it... 
I will try it now..
(I'm using ubuntu 9.04 as well)

Sory for the image format its my first tread...

---

### Post by smokyink on 2009-05-18
Ok reinstalled it... 
and it did not work...
same problem as before
blank fields

Any suggestions??

Ok...
I tried pausing all torrents before they disapear...

 then switching them back on one by one

(seems to work),but when I switch on a particular torrent 

it goes blank again.. is it posible that a torent is the cause of it??

---

### Post by dhughes on 2009-05-18
You seem to have a lot of torrents going, did you change any of the default settings? 

 Maybe you have too many torrents and not enough bandwidth alloted to allow them to download and upload.

---

### Post by smokyink on 2009-05-18
Nope it went blank again...

i have around 13-14 torrents..
and yes i changed the defout settings
maybe if i set them back to the defaults...

---

### Post by smokyink on 2009-05-18
ok there are no defaults so here are my preferences:

Downloads:

Network:

Use random ports active port 60153

Outgoing ports: random

Network extras:
All checked

Encription:

Inbound:Enabled
Outband:Enabled
level:Either
Incrypt entire system

Bandwidth:

Max connections:500
Max upload slots: 18
Max download speed : -1
Max upload speed: 80
Max half -open connections: 50
Max connection attempts per second:40

Ignore limits on local network: checked
Rate limit IP overhead Checked

per Torrent Bandwidth Usage:

Max connections  -1
max upload slots -1
max download speed -1
max upload speed -1

Deamon:
Port 58846

Allow Remote connections checked

---

### Post by dhughes on 2009-05-18
> **smokyink said:**
> Nope it went blank again...

i have around 13-14 torrents..
and yes i changed the defout settings
maybe if i set them back to the defaults...

 I figured it was at the default and you had too many torrents, too little bandwidth and possibly a closed port. Did you open a port for Deluge in your router?

 I'd say try one torrent and wait to see how it goes, then add one more etc..

> Use random ports active port 60153 maybe that is your problem, try a specific port.

---

### Post by smokyink on 2009-05-18
How do i open a port in my router for deluge?

i tried...It seems to work for now 6- uploading, 3- down loading, 5-stopped (2 of which I think cause the problem, because these 2 are new added today)

---

### Post by dhughes on 2009-05-18
> **smokyink said:**
> How do i open a port in my router for deluge?

i tried...It seems to work for now 6- uploading, 3- down loading, 5-stopped (2 of which I think cause the problem, because these 2 are new added today)

 What kind of router do you use, what brand? Actually the best place is portforward.com they walk you through it, step by step.

 Oh and except for the random incoming port, I use a specific port, compared to your's here is what I use but it's nothing special really just poking around: 

 Global Bandwidth Usage
200
4
-1.0
-1.0
50
20

Per Torrent Bandwidth Usage
-1
-1
-1.0
-1.0

Daemon

[ ] Allow Remote Connections <--not sure of its purpose so I left it unchecked

---

### Post by smokyink on 2009-05-18
hmm thanks for the site
my router/modem is: speed touch 585i v6, Thomsan
at least that's what it says on it

---

### Post by smokyink on 2009-05-22
ok fixed it thanks

---

