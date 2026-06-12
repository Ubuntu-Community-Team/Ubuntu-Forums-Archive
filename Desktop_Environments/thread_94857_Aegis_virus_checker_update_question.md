---
title: "Aegis virus checker update question"
date: 2005-11-25
forum: Desktop Environments
---

### Post by blastradius on 2005-11-25
Hi all.

I'm probably in the wrong forum here, and if so i apologise.  Anyway, i've installed the above virus checker, when i start it up it tells me that a 'new version of file::scan is available' and do i want to update.  When i click yes  it prompts for the root password and seems to do it's thing, it then tells me to restart Aegis.  
The thing is, it asks me to do this every time i restart!  
Maybe i'm paranoid or am i going insane (get the Black Sabbath in!) but is this anything to worry about?

Thanks in advance

Eric

---

### Post by topic58 on 2005-11-25
I have had that problem too with Aegis. Solved it by downloading F-prot instead. It's free and works nicely in terminal.

---

### Post by korami on 2005-12-12
[QUOTE=blastradius]Hi all.

I'm probably in the wrong forum here, and if so i apologise.  Anyway, i've installed the above virus checker, when i start it up it tells me that a 'new version of file::scan is available' and do i want to update.  When i click yes  it prompts for the root password and seems to do it's thing, it then tells me to restart Aegis.  
The thing is, it asks me to do this every time i restart!  
Maybe i'm paranoid or am i going insane (get the Black Sabbath in!) but is this anything to worry about?

Thanks in advance

Eric[/QUOTE]

If anyone still interested...

I had the same issue, then I run Aegis as root (with gksudo) and it worked, that is i had to configure some CPAN module at the beginning, but after that the file::scan was updated, and after restart I wasn't prompted anymore for a new update.

So it seems to work when running as root.

---

### Post by bluevoodoo1 on 2005-12-13
[QUOTE=korami]If anyone still interested...

I had the same issue, then I run Aegis as root (with gksudo) and it worked, that is i had to configure some CPAN module at the beginning, but after that the file::scan was updated, and after restart I wasn't prompted anymore for a new update.

So it seems to work when running as root.[/QUOTE]

Thanks! Worked perfectly for me! I was wondering how to remedy that.

---

### Post by riktzvet on 2006-01-15
I got it to work that way as well. "Sudo aegis-virus-scanner", enter the root password and the update takes place. At the point that it asked if I wanted to configure CPAN manually I chose ~no~ then it completed the update and no longer asks to be updated. I assume tho that there will be updates to it in the future, i.e. dat files or the equivilent?

---

### Post by Cornelius Johannes on 2006-02-04
thanks, this worked for me too.

---

### Post by matchstich on 2007-07-24
i tried this and think i screwed it up, keep getting error messages.

how do i unido and start over.
 thanks

---

### Post by matchstich on 2007-07-24
[QUOTE=matchstich;3072470]i tried this and think i screwed it up, keep getting error messages.

how do i undo and start over.?
 thanks[!/QUOTE]

---

