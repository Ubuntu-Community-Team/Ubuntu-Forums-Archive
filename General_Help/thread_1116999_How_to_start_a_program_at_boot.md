---
title: "How to start a program at boot?"
date: 2009-04-05
forum: General Help
---

### Post by mackrackit on 2009-04-05
Hi all,

Sorry to ask such a basic question...

I have a program called Run Basic that I would like to have start at boot like apache zoneminder does.

The file to start is:
/home/shop/rb101/rb.im

Where and how do I do this?  I am using 8.04

Thanks!!!

---

### Post by Vadi on 2009-04-05
*System - Preferences - Sessions - Add* should do it.

---

### Post by hessczoo on 2009-04-05
System -> Preferences -> Startup Applications

Then use the add option to add in the command to run.

---

### Post by mackrackit on 2009-04-05
Thanks for the replies.

I thought 

System - Preferences - Sessions

Was for after log-in?

Tried it and I it does not start after log-in either.

When I start this normally from a terminal I use this:
```

cd rb101

./rbp rb.im

```
In the sessions add box I put:

/home/shop/rb101/ ./rbp rb.im

No errors...just nothing..

I am wanting the program to start before log-in.

Thanks,
Dave

---

### Post by 3Miro on 2009-04-05
Try to use:

```

/home/shop/rb101/rb.im

```

---

### Post by Vadi on 2009-04-05
This will do it after, yes. Before means tinkering with [Upstart]("http://upstart.ubuntu.com/"), I think. And I haven't went into that terrirotory.

---

### Post by Slim Odds on 2009-04-05
The sessions thing only starts at login. If you want something to start at boot time, put it in /etc/init.d/rc.local (that's what it's there for).

---

### Post by mackrackit on 2009-04-05
Been playing with rc.local...Still no luck.

How do I convert what I do in a terminal
```

cd rb101

./rbp rb.im
```
to something that works in rc.local?

I have tried
/home/shop/rb101/rb.im
and
/home/shop/rb101 ./rb.im

What am I doing wrong?

Thanks,
Dave

---

### Post by Slim Odds on 2009-04-06
```
/home/shop/rb101/rbp /home/shop/rb101/rb.im
```

---

### Post by mackrackit on 2009-04-15
Thanks everyone for trying to help me with this.  Come to find out the reason it would not work is that Run Basic is not a headless program.

There is a place for newbies... Where is the place for ditzes???:rolleyes:

---

### Post by Vadi on 2009-04-15
Ah. So only sessions will work then...

---

### Post by mackrackit on 2009-04-15
Yep, I talked to the developer of Run Basic and he has, I guess you would call it a pre beta headless version, that I am going to try in a day or so.

That should fix my problem.

Thanks again for everyones help.
Dave

---

