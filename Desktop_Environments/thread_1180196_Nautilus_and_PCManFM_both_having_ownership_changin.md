---
title: "Nautilus and PCManFM both having ownership changing issues."
date: 2009-06-06
forum: Desktop Environments
---

### Post by learningcurb on 2009-06-06
So I made an extra user account for testing things out.  Then I decided that having an extra user account around was just getting in the way and decided to combine all my accounts.

Nautilus with gksudo changed the ownership a portion of the files, but did not change them all and returned no errors to the terminal.  PCManFM in administrative mode changes permissions on some of the subdirectories and gives me a dialogue box that says "No such file or directory".  It doesn't return any messages to the terminal either.

Finally I was able to change the ownership from the commandline using sudo chown -R, but I am curious why the graphical file managers aren't able to do the job.  Does anyone know what is wrong?  I'm not even sure which program to file a bug report under since it seems to be a more general problem than just one file manager.

---

