---
title: "[SOLVED] how can i shutdown -r now.. without sudo?"
date: 2009-01-12
forum: General Help
---

### Post by cb34 on 2009-01-12
hi, on my own personal home system with no other users, how can i make certain commands not need root access.

for starters, to understand/learn how to do this, i want to set it up so i can run:
shutdown -r now
without sudo, from the user shell. i figure there must be a way.

as i dig deeper into linux, being a fairly new user(under a year) there is nothing that i get to, that i think, "can this be done?", it's alwayz, "HOW can this be done?" :D so...

can someone please help me out how to do this kind of thing.

i have no clue, just thinking.. can it be done like putting certain commands into a certain group that i have access to.. or some special code in sudo visudo?

Thank you very very much for any help. :D i just never stop tweaking my box. :guitar:

---

### Post by Sprut1 on 2009-01-12
Sorry for my ignorance, but why do you want to do that?

---

### Post by cb34 on 2009-01-12
so everything is the way i like it.. no reason.

and it's not that particular command, its the concept to know how to do this, even when i dont need something, i want to still know how to do it. im on a never ending hunt for linux knowledge.

and why in gnome, can u just hit reboot, or shutdown and you dont need to enter a pass, thats where the question in my head came from to be honest. :)

i wonder if it's some shutdown script that needs to be modified to not check who's running the script??

---

### Post by jediborger on 2009-01-12
Here's a link to a documentation page on how to edit the sudoers file. Specifically at the bottom is an example of allowing the shutdown commands to run without a password.

[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

---

### Post by cb34 on 2009-01-12
thank you very much jediborger!! i'm going to read it right now. :D

you rule.

---

### Post by Ahadiel on 2009-01-12
> **cb34 said:**
> and why in gnome, can u just hit reboot, or shutdown and you dont need to enter a pass, thats where the question in my head came from to be honest. :)

It doesn't ask for a password because Gnome (run as your user) communicates with GDM (run as root).

---

### Post by Sprut1 on 2009-01-12
> **cb34 said:**
> so everything is the way i like it.. no reason.

and it's not that particular command, its the concept to know how to do this, even when i dont need something, i want to still know how to do it. im on a never ending hunt for linux knowledge.

and why in gnome, can u just hit reboot, or shutdown and you dont need to enter a pass, thats where the question in my head came from to be honest. :)

i wonder if it's some shutdown script that needs to be modified to not check who's running the script??

Okay, I see now - was just curious :)

---

### Post by cb34 on 2009-01-12
i can totally understand why you asked that, eeez cool. :D be well.

---

### Post by cb34 on 2009-01-12
> **Ahadiel said:**
> It doesn't ask for a password because Gnome (run as your user) communicates with GDM (run as root).aha! gotcha.. was thinking it was something like that, just didn't get what was goin on.

Thanks for the info. :)

---

### Post by quazi on 2009-01-12
> **cb34 said:**
> thank you very much jediborger!! i'm going to read it right now. :D

you rule.

It's mentioned in the link posted, but make sure you pay attention to order in the sudoers file.  Took my awhile to figure out why my sudoers changes weren't doing anything.

---

### Post by cb34 on 2009-01-12
> **quazi said:**
> It's mentioned in the link posted, but make sure you pay attention to order in the sudoers file.  Took my awhile to figure out why my sudoers changes weren't doing anything.i will, thank you for this. :D

---

### Post by iaculallad on 2009-01-12
You could just add the SUID mode to your shutdown terminal command:

```
sudo chmod u+s /sbin/shutdown
```

You can now invoke the shutdown command without elevating your privilege through sudo.

Simply:

```
shutdown -h now
```

or

```
shutdown -r now
```

---

### Post by cb34 on 2009-01-12
why didn't i think a that.. hehe.. no seriously.. THANKS ALOT!!

so far up until now, i could never understand things to do with suid, and im usually pretty competent with understanding new things.. but i'll get to reading on it i guess, and all the chmod flags.. need to get my head around all that.

thanks, i'd rather do this than modify the visudo file, which is still pretty simple, just this is simpler.

you also rule iaculallad!! :D:D

good one.

---

### Post by cb34 on 2009-01-12
ran chmod on the shutdown binary, then rebooted without sudo and it works.. and i'm back. :)

thanks again.

i love this forum and all you very helpful, insightful people out there!
you all rock! :guitar:

---

### Post by iaculallad on 2009-01-12
I'm glad that the idea of using SUID mode helped ):P
Go Ubuntu.

---

