---
title: "desktop corrupted"
date: 2007-12-02
forum: Desktop Environments
---

### Post by hollowhead on 2007-12-02
I have a strange problem I have not seen the like of before.  Just clean installed gutsy on desktop machine and wiped windows.  Setup users for all the family.  Everything was fine until this evening when now if you download say an mp3 (but anything really) via firefox to the desktop then you cannot do anything with that file.  All the menues work except relating to nautilus.  If you try home computer etc from places then nothing happens. Log out doesn't work and I have to do ctrl-alt-backspace.  I suppose the problem is nautilus.  How should I sort it, the system really isn't properly usable.

---

### Post by ItsManaged on 2007-12-03
Does this happen with any user or just one user?

If it only happens with one user, the easiest way around it is to create a new user (System -> Administration - > Users and Groups), then log in as the new user. You may want to delete the old user, but not really necessary.

---

### Post by hollowhead on 2007-12-03
Thanks for your response.  Any user, it was definitely nautilus.  The problem started (I think?, I hope?) when my wife put her ipod shuffle in the machine rhythmbox started multiple times and crashed each time (we were messing about with the shuffle we though there was a loose connection).  I tried uninstalling rhythmbox , reinstalling nautilus,  uninstalling nautilus to no effect.  I had a really bad hang then when I logged back in the background was blank.  I also had a an error message which I have not got in front of me about a problem with bonobo.  Checking logs revealed nothing except in root there was a naultulus log that just said seg11 fault (which is memory allocation if I am correct).  Running nautilus from a terminal produced no errors.  The system was in effect unusable so this morning I reinstalled gutsy.   Incidentally I have a lap top with exactly the same gutsy (though upgraded from feisty) system on and putting in the ipod crashed rhythmbox but did not cause any subsequent problems in nautilus -although I only allowed one crash!  This is all right as long as the problem does not re-occur- having persuaded my wife to dump windows. Nautilus (and linux) has been very reliable on my laptop and I like it as a file manager.  Could it be a hardware problem I know to check memory but is there a diskchecking utility out there?  As anyone else this problem with nautilus or shuffles?  Puzzled and a bit worried.  Hollowhead.

---

### Post by osdesk on 2007-12-06
I'm having a similar problem.  I did a fresh install of Gutsy on a new drive for a client and everything was working fine for a few days.  

I started editing the ppp for him to have dialup (with no success) and all of a sudden an error message came up stating that bonobo might have crashed nautilus and it recommended to reboot nautilus.  Before I was able to do that, the client rebooted the entire system, and now I can only get a dark screen, no menus, no options, etc. and cold shut down is necessary as ctrol+alt+bksp doesn't work each time.

I have found no solution thus far.  :(

---

