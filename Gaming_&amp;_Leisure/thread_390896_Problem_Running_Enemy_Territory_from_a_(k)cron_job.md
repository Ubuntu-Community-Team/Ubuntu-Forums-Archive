---
title: "Problem Running Enemy Territory from a (k)cron job"
date: 2007-03-22
forum: Gaming &amp; Leisure
---

### Post by PowerRanger on 2007-03-22
Hello

I play fairly regularly on an ET server which resets XP after 12 hours of not connecting.  I'd like to set up a cron job which connects and disconnects automatically for me so I don't have to connect before I go to work (it's too tempting if it's a map I really like).
  
I've installed Gnome scheduler and kcron.  I can create an entry in kcron which I can 'run now' which connects just like I'd like, but I can't seem to get the job to run correctly from the scheduler.  I suspect I might need to point it to my profile somehow, but I'm not sure.

My command looks like this:

```
/usr/local/bin/et +connect xxx.xxx.xxx.xxx:portnnn | /usr/bin/uptime >/home/flip/uptime 

```

with xxx...xxx being the ip addr of the server and portnnn being the port number 

I know the _job_ is running because the uptime is logged correctly (I put this in just to test whether the job was running)

In kcron ;
my HOME variable is set to /home/flip
my PATH is set to /usr/local/bin


Any help would surely be appreciated.
Thanks
Mike

---

### Post by PowerRanger on 2007-03-24
I'm trying to get this on the first page again.  

Anyone?

---

### Post by PowerRanger on 2007-03-27
With the job scheduled for 23:20 

My /var/log/syslog shows 

```
Mar 27 23:20:01 flip-dual-screen /USR/SBIN/CRON[27433]: (flip) CMD (/usr/local/bin/et +connect xxx.xxx.xxx.xxx:xxxxxxx)

```


(I've removed the part of the cron job that logs the uptime, since I know the job is firing off, and also changed the syslog entry here with regards to ip and port number to protect the innocent)

I can see the command gets executed as my user, yet the game never starts up.  

Can anyone think of a better forum to post this in?

---

### Post by PowerRanger on 2007-03-29
Well, I spent a little time on IRC and got a little further with this but I'm still having problems.  Turns out I_probably_ need to preface the command with something like ```
DISPLAY=:0 
```.  The problem now is I can't get *anything* that's graphical to fire properly from cron ( this isn't necessarily an Enemy Territory issue).  I determined this by trying to fire Totem from cron.

```
DISPLAY=:0 /usr/bin/totem
```

Again, it runs fine from command line, and I see the cron entry in syslog:
 ```
Mar 29 22:50:02 flip-dual-screen /USR/SBIN/CRON[4549]: (flip) CMD (DISPLAY=:0 /usr/bin/totem)

```

But nothing shows up.  I wonder if nvidia twinview has anything to do with this?  Alas, IRC guys were stumped by this one and Google has failed me so far.

---

### Post by SBFC on 2007-03-29
I apologize in advance for not having any suggestions for you. But I've been interested in getting this to work for a while as well.

If I manage to stumble upon anything useful I'll post it.

Whosgaming by chance?

---

### Post by SBFC on 2007-03-29
Well, good news for me, but prolly not so good for you. 

I was having the same issue as you, where the job would run but ET wouldn't. I tried the solution that was offered to you on IRC and it worked for me.

```

oblivion@nippon:~$ crontab -l
# m h  dom mon dow   command
22 * * * * DISPLAY=:0 /usr/local/bin/et

```

I'm using nvidia, but not twinview, so maybe that is what's preventing it from working on your end.

---

### Post by PowerRanger on 2007-03-29
yup-- WG.  Have you tried to get yours running from cron yet?  LOL I guess I posted just as you were trying it.

---

### Post by SBFC on 2007-03-29
Heh, the 12 hour xp save tipped me off. Not to get too nerdish, but what's your handle?

Runs fine in cron...now if only I could figure out how to automatically kill it. ;)

Trying to find out if you can assign a PID to an application at launch rather than it being assigned one.

---

### Post by PowerRanger on 2007-03-29
I'm PM you my username, just in case WG frowns upon this -- I was gonna run /usr/bin/killall et.x86 a few minutes after connecting.  With Gnome Schedule you can make it to the minute, with Kcron, the granularity is 5 minutes.  The only problem is if server 1 is full, you'll be prompted to connect to #2, of course you won't be there to accept,  so when the killall runs it'll disconnect without restarting the ET XP clock.  Shouldn't be a problem for me in the morning though.

---

### Post by SBFC on 2007-03-30
I haven't used TwinView in Linux yet, so I'm not sure how it behaves...but is your main display actually 0?

This isn't much of a solution...but do you have exim4 installed? Whenever one of your cronjobs runs it sends you a mail with the output.

When I was trying to run ET with cron prior to using 'DISPLAY=:0' I noticed the following error:

```
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

So, if you saw such an error you'd at least know that your proper display isn't 0.

I guess you don't really need exim4 for that though, could just look in /var/mail/<user>.

---

### Post by PowerRanger on 2007-03-30
Good News!  Your last comment is what I needed to figure this out.    The e-mail indicates an X permissions problem;
```

/bin/sh: xhost: not found
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

After Googling for this I determined that I can effect a removal of all security to the X server with the comand with 
```

xhost +
```

A less invasive solution is to add myself to the local X users with the command

xhost local:flip

I read that I can put this in my .bashrc file, I've now done that and I'm gonna see if this will survive a reboot...

---

### Post by PowerRanger on 2007-03-30
Success!  I've spawned totem from cron after a reboot.  I have the 'start' and 'kill' et jobs set up for tomorrow morning, if it doesn't work I'll post back but I'm sure that was the problem.

Mike

---

