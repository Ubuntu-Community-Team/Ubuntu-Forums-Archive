---
title: "Forwarding X across multiple machines with ssh?"
date: 2006-01-12
forum: General Help
---

### Post by bb002 on 2006-01-12
I have what I believe to be a rather odd setup. I have four linux boxes, hereby known as A, B, C, D.

A is my home Desktop
B is my Linux Media Center. I have my router forward the ssh port to this machine.
C is a linux server at work that I have an account for.
D is the workstation i use at work.

I can get from D to A but i have to ssh several times. From D to C, C to B, B to A. Despite the long tunnel ssh it is just as fast as sitting in front of the machine.
I can also get from A to D with this path: A to C, C to D. I am able to cut B from the proccess because of my router.

That works great but I can't use X applications beyond the first ssh. Is their a way to make it work?? The X apps will probably lose the race with molasses but that doesn't matter to me.

 How about scp? That way I wont have to transfer files from machine to machine to machine to machine.


I understand that this is a odd request but any help would be appreciated greatly.

---

### Post by Suger on 2006-01-12
From A to D
On D
```
ssh -L 7372:C:7372 C
```
On C
```
ssh -L 7372:B:7372 B[code]
On B
[code] ssh -L 7372:A:22 A
```

Then, on D, in another terminal

```
ssh -p 7372 -Y localhost
```

The other way :
On A :
```
ssh -L 7372:C:7372 C
```
On C
```
ssh -L 7372:D:22
```
and on A again
```
 ssh -p 7372 -Y localhost
```

In fact, because of the known_hosts check, you have to use a Host name instead of localhost for the ssh -Y part. So, in D's ~/.ssh/config, add a line
Host Home
localhost 7372

and all you have to do is ssh -Y Home

HTH

---

### Post by bb002 on 2006-01-12
Thanks Suger. I remember seeing those ssh options in the man pages but I never put two and two together. Seems so obvious now...

I don't understand what you mean by > In fact, because of the known_hosts check, you have to use a Host name instead of localhost for the ssh -Y part. So, in D's ~/.ssh/config, add a line
Host Home
localhost 7372

and all you have to do is ssh -Y Home



---

### Post by Suger on 2006-01-13
Well, ssh checks an rsa key from the computer when it establishes the connection, to prevent a man in the middle attack. If you don't specify that localhost 7372 is different from localhost, he'll refuse to connect to localhost 7372, so you need to give a specific name to localhost 7372 (I suggested Home, as that is where you are connecting to). But my syntax was wrong. What you want is
```
 Host Home
Hostname localhost
Port 7372
```. This way, Home will have a different known_host key from localhost.

---

