---
title: "New to Ubuntu, Error message already :-("
date: 2009-02-01
forum: General Help
---

### Post by sdlong92 on 2009-02-01
Hello,

I just recently installed ubuntu today and already have a problem. I was following directions from this website 'https://help.ubuntu.com/community/WorldofWarcraft' and only made it to step 2... which is to type in:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

but it tells me that there is no valid openPgp data found there. So I decided it was about time to give up WoW anyway. So I just stopped there and went internet browsing for a while. Anyhow, I then later went to Synaptic Package Manager but it shows error:

E: Type '--2009-02-01' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report

I then used 'gedit' to get this for you folks so see if you could help at all since on I did some searching and it seems you need it:

--2009-02-01 18:42:48--  [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list)
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 180 [text/plain]
Saving to: `hardy.list'

     0K                                                       100% 11.2M=0s

2009-02-01 18:42:49 (11.2 MB/s) - `hardy.list' saved [180/180]

Any help that can be given would be really appreciated. It's my first day on Ubuntu and I am already afraid that i broke my computer.

Thanks in advance for any help.

---

### Post by mb_webguy on 2009-02-01
You haven't broken your computer.  :)

You simply need to add the GPG key for the Wine repository, which is what you attempted to do in step 2.  Follow [these instructions]("http://www.winehq.org/download/deb") to add the Wine repository, install Wine, then pick up at step 3.

---

### Post by sdlong92 on 2009-02-01
> **mb_webguy said:**
> You haven't broken your computer.  :)

You simply need to add the GPG key for the Wine repository, which is what you attempted to do in step 2.  Follow these instructions to add the Wine repository, unstall Wine, then pick up at step 3.

Thank you for yourhelp Webguy, good to know I didn't break anything yet (I guess that's for tomorrow). But you say to "follow these instructions to add the Wine repository", and I see no instructions or a link. Am I missing something (sorry, it really is my first day T.T).

thanks again, 
-sophy

---

### Post by mb_webguy on 2009-02-01
Oops.  :oops:

I mean to add [this link]("http://www.winehq.org/download/deb") to the words "these instructions".  Sorry!

---

### Post by sdlong92 on 2009-02-01
That seemed to have done it Webguy. Thanks for helping me with this. I don't regret installing this os anymore!

Moderator, please lock this thread. Thanks again

---

