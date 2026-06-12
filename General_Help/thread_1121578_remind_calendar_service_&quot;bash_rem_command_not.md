---
title: "remind calendar service &quot;bash: rem: command not found&quot;"
date: 2009-04-10
forum: General Help
---

### Post by limerentjellyfish on 2009-04-10
Hi.  I installed the remind command line calendar program on eexubuntu 7.10 using getdeb.  My understanding it should be able to type

REM 6 Jan MSG David’s birthday
to set up a reminder message of "David's birthday" for january 6 

Apparently I can't execute the rem command through the built in bash terminal, I get "bash:rem:command not found".  The executable file is installed in usr/bin/ 

when I replace "REM" with "remind" the program itself seems to run (I get syntax info, etc) but takes no action.  When I type "remind" by itself I get "no reminders".  I'm new to linux, do I need to edit PATH or bashrc?

I'm pounding my noggin against the woodgrain here, thanks in advance for your help :)

---

### Post by Urara on 2009-04-21
I was just monkeying around with remind earlier today. There's a good tutorial on the 43folders.com website.

Anyway, it took me a while to figure out that I needed to create a text file called ".reminders" in my home folder and that's where I entered the "REM Apr 30 2009 _10 MSG blah,blah,blah %b.%". Then to display the reminders I had to enter "remind .reminders".

Hope this helps!

---

