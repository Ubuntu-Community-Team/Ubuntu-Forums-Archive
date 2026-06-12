---
title: "The death of a filesystem"
date: 2009-03-16
forum: General Help
---

### Post by bla687 on 2009-03-16
So, this is an interesting problem I've run into.

I've got an eeepc netbook that I put ubuntu 8.10 onto. It's using a customized kernel designed for the eeepc, but I don't think that that is the issue here (though I've been known to be wrong before). 

Anyway, a while back, I wasn't able to install any programs, because apt-get had a package half installed, and it couldn't complete the installation or remove the package due to a "stale NFS file handle". Now, I know I am not running anything to do with NFS on my laptop, so I decided to run a filesystem check on my next boot (when I had finally decided that this was an insane problem that shouldn't be happening at all) and fsck managed to find and fix one or two problems. I thought was the end of it.

That was about two weeks ago, and since then I've had to run fsck on startup or in a recovery console about four or five more times to be able to log in (due to problems ranging from not booting to non-functional I/O devices), and each time the amount of errors that need to be fixed grows. I can't help but suspect that there is an underlying problem, and I'm hoping that reinstalling ubuntu is the most drastic move I need to take. Does anyone know if there's a better way to fix a corrupt filesystem so the problem won't continue to return?

Sorry for the long block of text. Any ideas would be greatly appreciated.

---

### Post by oldos2er on 2009-03-16
Your hard disk could be dying. I suggest you backup any data you don't want to lose.

---

### Post by bla687 on 2009-03-16
That's kind of what I'm afraid of. I don't have much to back up, I was just hoping there might be an alternative explanation, since I haven't even had the thing for very long. At least I don't think the warranty has expired yet.

---

### Post by Slim Odds on 2009-03-16
LOL 

When I read the title I thought that you were advertising a new book..   ;)

---

### Post by redb on 2009-03-16
> **Slim Odds said:**
> LOL 

When I read the title I thought that you were advertising a new book..   ;)


This is funny cuz it's Topical humour.

---

