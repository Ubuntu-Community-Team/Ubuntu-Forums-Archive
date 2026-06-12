---
title: "where to get REAL help for sudo apt-get"
date: 2006-01-07
forum: Desktop Environments
---

### Post by bullfrog on 2006-01-07
****this has been going on for about 1 month after working for 6 to 8 weeks. sudo apt-get updates or anything will not take pass word.just sits and blinks .have never had a root password. i also have it on 2 different pcs.1is a 2gig, 1mig ram the other is a 1.66 with 512ram.both on home network. i also have it 3 hard driveson 1 pc. not hooked together.the other one is dual booted with xp [witch im trying to get out from under]  now that said ive looked every where read almost everything but seen a problem like this.so i reloaded 1 h.drive this morning with a new ubuntu disk whitch i just got the other day. same thing.if  you cant help where do i go to find out what is wrong??  thank you for your time.  bullfrog  p.s. i work at a computer shop but the tech  just dont know.  :confused:

---

### Post by imranj on 2006-01-07
[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

do have a look here? okie

---

### Post by bullfrog on 2006-01-07
forgot to say synaptic and add apps. works justfine .soory about this.bullfrog:mad:

---

### Post by leech on 2006-01-07
That's the oddest thing I've ever seen.  I would check to make sure the user you are in is in the admin group.  Go to System -> Administration -> Users and Groups.

Then click on the user, cick on the Propeties button, then select the User Privileges tab.  The third line there is "Executing system administration tasks"  Make sure there is a check mark there.  Click OK and close that out.

Then just to make sure, you can run 'more /etc/group |grep admin' and see if your user is in that line with the admin group.

And lastly, run 'sudo more /etc/sudoers' and make sure the line > %admin  ALL=(ALL) ALL is there.  Then everything should be working for that user.

Leech

---

### Post by conor on 2006-01-07
This happened to me too!    When you reloaded your system did you do an expert install?     Thats what my problem was, if I did an expert install and didn't hit 'configure multiseat system' then that happened.

---

### Post by bullfrog on 2006-01-07
****well i found out im in users group but that is all because sudo will not take password just sits there and blinks sometimes it isnt even all black just a outline.i tryed to add root password it asked for new password but thenit wont take it just blinks.one time it took password then jumps back starts blinking again wants some else but just the blinks on far left edge nothing else.got auto. update then i ran sudo passwd root again took password then says unknow user "root". the update was for sudo and4 more. WHAT can i do now???   thanks again for your time. bullfrog   ps everything else works just  sudo apt-get  did to for awhile.thanks b.f.

---

