---
title: "darwinia"
date: 2006-08-22
forum: Gaming &amp; Leisure
---

### Post by s_h_a_d_o_w_s on 2006-08-22
darwinia installed fine but it won't run. it crashes after3 seconds. Has anyone got it running with dpper?

---

### Post by Tyler Oderkirk on 2006-08-31
It runs fine for me. Do you get any error messages?

---

### Post by borkabrak on 2007-10-10
Darwinia won't run for me, either.  Doesn't take three seconds, either, but instantly exits with this:

```
.
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

Now, running 'gcc --version' indicates that I'm running version 4.1.2, but that's the latest version in the repository, and I'm hesitant to try to install it, if it's somehow not required for others to run.  

I got my copy of darwinia from Introversion Software's own website, if that helps.

Any ideas?

---

### Post by Sockerdrickan on 2007-10-10
This darwinia release you have must be really new, correct?

---

### Post by borkabrak on 2007-10-10
GOT IT!

In case this post is viewed individually, here's the story till now:  I downloaded darwinia from Introversion's website, installed it, and got this error when I tried to run it: 

[B].
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
[/B]

I was stymied by this, as gcc 4.2 is not yet in the official repository.  Then I noticed that it was one of darwinia's own files that is trying to use that version.  Did I *have* to use their version? I ran this:

[B]$ locate libgcc_s.so.1

/lib/libgcc_s.so.1
/home/jcarter/games/darwinia/lib/libgcc_s.so.1
[/B]
See?  I've got my *own* version of libgcc_s.so.1  But do I care about that?  Is it any different?  

[B]$ locate libgcc_s.so.1 | xargs diff

Binary files /lib/libgcc_s.so.1 and /home/jcarter/games/darwinia/lib/libgcc_s.so.1 differ
[/B]
Aha!  What if I use my own version, instead of the one that shipped with darwinia?

[B]$ mv libgcc_s.so.1 libgcc_s.so.1.as_shipped
$ ln -s /lib/libgcc_s.so.1 ./libgcc_s.so.1
[/B]

Worked like a charm!  Darwinia runs just fine now!

I hope this helps someone.  I was about to kvetch to Introversion, and I really didn't want to -- I *like* people who make games for Linux.

---

### Post by borkabrak on 2007-10-10
O hai, Tux0r -- that was a really fast response.

And yes, I just downloaded the thing less than a week ago.  Seems the repos may still be catching up.  But isn't gcc 4.2 still under development?  I wonder if it's wise for Introversion to code against uber-new libraries..

---

### Post by Sockerdrickan on 2007-10-10
What I know is it's in gutsy :lol:

---

### Post by borkabrak on 2007-10-10
Ha!  I had no idea we were near another release!  Woohoo!  Looks like 8 days left!

I guess it was *my* information that was out of date..  :)

---

### Post by padawan5555 on 2009-04-25
Thank you.

---

### Post by Tofu_Madness on 2009-08-30
Well, since this thread is already came back from the dead..

I got a same error message as borkabark. So, as borkakark suggested I copied libgcc from /lib/ to /usr/local/games/darwinia/lib/, and volia it fixed the problem.

:)

---

### Post by Perfect Storm on 2009-08-30
necro posts.

Thread closed.

---

