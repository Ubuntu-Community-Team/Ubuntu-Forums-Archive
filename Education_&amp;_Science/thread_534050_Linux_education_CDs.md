---
title: "Linux education CDs"
date: 2007-08-24
forum: Education &amp; Science
---

### Post by x1a4 on 2007-08-24
Does anybody know of the existance of good, high quality educational CDs, teaching the mundane how to Linux?  

Thank you.

---

### Post by daveshields on 2007-08-24
Re "Does anybody know of the existance of good, high quality educational CDs, teaching the mundane how to Linux?"  

None come to mind. I tried to find something via Google with 'linux educational cd's" but the results from that show that "educational cd" is now used for bootable "live" cd's that people can use to learn about software without installing it; for example, the basic 7.04 install cd is also an "educational cd."

There are many other ways to learn Linux, but I think the key point is that as soon as possible you have to do Applications->Accessories->Terminal to start a shell window and then begin to learn how Linux is put together. By the way this won't be mundane; I expect you'll find it lots of fun.

Note that the basic ideas in Linux have been around for close to forty years now and (this is perhaps the only prediction about the future of operating systems in which I have some confidence) will be around for decades to come. What you do learn will be relevant.

Here are some possibilities:

1) If you like printed books I recommend William von Hagen's "Ubuntu Linux."  It has close to 900 pages, is quite well-written and includes many diagrams. It also includes a CD with Ubuntu itself and some additional programs.

2) Many useful documents can be found online at [http://tldp.org](http://tldp.org) (The Linux Documentation Project) 

3) You can also use Google et.al to find materials; search for example on "bash tutorial."

4) There are the many books from O'Reilly, [http://oreilly.com](http://oreilly.com) . You can find many of them in a nearby bookstore. Browse to see if any look interesting.

5) You can start from the ground up. Open that terminal window, type a command

```
$ echo "hello world"
$ date
$ whoami
$ pwd
$ ls
$ ls -tl
```

See what happens. Then go off and learn these commands. I just learned while preparing this response that wikipedia now has entries for many of them; for example, look up "ls" there. Figure out what that "-tl" does.

Or poke around your system looking for scripts. For example, take a peek at the scripts in /etc/init.d These are run when your machine starts up. Look for frequently mentioned commands and similar constructs, that sort of thing.

Then learn about "tar." After that take on "grep." By the time you get to "find" -- or more likely sooner -- you'll be answering newbie questions of Unbuntu forums, sharing your new-found knowledge in the form of beans.

Good luck.

---

