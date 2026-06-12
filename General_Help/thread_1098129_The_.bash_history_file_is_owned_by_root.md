---
title: "The .bash_history file is owned by root"
date: 2009-03-16
forum: General Help
---

### Post by gauthma on 2009-03-16
After a clean install of Ubuntu Intrepid Ibex (8.10, alternate cd, amd64), bash history was never saved. After a long while fiddling with it, I eventually found that this is was due to the fact that .bash_history was owned by root! With permissions of 600, when logged in as the normal user, I could not write to the file. 

Searching the forums I found [this thread]("http://ubuntuforums.org/showthread.php?t=737058") about the same issue, and tried to reply to it, but it was closed, so I decided to ask this here: did anyone else had the same trouble? Is it a known bug?

Cheers

---

### Post by taurus on 2009-03-16
Just change the ownership of ~/.bash_history from root back to your login name.  _Assuming_ your login name is john, you would run

```
sudo chown  john:john /home/john/.bash_history
ls -la
```

---

### Post by gauthma on 2009-03-16
Thanks for the quick feedback, but I have done that already (forgot to say that in previous post, sorry). My question was rather if this is a known bug or not. As stated in the link of my first post, the same situation happened with earlier versions of ubuntu, hence my question.

But I still appreciated the quick feedback ;)

---

### Post by Slim Odds on 2009-03-16
> **gauthma said:**
> My question was rather if this is a known bug or not. As stated in the link of my first post, the same situation happened with earlier versions of ubuntu, hence my question.

My guess is a cockpit problem.

I've never seen that on any of my Ubuntu machines and I've never heard of lots of people having that problem.

Is is possible that you did something strange?

---

### Post by gauthma on 2009-03-16
> **Slim Odds said:**
> Is is possible that you did something strange?

While that's certainly not impossible, I do doubt it. In particular, I am certain that it wasn't me that made such a change! :wink: Do you have any idea of what changes could cause for something like this to happen, literally, automagically?

---

### Post by trwww on 2009-03-16
> **gauthma said:**
> Do you have any idea of what changes could cause for something like this to happen, literally, automagically?

Running the user's first command ever as sudo may do something like that. Stuff like that.

---

### Post by philinux on 2009-03-16
Definitely PEBKAC.

Permissions don't change by automagic.

---

### Post by Slim Odds on 2009-03-16
> **philinux said:**
> Definitely PEBKAC.

Permissions don't change by automagic.

Yes, my thoughts exactly....

BTW, a "cockpit problem" == PEBKAC

---

### Post by gauthma on 2009-03-17
> **trwww said:**
> Running the user's first command ever as sudo may do something like that. Stuff like that.

Erm, yes that might be it :oops:

I did not see that one coming... but well, I guess that solves it then! Thanks for all the replies!

/me gets back to the cockpit :-)

---

