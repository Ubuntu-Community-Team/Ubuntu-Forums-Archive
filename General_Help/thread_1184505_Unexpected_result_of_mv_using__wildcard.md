---
title: "Unexpected result of mv using * wildcard"
date: 2009-06-11
forum: General Help
---

### Post by george.henne on 2009-06-11
In a bash shell, I issued a mv command with a puzzling result. I'm hoping someone could explain it to me.  I am assuming, at this time, that there is something about how the * wild card expanded that I don't understand.

After a massive file transfer of a directory named "RAID_BACKUP" into my new RAID, I needed to tidy the directory structure.

** The command I issued:

# mv /mnt/RAID5/RAID_BACKUP/* /mnt/RAID5/

** What I wanted it to do:

Move the directories in RAID_BACKUP up one level into RAID5, emptying RAID_BACKUP so I could remove it.

** What actually happened:

Only the alphabetically-last directory was moved into RAID5, and all of the other directories were moved into that alphabetically-last directory.

Before the move, I had:
/mnt/RAID5/RAID_BACKUP
/mnt/RAID5/RAID_BACKUP/george
/mnt/RAID5/RAID_BACKUP/judy
/mnt/RAID5/RAID_BACKUP/shared
/mnt/RAID5/RAID_BACKUP/unassigned (empty)

After the move, I had:
/mnt/RAID5/RAID_BACKUP (empty)
/mnt/RAID5/unassigned
/mnt/RAID5/unassigned/george
/mnt/RAID5/unassigned/judy
/mnt/RAID5/unassigned/shared

** Date I revoked my use-of-asterisk privileges:

Thu Jun 11 06:30:00 EDT 2009



Could someone please explain how this happened?

Thanks for any help in improving my understanding of bash wildcards. :D

---

### Post by benj1 on 2009-06-11
ive just tried to recreate it and haven't had that problem, have you been able to recreate it?

---

### Post by george.henne on 2009-06-11
> **benj1 said:**
> ive just tried to recreate it and haven't had that problem, have you been able to recreate it?

Ok, I've got more info this time.  I couldn't recreate it at first....

Then I looked back in the history and retried part that I didn't think had an effect.

Before the mv command, there was a 'failed' attempt with

```
 # mv RAID_BACKUP/* 
```

I didn't realise that it was this command that stuck everything from the RAID_BACKUP directory into the alphabetically last directory within RAID_BACKUP.

I think I get it now.  I think the command expands to

```
 # mv RAID_BACKUP/a RAID_BACKUP/b RAID_BACKUP/c 
```

which then shoves everything into c.

This is what I get for leaving out the destination in the mv.

I was thinking, at the time, that it might have defaulted to the current working directory.  I did a 'ls' to see if the stuff was where I wanted it to be, but I hadn't peered into RAID_BACKUP at that time.

Sorry for the confusion.  Problem solved.
:D

---

### Post by synapsys on 2009-06-11
You should also be able to use 

```
mv -R /RAID_BACKUP/* /destination/
```

The -R includes all subdirectories of RAID_BACKUP

---

