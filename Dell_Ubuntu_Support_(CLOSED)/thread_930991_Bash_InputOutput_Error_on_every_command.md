---
title: "Bash: Input/Output Error on every command"
date: 2008-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manish_jain on 2008-09-26
Hi
I have a very old Dell Inspiron on which Ubuntu 7.04 is installed.
The kernel version is 2.6.24-19-generic.

Sometimes, suddenly something happens and then every command from bash gives the same error:

~$ autoconf -V                                                                                                   
-bash: /usr/bin/autoconf: Input/output error
~$ ad                                                                                                            
-bash: /usr/bin/python: Input/output error

The file system becomes read-only and no files can even be 'touch'ed.

However, uname -r (and possibly other commands) still keep working. 
If you press Tab-Tab at the terminal, it hangs and then there is no way other than hard-boot to get stuff to work again.

Can anyone suggest something to repair this annoying recurrence.

---

### Post by MJN on 2008-09-27
If your file-system is becoming read-only then it is a likely sign you are having disk troubles. The read-only action is an attempt to prevent filesystem damage. Unfortunately if the bad disk/partition contains the root files then the system quickly becomes unstable as nothing can be written.

Next time it happens try running 'dmesg' as the last few lines may hold a clue as to why it is happening. Also, running 'mount' will show you which partition is now read-only.

Once you have determined that you do have a disk problem then replacement is likely the only really fix. Hopefully the dmesg output will reveal what's wrong, in which case a less drastic solution might be available.

Mathew

---

### Post by manish_jain on 2008-09-27
Hi
When this happens, even dmesg gives the same bash: Input/output error.

I ran smartctl of my only partition and I am attaching its output.

Hope you can make some meaning out of the output.

Thanks
Manish

---

### Post by niteshifter on 2008-09-28
Hi,

SMART is telling you that your disk:

Has had some control errors.
Load Cycle Count is high. Caveat: this isn't the most reliable metric of wear 'n tear. 
Most interesting is the drive temp (usually reliable): a high of 74C !!! Wow. That will shorten the drive's lifetime considerably. Possibly the source of the control errors.

You may want give the machine a cleaning / fan check. And a new HD wouldn't be a bad idea.

---

### Post by manish_jain on 2008-09-28
Thank you for your input. Do you recommend me buying a new machine itself or this could be made to work ...?

---

### Post by niteshifter on 2008-09-28
Hi,

> **manish_jain said:**
> Thank you for your input. Do you recommend me buying a new machine itself or this could be made to work ...?

Your call. A new drive will take care of the impending drive failure. If you're satisfied with the way the system works (other than this current issue) save some $$$ and stick with it. 

But that's just my 2 cents worth - from a guy who got past the "new-shiny-fast-gotta-have-it-now" bug some years ago, replaced with the it's-gotta-be-reliable bug ;)

---

