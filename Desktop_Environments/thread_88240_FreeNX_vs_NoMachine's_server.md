---
title: "FreeNX vs NoMachine's server"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Juzz on 2005-11-09
Hiyas,

Anyone who has bought the Nomachine server?
I would really like to know how it compares and whether or not a few different things are possible in the paid version.

[LIST]
[*]Can you delete sessions in the session list? (the current list is just growing and growing and growing)
[*]Can you resume sessions where you lost the connection? (on my workplace I tend to lose connection and I suspect it is some of my coworkers streaming that is messing with the bandwidth)
[/LIST]
I am getting to a point where I would like to pay for those possibilities, since I otherwise have to log in via putty and killing nxnode and nxagent processes to allow me to start up firefox again...

I'd really appreciate some info about the issues above.

Cheers
Juzz

---

### Post by Juzz on 2005-11-10
Has noone tried the nomachine's pay server?

---

### Post by rkelly on 2005-11-18
[quote=Juzz]HI am getting to a point where I would like to pay for those possibilities, since I otherwise have to log in via putty and killing nxnode and nxagent processes to allow me to start up firefox again...
[/quote] 
I had about the same problems when I experimented with FreeNX.
I disabled the multimedia support in the FreeNX client to sort this out.
Seems to me that this is a problem in the FreeNX server, but I am not sure about that.

---

### Post by Daz on 2005-11-18
[QUOTE=Juzz]Can you delete sessions in the session list? (the current list is just growing and growing and growing)[/QUOTE]

Hi Juzz,

In answer to your first question, yes, but you can also do this with FreeNX.  All you have to do is the following commands...

To see the list of open sessions:

```
sudo nxserver --list
```

Then, to kill off all of the open sessions (you may want to do this through SSH rather than an NX session as it will kill the current NX session too!):

```
sudo nxserver --terminate ***username***
```

Hope this helps relieve some of your frustrations.

Daz :)

P.S. I have only tried a demo of the paid for server and I think it was able to resume sessions, but i'm not 100% sure... :???: That said, the personal edition of the server is quite cheap, so if it can resume sessions, it might well be the way forward for you if you are having interupts regularly.

---

