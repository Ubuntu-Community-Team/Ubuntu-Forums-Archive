---
title: "d4x startup freeze"
date: 2005-05-02
forum: Desktop Environments
---

### Post by vegetto on 2005-05-02
d4x freezes at startup. the startup music plays and thats it d4x goes to snooze. i get this in terminal:
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Killed

i tried changing the gnome theme but i got a feeling it's got something to do with that irritating startup music. what file do i edit tos disable it.

---

### Post by jodef on 2005-05-02
d4x -> Options -> Interface -> Sounds -> Disable Sounds.

From the console type : **d4x** see if any errors are spit out in the console.

---

### Post by vegetto on 2005-05-02
The only proble is it freezes before i can do what you say. i am asking if there is any conf. file which i can edit to disable the sound or is it any other problem. tried reinstalling twice, no use.

---

### Post by Bruce3000 on 2005-09-12
Hmmm... I've just started getting the problem myself... reinstall didn't work... uninstalled it then installed aria instead. Same issue with aria, however these isn't sound of course.

Hence I don't think it's a sound issue as such. Will look into it further.

Bruce

---

### Post by racknemx on 2006-01-20
...hey, i had the same prob... its sound related
the config file is in ~/.ntrc_2/config

look for *enable sounds = 1*
and make it *enable sounds = 0*

... thats all ;)

---

### Post by owennewo on 2007-02-25
Same problem for me.

Turning off sound, as you described, fixed it.  Thankyou.

Owen

---

### Post by andriyr on 2008-01-11
Thanks a lot! 

I've experienced the same problem, and thanks to your advice had fixed it.

Thank you once more :)

---

