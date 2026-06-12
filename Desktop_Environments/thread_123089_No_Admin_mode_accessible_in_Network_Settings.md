---
title: "No Admin mode accessible in Network Settings"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Olflo on 2006-01-29
Hi,
strangely, the Window 'Network Settings' shows so big on my screen that it extends downwards beyond the limits of the screen. I cannot resize it using the mouse and I cannot move using the mouse. Hiding the panel won't help, since the window goes all the way down beyond the screen.
Because of this I cannot acces the button 'Administrator mode' since it is  situated in the section of the window which is hidden from view. All other modules in the 'System settings' dialog do NOT show this behaviour, it is only 'Network settings'.

---

### Post by GeneralZod on 2006-01-29
Yet more bugginess, I'm afraid - since there are far less devs working on Kubuntu than Ubuntu, Kubuntu tends to be far rougher around the edges, alas - I'm going to see if KDE is better served in Dapper and if not, might jump over to SUSE for a while.

Anyway, run 

```

kcontrol

```

as a workaround.  In case the admin mode doesn't work in that (yes, another Kubuntu-specific bug :(), use

```

kdesu kcontrol

```

---

### Post by Olflo on 2006-01-29
General,
you seem to be just waiting for my posts to be the first to answer...:p  thank you.

It looks like kdesu can often to a better job than sudo...whats the difference, actually?

btw: running kcontrol is perfectly ok, admin mode is available. :-D 

you say there are fewer devs working on kubuntu than on ubuntu. well, how can I report this bug to help someone improve kubuntu? The report bug feature in the system settings is buggy in itself and wont do the job. 
i still like kubntu enough to not go back to suse and maybe i can help by reporting a few bugs.

---

### Post by GeneralZod on 2006-01-29
[QUOTE=Olflo]General,
you seem to be just waiting for my posts to be the first to answer...:p  thank you.
[/QUOTE]

It's a slow day ;)

```

It looks like kdesu can often to a better job than sudo...whats the difference, actually?

```

I'm not really sure, other than the fact that kdesu is obviously a GUI app and that KDE apps appear to be more likely to work with their own native sudo-ing mechanism.

```

btw: running kcontrol is perfectly ok, admin mode is available. :-D 

```

That's good - the bug was present in Kubuntu 5.04 *and* in the initial release of 5.10, but a later update to 5.10 fixed it :)

```

you say there are fewer devs working on kubuntu than on ubuntu. well, how can I report this bug to help someone improve kubuntu? The report bug feature in the system settings is buggy in itself and wont do the job. 
i still like kubntu enough to not go back to suse and maybe i can help by reporting a few bugs
```

I think "malone" is used nowadays, but I know there's definitely no point in filing a report about this particular bug - *lots* of people have been complaining about it already :)

---

### Post by ergo_pro on 2006-01-29
You can move the window by grabbing window and moving it while holding ALT down. 

(sry about bad english)

---

