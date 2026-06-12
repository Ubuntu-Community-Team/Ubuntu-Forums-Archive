---
title: "Configure the session start programs order"
date: 2009-01-07
forum: Desktop Environments
---

### Post by ztrange on 2009-01-07
Im having a problem with the programs that start when I log in to my computer. I have configured emesene to start with my account but the problem is that it starts before Im auto logged in to my wifi internet so it always gives me this connection error.

Im wondering if there is a way to set the desired order of the services or maybe a delay for a certain program.

I have tried sleep 10s

like this:
sleep 10s;emesene -m --user=mymail@mail.com

but it doesnt work; emesene doesnt launch at all.

Any ideas?

Thanks in advance

---

### Post by ztrange on 2009-01-09
Bump...

Anyone?

---

### Post by ztrange on 2009-02-08
This one is kind of old and no one replied to it... Well, I finally got a solution that works pretty fine, maybe it is too simple but may help someone and I want to mark this solved...

I created a emeseneStart.sh in my home/scrips folder:
```

#!/bin/bash

sleep 50s
emesene -m --user=mail@mymail.com

```

I gave it execution permission
I added a session start program that was linked to that "program"

And voila

PS. I wonder why I cant find the mark as solved button...

---

