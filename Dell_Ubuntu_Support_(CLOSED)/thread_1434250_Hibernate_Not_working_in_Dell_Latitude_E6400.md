---
title: "Hibernate Not working in Dell Latitude E6400"
date: 2010-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rainbow99984 on 2010-03-20
Hi, I'm just a Newbie, I installed (actually by some other person) Ubuntu 9.10. I just want to use Hibernate and suspend. both goes well but wake up for both of them Hanged up system.

In case of Suspend system goes off(not completely) the  power button LED blinks. Now what ever i tried like pressing Enter key, Mouse Movement, Pressing Power button(not holding for long it just restart the system) but no effect.

In case of Hibernate it goes off completely. When I restart it says waking up but freeze there for long nothing happens.

Both occasion i just restart the system.
Any suggestion or workaround welcome 
PS: please guide in little bit detail as I'm just learning Linux....
Thanks
Rahul:KS

---

### Post by pizza-is-good on 2010-03-20
I'm still working on it (as I told you in my pm), but if you could give us more info that'd be great.

Dual booting?
What kernels do you have installed?

All of your computer's specs. 

etc, etc. Everything you can tell us will make it easier.

~pizza

---

### Post by rainbow99984 on 2010-03-22
Hi, System details are :give by uname -a
Linux  2.6.31-20-generic #58-Ubuntu  i686 GNU/Linux
Gnome 2.28.1 
Core2Duo 
Ubuntu 9.10 karmic
Memory 3.4GiB
What else please let me know and ofcourse how to get it as well..  :)

Recently I tried Hibernate / suspend and both work few times and hang on few occasion can it be by the applications i left open

PS: when it was not working i don't have Nvidia driver installed 
But I do have it now Nvidia Server version 185 (can it be because of it? )

---

### Post by pizza-is-good on 2010-03-22
> **rainbow99984 said:**
> Hi, System details are :give by uname -a
Linux  2.6.31-20-generic #58-Ubuntu  i686 GNU/Linux
Gnome 2.28.1 
Core2Duo 
Ubuntu 9.10 karmic
Memory 3.4GiB
What else please let me know and ofcourse how to get it as well..  :)

Recently I tried Hibernate / suspend and both work few times and hang on few occasion can it be by the applications i left open

PS: when it was not working i don't have Nvidia driver installed 
But I do have it now Nvidia Server version 185 (can it be because of it? )

OK, thanks. I think that helps.

I tried with my E6400. Both suspend and Hibernate work. Hibernate takes a while to get into and get out of. The screen even flashes some errors while doing so, but it ends up working.

If it were windows we were dealing with, then I would guess that the open programs and uninstalled driver were the problem. But this is Ubuntu, and honestly I expect it to not have such silly problems.

Do the problems now happen more often than not?

Here is something else you might want to try:

You can have Ubuntu save your running applications upon shutdown, making it the same as hibernate. It might take a few extra seconds than hibernate to get it started up again, but the E6400 is a fast computer, so the difference is minimal.

I'm looking for input from someone else, since I am a little out of ideas.

(You might want to ask a mod to move the thread to Absolute Beginner Talk, that way more people might be able to answer. Not very many people 'surf' the Dell section of the forum. Just click on 'report abuse' on your first post, and then tell the mod that you'd like the thread moved.)

~pizza

---

### Post by rainbow99984 on 2010-03-24
Hi, Not sure How but Its working fine (with some delay and some flip in screen with some msg that flash in between ). I guess it can be by nvidia driver. Initially I did not have it. 
And yes I tried the save application feature and is similar good as hibernate.
Thanks.
(I'm marking it solved cause its working since then and even in your(pizza) system)
Rahul.

---

### Post by pizza-is-good on 2010-03-24
Well, glad you got it working.

You might want to join the Dell Latitude group in these forums. There is a few of us. Just follow the link in my signature.

~pizza

---

