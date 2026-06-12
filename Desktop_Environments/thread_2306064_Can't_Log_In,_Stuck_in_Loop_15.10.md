---
title: "Can't Log In, Stuck in Loop 15.10"
date: 2015-12-11
forum: Desktop Environments
---

### Post by matthewland123 on 2015-12-11
i can't seem to log in, and i have tried editing the .Xauthority already, and the guest account doesn't work either so it's not user based. Any ideas?

---

### Post by yoshii on 2015-12-12
This could be dangerous and is maybe a last resort.  I haven't tried it myself, but you might be able to do something like:  

1) obtain a LiveCD and boot up with it
2) reinstall Ubuntu without reformatting using a different username keeping mainly the home folder
3) clean up the old stuff using the new user

This guy did something like this here:  [http://ubuntuforums.org/showthread.php?t=2306062&p=13405525#post13405525](http://ubuntuforums.org/showthread.php?t=2306062&p=13405525#post13405525)
He was able to recover his stuff.  

There's one line where he says "deluser", but I think he means user "deity" using the command "deluser" maybe.  
I think what he described might work.  

Good luck.

---

### Post by Bashing-om on 2015-12-12
matthewland123; Hello ;

Next in line IF this proves NOT to be an authorization issue to access "your" /home;
is to check for what the graphic's driver situation is:

can you boot from grub's boot menu in the 'recovery mode' ? That loads the fall back graphics driver, one way to 'see' if this is graphic's related.

also another thing is to boot to terminal and take a direct look at what is .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

