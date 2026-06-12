---
title: "kubuntu default vnc server crashes"
date: 2006-08-30
forum: Desktop Environments
---

### Post by NiksaVel on 2006-08-30
Hey all,

I recently started using kubuntu to see what it would work out like...  I have ONE single problem that stands out so far - my vnc server proggy crashes on a regular basis. It's the default remote desktop prog that comes with the kubuntu installation.

What happens is when I connect to it from home it works great for a minute or so and after that I loose the connection and can no longer reconnect. When I get back to work to the comp phisically I see the error report screen that comes when a prog crashes....


can anyone tell me:

1. should I use another version of vnc server/which
2. can I make a process autorestart when it crashes
3. is there a way to fix this one from crashing?


thanks!

---

### Post by savohead on 2006-09-05
Hi NiksaVel,
sorry if i have no answer for you, but i just wanted to stress your question with another error message i get from another VNC client on my Kubuntu.
I have an old machine, i installed Kubuntu after having worked on Ubuntu on my usual laptop, i just wanted to make this old workstation work for me all day and control it once in a while from my laptop, i downloaded Krfb, i configured it and with some settings i managed to use it .... but:
First time i tried to launch an application and it started the process without opening the app itself, re-tried and another process appeared without displaying any window.
Second time, it worked fine, but suddenly i got disconnected with an unknown error message sent from the workstation.
I had to change my desktop area manually (on the workstation i mean, not in remote) just to connect again, then when i try to switch to the area in which the application is running, another unknown error message appears.
I hope someone could explain us which server is the best one on kubuntu, i apologise for my confused english, but i'm confused also in italian (sorry).
It's my first post here, but i've read so many up to now that i have to THANK EVERYBODY HERE, you've been a bible for me.
bye.

---

### Post by savohead on 2006-09-05
hi, here i am again for a little update. I found out that my problem was quite known, so there's a solution (not so good but at least it works), i have to set my display settings to 640x480 on my Terminal Server Client just to view my workstation thanks to Krfb, it's simple, i think you could use it. Now i'll try some different things, i'll let you know if i find something better.
bye

---

### Post by NiksaVel on 2006-09-05
I believe I figured out what my problem was....  if any of you whiz guys knows something about networking pls confirm or deny. :D 

I use this comp purely for downloading crap 24/7, and I use ktorrent... I set unlimited # of connections in ktorrent and thats when the problems started. After turning it down to the default 800 limit it worked 100% okay...


cya
NiksaVel

---

