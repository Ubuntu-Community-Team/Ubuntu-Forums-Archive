---
title: "Klibido Problems"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Pootas on 2006-07-25
Hi,

I'm running Dapper with Klibido to grab nzb files. Basically when I grab an nzb where the files total around 700mb everything works fine...However if I grab a nzb where the files are over 1gb I get an error:

"There was an error writing to disk - The download queue has been paused. Chances are that the filesystem is out of space. Correct the error and restart the queue"

The thing is I have a 200gb hardrive with around 160gb free and a 2.9gb swap partition that is rarely about 2% usage so I know the filesystem is fine. Any ideas on how to fix this as I really don't want to install another newsgroup reader as Klibido does the job well apart from this annoying error!!

Thanks,

Matt

---

### Post by lamego on 2006-07-25
Please open a terminal, type "df" and post the output.
Even if you have such a large drive you can have setup several smalls partitions.

---

### Post by sal on 2006-07-25
> **Pootas said:**
> Hi,

I'm running Dapper with Klibido to grab nzb files. Basically when I grab an nzb where the files total around 700mb everything works fine...However if I grab a nzb where the files are over 1gb I get an error:

"There was an error writing to disk - The download queue has been paused. Chances are that the filesystem is out of space. Correct the error and restart the queue"

The thing is I have a 200gb hardrive with around 160gb free and a 2.9gb swap partition that is rarely about 2% usage so I know the filesystem is fine. Any ideas on how to fix this as I really don't want to install another newsgroup reader as Klibido does the job well apart from this annoying error!!

Thanks,

Matt

the queue has been currupted. go into the /klibido/db folder in your ~ directory and delete the file queue and then restart klibido.

---

### Post by Pootas on 2006-07-25
> **sal said:**
> the queue has been currupted. go into the /klibido/db folder in your ~ directory and delete the file queue and then restart klibido.

Nice one....It worked a treat.

Thanks for your help ;)

---

### Post by sal on 2006-07-26
> **Pootas said:**
> Nice one....It worked a treat.

Thanks for your help ;)

no problem.

---

### Post by marx2k on 2007-11-06
Well, the problem is that it deletes a huge queue I had going :( Anyone know of anything else?

---

### Post by gjarboni on 2008-02-29
[SIZE="2"]This didn't work for me and I ended up deleting everything in klibido/db. But in retrospect I think the path in the Group properties was corrupt as my problem was limited to downloading from a single group.

If anyone else has the same problem, I'd recommend right clicking on the group with the problem and choosing group properties. Correct what's entered under "Save Directory" Hopefully this will help someone else. [/SIZE]

---

### Post by volumen1 on 2008-07-10
You just made my day!  I have this problem all the time!  My save directory in group properties had crazy control characters in it.  Thanks!

---

