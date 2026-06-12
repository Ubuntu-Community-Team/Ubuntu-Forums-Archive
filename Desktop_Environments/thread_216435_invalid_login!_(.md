---
title: "invalid login! :("
date: 2006-07-15
forum: Desktop Environments
---

### Post by rockprincess on 2006-07-15
hello all,

i'm quite upset right now, i've purchased a new 160gb HDD today, and installed Dapper Drake on it. On my old 80gb HDD Dapper Drake is running smoothly for the past three weeks and now since I ran out of space I decided move onto a bigger HDD. So far so good, installation on the new HDD ran smoothly. 

And then I loaded both HDD's together, booting with the newly installed 160gb system. I couldn't mount the old one (for some unknown reason) I decided to shut down and just start the old one and burn the files that I desperately needed onto a dvd.
and now this is where my problem is, my login wasn't accepted anymore (no error message) it just wasn't accepted.
is it because i chose the same login name and password for both systems and booted them together?!

is my data on the old system forever lost?!!!

I'm really desperate right now, as I don't know what to do!

Hope my english isn't too bad!

thank you in advance,
Theresa

[B]EDIT: Ok, it doesn't say "Login failed." it only does when I type in a false password, but it actually goes all black for a second and then switches back to the KDE login interface. That's what frustrates me, because I actually type in the right password but can't get any access.
[/B]
Any ideas?!

---

### Post by ltmon on 2006-07-15
Don't worry, your data isn't lost: at very least you can use a livecd to recover the data.  But that's an extreme measure for now.

This is the kind of behaviour that tends to happen when there has been an error of some kind.

I suggest the following to find out the error:

1. ctrl-alt-f1 to get to a text terminal from the login screen.
2. Login
3. "sudo /etc/init.d/kdm stop"  This stops the currently running session you just moved from.
4. "startx"

The final step will most likely fail, but you will be able to use ctrl-alt-f1 to go back and see the errors.  Post back what you see here.

L

---

### Post by rockprincess on 2006-07-16
thank you, ltmon!

this was a brilliant answer, I managed to stop the kdm login manager.

these are my error messages:

```
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
                 No such file or directory. 
Error opening /dev/wacom: No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
                 No such file or directory. 

```
this gets repeated a few times until this comes in.

```
waiting for x server to shut down FreeFontPath: FPE "/user/share/X11/fonts/misc"
refcount is 2, should be 1; fixing.
```

I have no idea what this means.

I appreciate any help!

cheers,
theresa

---

### Post by ltmon on 2006-07-16
Unfortunately I don't think that either of the above is your problem.

The first is there because Ubuntu seems to automatically configure a Wacom tablet for every install, even if one doesn't exist.  But as the error message says "Errors from xkbcomp are not fatal to the X server".

The second one is just some of the foobar that X prints out all the time.  I get the same message with no ill effects.

Can you try looking at the file "/var/log/kdm.log".  It's the log file for the login/desktop manager for KDE.  It might have a clue.

Do you also have Gnome installed?  If you do you could try setting your session to a Gnome session (use the "Menu" button at the login screen).  If this worked we could narrow down your problem to a KDE only problem.

Cheers,

L.

---

