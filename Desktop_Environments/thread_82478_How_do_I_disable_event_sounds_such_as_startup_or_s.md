---
title: "How do I disable event sounds such as startup or shutdown?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by blueturtl on 2005-10-26
This is really a minor issue, but since my system is so fast to shutdown, the sound that is supposed to be played always clips in the middle which is mildly unprofessional. This is why I thought I'd just remove the sound through *Preferences -> Sound->Sound events* but even after I removed the log-out sound it's still played. What do I do next?

---

### Post by jrib on 2005-10-26
System -> preferences -> sound -> sound events -> system events

change "Log in" and "Log out"

---

### Post by santo on 2005-11-03
_Jason, I think you have misunderstood the initial post.

The problem is that the sounds keep playing after having disabled/removed them through System -> preferences -> sound -> sound events -> system events.

I'm experiencing the same problem right now, with my brand new laptop (Dell inspiron 9300).

On my previous laptop (Acer TravelMate 8003LMi), I didn't have this problem.

Any suggestions welcome

---

### Post by Xian on 2005-11-03
You can use apt to remove the sounds (you'll also lose gdm):
```
$ sudo apt-get remove ubuntu-sounds
```

Or just delete the wavs in /usr/share/sounds.

---

### Post by santo on 2005-11-04
Maybe that's a temporary workaround.

But the fact is that there is a sound preferences option in the menu.
And if the option is there, it should work.
If it doesn't, then don't put it there in the first place

---

### Post by blueturtl on 2005-11-04
Well. It seems to work now. I did a fresh install after trying out Breezy Badger and I don't know why it didn't work with my previous install.

---

### Post by santo on 2005-11-10
Still not working for me. The sounds are still there, although I have disabled them in the sound preferences.

And I don't have the time to completely reinstall Ubuntu (again) as blueturtl did
("Again", because I already had to reinstall it recently because my previous laptop was stolen)

---

### Post by manicka on 2005-11-10
[QUOTE=santo]Still not working for me. The sounds are still there, although I have disabled them in the sound preferences.

And I don't have the time to completely reinstall Ubuntu (again) as blueturtl did
("Again", because I already had to reinstall it recently because my previous laptop was stolen)[/QUOTE]

what happens after a reboot?

---

### Post by Buffalo Soldier on 2005-11-10
Perhaps this is what you're looking for?

System -> Administration -> Login Screen Setup -> Accessibility:[list]
[*] Make a sound when login is ready
[*] Make a sound after a successful login attempt
[*] Make a sound after a faild login attempt[/list]

---

### Post by r0ll3r on 2005-11-15
Same here. It seems not all, but some installation result that "System / Preferences / Sound" is not disabling login and logout sound. Maybe it is because I installed Breezy 5.10 PRE release, then continuosly upgrading all packages.

---

### Post by santo on 2005-11-16
@manicka:
reboot doesn't do anything.

@Buffalo Soldier:
System -> Administration -> Login Screen Setup -> Accessibility:

    * Make a sound when login is ready
    * Make a sound after a successful login attempt
    * Make a sound after a faild login attempt

doesn't disable the login sound either (i.e. it does disable the bongo sound when the login box is displayed, but not the sound that is played after submitting username + password)

@r0ll3r: 
That's not the case, as I'm experiencing the "problem" with a clean installation of v5.10 (i.e. not colony, etc, but the final release)

Maybe it's the other way around ?
I think I didn't have this problem on my previous laptop where I installed colony 3 and then upgraded.

---

### Post by r0ll3r on 2005-11-17
One more thing:
i tried the "rename login.wav and logout.wav" workaround. After that, the login sound was still playing during login. I realized, that login.wav and logout.wav are symlinks. I only renamed these symlinks.
Summary: the problem is that somewhere inside ubuntu, "startup.wav" is set or hardcoded, that's why it is played every time i login.

Of course, renaming "startup.wav" will disable the login sound, but hey, this is a workaround.

---

### Post by Matoridi on 2006-05-04
I tried replacing the startup and shutdown sounds with short ones, and it worked.  If you then go back to sound preferences and remove any startup sound, the default Ubuntu sound comes back...

I guess you could use a short silent recording as a workaround...

---

