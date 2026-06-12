---
title: "Working Incremental backup utility?"
date: 2008-12-21
forum: General Help
---

### Post by JumpingJack on 2008-12-21
Hello all! :)

I'm just searching an incremental backup utility that really works. Let me explain my scenario:

 I work as a Freelance developer, so i use ubuntu on my laptop. On my homebase (my house) i have a Western Digital MyBook NAS unit. What i need is a piece of software able to automatically dump incremental backups (every hour) to the NAS unit when i'm working at home. So if i accidentally delete something of my job...i'll have a 1 hour old backup.

Things tested so far:

- Timevault (0.7.5): Still alpha, and still very buggy, problems found after intensive tests:

  Timevault hates SMB shared folders as snapshot root: Database locks all  the time, process hanging up from time to time...and so on,impossible to create a baseline snapshot on the remote unit. 
After diving on the forums, i managed to avoid the database locks problem just adding the "nobrl" flag to my CIFS mount command but it is still unable to create de Baseline snapshots...no way, i give up.

SO my conclusion is: Timevault doesn't works well when the snapshot root is a network share.


- FlyBack: Well, it creates backups, but i think something is going weird with the "incremental" thing....it looks like copying all the data on each snapshot! ... Maybe the HARDLINKING technique doesnt works on network drives?!?


- rsnapshot: Tried it for a little amount of time, i don't fully understand the way it works.

   
  


 Any suggestions?


Thanks in advance for your help

---

### Post by bodhi.zazen on 2008-12-21
Have you looked at rsync ?

---

### Post by JumpingJack on 2008-12-21
Well, mostly all the solutions i've tested are using RSYNC. In fact, Flyback is more or less a "complex" rsync front-end.

I think the problem is the SMB shared folder being the destination folder of the backups, not allowing hardlinking and file stats changes. I think i'll give a try to NFS.

---

