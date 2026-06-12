---
title: "Gpilotd sync problems w/ Treo 755p"
date: 2008-02-14
forum: Desktop Environments
---

### Post by agibby5 on 2008-02-14
I've successfully synced many times.  However, when I wanted to Copy to the PDA (contacts and calender items) since I messed up many of the  records on the PDA, gpilotd will not sync the contacts or the calender items.  All it says is ignoring for those items.  The only two things that will sync are the memos and the to-do list even though those things are set to Disabled.  I really need this to work, my calendar and contacts are ruined on my phone.  Does anyone have any ideas as to what I can do to remedy this situation?

---

### Post by agibby5 on 2008-02-18
Any ideas are greatly appreciated.  Thanks.

---

### Post by agibby5 on 2008-02-25
If I could be pointed in the right direction for this, that'd be great.  This is very important to me since I've switched to Ubuntu fully.  I need to get my contacts from the computer back onto the Treo.  Is there an IRC room or forum specific to evolution or gpilot problems?

---

### Post by agibby5 on 2008-03-06
My settings are:
[IMG]http://image.bayimg.com/bajdoaabc.jpg[/IMG]

Here's my gpilotd output... (I've removed the successful sync of the Memos and Tasks since they contained personal info)
```
gpilotd-Message: Instantiating 5 conduits...
eaddrconduit-Message: in address's conduit_get_gpilot_conduit

ecalconduit-Message: in calendar's conduit_get_gpilot_conduit

etodoconduit-Message: in todo's conduit_get_gpilot_conduit

ememoconduit-Message: in memo's conduit_get_gpilot_conduit

gpilotd-Message: Instantiated 0 backup conduits, 1 file conduits, 4 other conduits
gpilotd-Message: HotSync button pressed, synchronizing PDA
gpilotd-Message: PDA ID is 10455, name is Treo 755p, owner is XXXXX
gpilotd-Message: Pilot has 0 entries in restore queue
gpilotd-Message: Pilot has 0 entries in conduit queue
gpilotd-Message: Pilot has 0 entries in file install queue
gpilotd-Message: Base ContactsDB-PAdd is to be ignored by sync
gpilotd-Message: Base CalendarDB-PDat is to be ignored by sync
gpilotd-Message: Base AddressDB is to be ignored by sync
gpilotd-Message: Base DatebookDB is to be ignored by sync
gpilotd-Message: Base ContactsANIndex-PAdd is to be ignored by sync
gpilotd-Message: Base ContactsBDIndex-PAdd is to be ignored by sync
gpilotd-Message: Base AddressCitiesDB is to be ignored by sync
gpilotd-Message: Base AddressCompaniesDB is to be ignored by sync
gpilotd-Message: Base AddressCountriesDB is to be ignored by sync
gpilotd-Message: Base CalendarLocationsDB-PDat is to be ignored by sync
gpilotd-Message: Base AddressStatesDB is to be ignored by sync
gpilotd-Message: Base BGCache-PDat is to be ignored by sync
gpilotd-Message: Base AddressTitlesDB is to be ignored by sync
gpilotd-Message: Base Txn Log 50416464 is to be ignored by sync
gpilotd-Message: Base Txn Log 50446174 is to be ignored by sync
gpilotd-Message: Synchronization ended
gpilotd-Message: setting PILOTRATE=115200

(gpilotd:29548): gpilotd-WARNING **: An error occurred while getting the PDA's system data

(gpilotd:29548): gpilotd-WARNING **: error -201 from pi_close.


```

Any help is GREATLY appreciated... I also deleted the files whose filenames contained 'pilot-sync' in .evolution folder in my home directory... I hoped that this would 'reset' the sync process.  The Memos and Tasks still synced but the rest did not...

---

### Post by agibby5 on 2008-03-20
FINALLY!  I solved this.  

I backed up all my /home data.  I then proceeded to delete all the .gnome*, .gpilotd, .evolution, etc folders.  I imported ONLY the address book information back into Evolution, reconfigured gpilotd and tried to sync.  Still the same issue.  I then restored my /home directory.

At this point, I figured the problem must be my 755p.  I did a full factory restore on it and tried to sync all my data... VOILA!  Problem fixed.  Some of the databases must have been corrupted on the phone which prevented the sync from going through successfully.  I hope this post helps those of you who may be having similar issues.

---

### Post by Apnu on 2008-03-25
agibby5 -- Thank You! Thank You! Thank You!

I had a similar problem and couldn't figure out what to do.  I followed your advice and it didn't work, but I felt I was on the right track.  So I tried again... full factory reset with my Treo. However instead of backing up and restoring my /home I instead, deleted every reference to "pilot' in my home dir.  

To find them, at the command line do "sudo updatedb" When that is complete, do "locate pilot | more" to see a list. Hunt down and rm all the files that say "pilot", there will be several in .gnome* directories and .evolution/

This basically made gpilotd think it had never been run before.  When I ran it, I went through the usual setup then set my conduits up the way I wanted (specifically "copy to PDA" for EAddress and ECalendar) and sync'd.  And it worked!  Yippie!

:) :) :) :)

---

### Post by agibby5 on 2008-03-30
I have made a few edits to some events in my calendar in Evolution and tried to sync again and I'm having the problem listed in my first post again.  I'd hate to have to reset my Palm before every sync... of course I'm not going to do that.  I just changed the same events in JPilot, and it synced perfectly.... no need for a reset of the Palm.  Sounds like a bug in gpilotd.... I'd really love it if I could use Evolution since I also use if for work emails (MS Exchange server connection)...  but I'll work with JPilot since it works everytime.

---

### Post by agibby5 on 2008-07-03
To get rid of all the evolution data and gpilotd data in the home directory.... do the following: 

cd to your home directory and run: 

```

find . -name "*gpilotd*"
find . -name "*evolution*"

```

Once you see what you've expected, you can then do this: 
```

find . -name "*gpilotd*" -exec rm {} \;
find . -name "*evolution*" -exec rm {} \;

```

This will essentially remove all your evolution data.  Ever since I switched to Jpilot, which works with my Palm sync every time, I became more and more annoyed by the evolution alerts that I've been receiving and that are now outdated since I haven't been able to successfully sync my palm.

---

