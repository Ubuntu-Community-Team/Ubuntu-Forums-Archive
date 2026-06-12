---
title: "auto logout problem"
date: 2008-05-19
forum: Desktop Environments
---

### Post by anystupidname on 2008-05-19
I couldn't find the "stupid user tricks" section so I'm posting this here. You have to promise not to laugh though...

I added TMOUT=3 to /etc/profile and/or /etc/environment
and then did an export TMOUT

(I'm guessing that is seconds instead of minutes or something like that...)

Somebody else rebooted the box and now we log in and get logged out immediately.
I'm not at the physical location of the box and the person there knows even less about *nix than I do...

Any suggestiongs other than booting from a knoppix cd fixing the problem that way?

---

### Post by gnivler on 2008-05-19
> **anystupidname said:**
> I couldn't find the "stupid user tricks" section so I'm posting this here. You have to promise not to laugh though...

I added TMOUT=3 to /etc/profile and/or /etc/environment
and then did an export TMOUT

(I'm guessing that is seconds instead of minutes or something like that...)

Somebody else rebooted the box and now we log in and get logged out immediately.
I'm not at the physical location of the box and the person there knows even less about *nix than I do...

Any suggestiongs other than booting from a knoppix cd fixing the problem that way?

Assuming you have GRUB installed, before the kernel boots you have the option of choosing the line ending with (recovery mode).  That should give you a command prompt, possibly one that will immediately get logged out, I'm not sure and it's about all I can think of aside from the live cd idea you have.

---

### Post by sdennie on 2008-05-20
If you only have ssh access to the box, you could try using something like:

```

ssh the_box sh -i

```

That will create an interactive sh shell under the bash shell to fix the problem.  I don't know if bash shell will timeout if it has child processes so, you may be able to fix the problem using that method.

Edit:

Actually, it looks like it may not invoke bash at all using that method.  I just tried to ssh in locally and I didn't notice any new instances of bash being created.  In which case, it will probably fix your problem.

---

### Post by anystupidname on 2008-05-20
Thank you both for your replies! I seriously appreciate it. Sorry, I'm impatient and ended up taking the hour drive out there and using a knoppix CD to change the TMOUT setting. I particularly like vor's idea though. I might just setup a test box to test that for next time.

---

### Post by eltchka on 2008-08-09
Hi!

I have just switched to Ubuntu 8.04 from fedora 9. i have a brand new laptop which came pre-installed with Ubuntu. Everything works fine, but when I leave it idle for sometime, it comes up with the login screen. So it seems it's automatically logging out after a certain period. When I log in again, none of the programs that were running previously aren't running anymore.

Could this be a set automatic log-out thing? If yes, how can I stop it from doing that?

---

