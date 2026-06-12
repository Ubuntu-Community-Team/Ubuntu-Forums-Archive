---
title: "Latest cairo update"
date: 2006-07-02
forum: Desktop Environments
---

### Post by viraptor on 2006-07-02
There's something wrong with today's libcairo update:

libcairo2:
  Requires: libfreetype6 (>=2.2.1), but 2.1.10-1ubuntu2.1 is installed.
(message translation to Eng. mine - I'm not en_US here, so original may be different)

And it's true - libfreetype is 2.1.10-1 here and there's no 2.2.1 update. Should this be on launchpad, or are packages problems reported in some other place?

---

### Post by Anduu on 2006-07-02
I'm sure they just haven't put up the updated dependencies yet...give it time.

---

### Post by viraptor on 2006-07-02
Ok - but seeing that kind of thing during repos update is one thing...
Seeing lone package with unresolvable dependencies for a whole day is something completely different - it's II time in official Dapper (1/month?) this happens. Aren't repos changes tested on a clean system before publication?

I know this seems paranoid, but there are some publication rules... aren't there? Shouldn't that be tested?...

---

### Post by kpkeerthi on 2006-07-02
Same problem here. I thought it was the compiz update that caused this problem...
[http://www.compiz.net/viewtopic.php?pid=11339#p11339](http://www.compiz.net/viewtopic.php?pid=11339#p11339)

---

### Post by rko618 on 2006-07-03
Same problem here.

How can we go about getting this fixed in the repos?

---

### Post by knn on 2006-07-03
Posted on Compiz forums three hours ago

> 

I'm sorry about that, I will fix it tomorrow, for now i'm going to bed.



---

### Post by tokez on 2006-07-03
Thanks for the update, knn.

---

### Post by Anduu on 2006-07-03
OK I think it is time to bring this to someone important's attention...it has been 2 days now.

Who/where does one need to go?

---

### Post by knn on 2006-07-03
[QUOTE=Anduu]OK I think it is time to bring this to someone important's attention...it has been 2 days now.

Who/where does one need to go?[/QUOTE]

Wait. See my post above.

---

### Post by Anduu on 2006-07-03
[QUOTE=knn]Wait. See my post above.[/QUOTE]

#-o 

Didn't even see that...heh.

---

### Post by Anduu on 2006-07-04
Grrrr....

---

### Post by nocturn on 2006-07-05
What do you mean?

---

### Post by Anduu on 2006-07-05
[QUOTE=nocturn]What do you mean?[/QUOTE]

I mean it is now going on day 3 since he said he would fix it...

---

### Post by viraptor on 2006-07-06
Ahhh... sorry 'bout writing here about that update. I thought it was stock ubuntu package, but that one was quinn's from external repo. That changes some things :)

---

### Post by Anduu on 2006-07-06
Anywho they have it fixed now =D>

---

### Post by mcduck on 2006-07-06
[QUOTE=Anduu]I mean it is now going on day 3 since he said he would fix it...[/QUOTE]
He had to downgrade some packages on his system to compile a working package, and that broke some things on his system so he had to fix it before making those new packages. 

Anyway, the problem is fixed now :)

---

