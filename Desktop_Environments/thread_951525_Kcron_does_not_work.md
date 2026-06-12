---
title: "Kcron does not work?"
date: 2008-10-18
forum: Desktop Environments
---

### Post by Quarkrad on 2008-10-18
I have spent days trying to get simple local folder sync/mirroring to work - I'm a new windows convert to Linux and there are dozens of simple apps to do for winXP.  At the moment it like trying to climb a mountain.  So far I successfully sync'd/mirrored two folders using Grsync.  I have played about with different options and thy all work by me pressing the Execute icon.  But this is not going to work for my wife every time she uses the pc.  So, I move onto kcron that appears to automate this.  In the Program: box within Krcon I have entered the line  /usr/bin/grsync -e default   for various times of the day but nothing happens - it is as if Kron will not work.   As said, if I launch Grsync an execute manually (i.e. my profile   default) I force folder sync/mirroring.  Any advice appreciated - perhaps I'm not using the right tools here.  All I want is a background task (winxop did it on shutdown) where user folders were copied (for backup). Must confess this simple(??) task seems a bit of a job for Linux.

---

### Post by mtbsoft on 2008-10-18
Take a look at Unison, it might be what you need.  It can sync. multiple folders/files across multiple machines and/or file systems and can work in both Linux and Windows.  I use it (among other things) to keep the urlfilter files, etc. for Opera in sync. across four machines - some dual boot some windows, some Linux.

Try [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/) for a start point.

Sorry, I forgot to say that this works fine with a variety of cron utilities and also as a startup option from the session startup.  You could create a script to run this and then shutdown and use that as the shutdown method too.

---

### Post by Quarkrad on 2008-10-19
Kron is still not working but something, somewhere, has added to the text string.  In order to kick grsync I had this text inserted:

/usr/bin/grsync -e default


Now it reads:

/usr/bin/grsync -e default >/dev/null 2>&1 # JOB_ID_4

I have no idea what this means and/or how it got there - will kcron work but its in some sort of queue?  Appreciate any help.

---

### Post by Quarkrad on 2008-10-19
Hmmm....... just launched the Terminal and typed in:

/usr/bin/grsync -e default

pressed return and it works - folders sync'd/mirrored --- so looks like kcron is not working for some reason.  Is it possible to automate this activity some other way?  I ideally I would like this activity to be kicked off when I instruct the pc to shut down.  At the moment it looks like my first winxp task will have to be done manually in Linux/Ubuntu - pity.

---

