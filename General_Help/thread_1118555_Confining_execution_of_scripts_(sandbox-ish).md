---
title: "Confining execution of scripts (sandbox-ish)"
date: 2009-04-07
forum: General Help
---

### Post by ohboyotero on 2009-04-07
Hey guys,

I'm a TA for a university course on, among other things, basic UNIX use. I'm trying to figure out how best way to programmatically run student homework scripts without risking:

    * Deletion or modification of any files outside of the current working directory, or creation of new files outside of the wd
    * Exploitation of known loopholes in *nix design (i.e. "LAWLZ I'Z R00T NOU!")

Students will be confined to scripts using built-in Linux/UNIX apps and commands. They will not be executing C/etc. code.

I'm not concerned with malicious students trying to actively attack the execution machine, but closing any obvious security vulnerabilities is an added plus.

I'll be running x86 Hardy server.

Is it enough to run their scripts as a special user which only has access to its home directory? I figure that's no good since there could be (and are) any unbounded number of world-readable/writeable files that could still be affected.

Chroot has the problem that anything outside of the chroot jail is not readable, including the binaries that they will need to invoke in their scripts (e.g. find, grep, cat, etc.). I'd have to duplicate enough of the file structure that their scripts would work, right?

Alternatively, I was thinking I could just run everything off of a live CD, but that's a last resort as it would be very tedious.

What do you pros think? Any thoughts would be appreciated. Thanks!

---

### Post by mcduck on 2009-04-07
How about using the guest account (available in 8.10 and later) to run the scripts?

The quest account has very limited access to anything outside it's own home. Also the guest user is created at the time you start the guest session, and removed afterwards so there would be no reason to worry about messing the user's home directory or files..

(And no, there really isn't any world-writable stuff outside user's home directories that user's could mess with. Even less when using the guest account as most of the file system isn't even readable.)

---

