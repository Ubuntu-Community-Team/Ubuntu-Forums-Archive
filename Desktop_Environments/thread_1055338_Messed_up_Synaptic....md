---
title: "Messed up Synaptic..."
date: 2009-01-30
forum: Desktop Environments
---

### Post by Da Mangaka on 2009-01-30
I'll try to make it as understandable as possible:

I was trying to get Joomla 1.5 installed here and I followed some instructions that later made me realize I did install it... but the 1.0 version
So... navigating around, I found the same installation process but for 1.5...
Sad thing is that I couldn't do it unless I deleted the original 1.0
So I looked at what I could do and there was somewhere I read that deleting the folder would kill it.
As I knew, it was in the /var/ folder in what Windows users know as 'C'
So, I used rm -R /var/

Ta-da! I can now install Joomla 1.5... right?
Turns out I killed that and a lot of stuff and now the synaptic won't let me neither delete, install, upgrade and more ...
Basically I think I also killed that thing.

What's most, every time I try to do a thing it comes out with this sentence:

```
Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Even if I AM logged as Root and I use Sudo (which I read is the option to act as root)
So I don't know how to fix this problem and I think I did a huge mess in here = _=()
Anyway I can fix this so I don't have to reinstall Ubuntu? (one of the options I have been seeing actually...)


PS: As you can see, I'm new in this OS . . .
Ubuntu version 8.10

---

### Post by Da Mangaka on 2009-01-31
:( no reply?

---

### Post by Arabica Bean on 2009-01-31
create the respective /var/lib/dpkg/ folders (as root) and get back to me.

I'm thinking that synaptic won't go any further as it can't find the folder that the lock is in.

Try and run synaptic, but I'm pretty certain it'll cough at you.

---

### Post by Da Mangaka on 2009-02-03
Ah, it's ok now
I re-installed Ubuntu.
Although when I tryied to create a folder (as you suggested) it wouldn't let me (since I wasn't root) but.. I can't log in via the log-on screen using root.
How do you bypass this? (in case something a-like but no the same happens)

---

### Post by taurus on 2009-02-03
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

