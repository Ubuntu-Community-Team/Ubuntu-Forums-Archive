---
title: "2 Users logged in? or is it  1?"
date: 2009-02-10
forum: General Help
---

### Post by thinkdez on 2009-02-10
I have checked google and the forums yet no luck to finding this answer.  I am hoping that somebody has a proper answer.

When I run the uptime command I get the following:
```
~$ uptime
 13:14:56 up 19 days, 21:13,  2 users,  load average: 0.00, 0.00, 0.05

```

I noticed that it showed 2 users logged in so I was curious as to who the other user is since I am the only one on the system so I ran the 'w' command to see and got the following:
```
$ w
 13:16:30 up 19 days, 21:15,  2 users,  load average: 0.00, 0.00, 0.04
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
mike  pts/1    192.168.25.50    13:04    0.00s  0.22s  0.01s w

```

So I thought that is weird 2 users but only one session is open!  So I did a ps aux and I don't see anybody else logged in.  So this puzzles me as I see no indication of a second user yet its telling me that there are 2 users.  

I read somewhere that because I am logged into the system via ssh that it will log me as 2 users but I have disproved this as when I setup a second ssh session it shows only 3 users.
```
$ w
 13:19:34 up 19 days, 21:18,  3 users,  load average: 0.00, 0.00, 0.02
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
mike  pts/1    192.168.25.50    13:04    2:02m  0.22s  0.22s -bash
mike  pts/2    192.168.25.50    13:19    0.00s  0.21s  0.01s w

```


I hope somebody has the answer to this.  Its puzzling!

---

### Post by TCSnyder on 2009-02-10
it is more a server check to see who is on the server.

one user is your gui and apps

the other is your terminal session

if you open 2 terminals you have 3 users :)

in a server there is no gui so it only shows 1 user

** correct me if i am wrong **

---

### Post by Tony Flury on 2009-02-10
do this 
```

$ users

```

in the terminal - i just did - my user is logged on twice - i guess Gnome counts as one login, and the terminal counts as a second

open a 2nd terminal - you will now three logged in users.

---

### Post by johnjohn2 on 2009-02-10
> **Tony Flury said:**
> do this 
```

$ users

```

in the terminal - i just did - my user is logged on twice - i guess Gnome counts as one login, and the terminal counts as a second

open a 2nd terminal - you will now three logged in users.

same here and it is weird

---

### Post by TCSnyder on 2009-02-10
i think it does it because in the terminal you can switch users

```
su - "USERNAME"
```

so then one more person is logged in. if it didnt show the terminal it wouldn't show the second user

---

### Post by thinkdez on 2009-02-14
Hey thanks for the replies.
I forgot to mention that I am using Ubuntu Server so no GUI/X-Server and I am not logged into the physical machine.  The 'users' command only shows that I am logged in.

Also a ps -ef does not show any other user except me in my session logged in.

Any other Ideas?

---

### Post by thinkdez on 2009-03-03
Can anybody elaborate further?  I just rebooted the box and it still states 2 users when I know there is only 1 user active on the system.

---

### Post by thinkdez on 2009-09-01
If anyone cares after some patching/upgrading the issue no longer presents itself.  Seems to have been a bug or something that is now fixed.

---

