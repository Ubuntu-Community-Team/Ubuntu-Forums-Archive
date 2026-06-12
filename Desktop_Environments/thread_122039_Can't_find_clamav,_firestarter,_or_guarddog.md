---
title: "Can't find clamav, firestarter, or guarddog"
date: 2006-01-26
forum: Desktop Environments
---

### Post by browndog on 2006-01-26
Hi all,

I've run countless searches through the Adept package manger search field looking for clamav, firestarter, and guarddog, and none of them are anywhere to be found.  Am I typing something in wrong?  I've also tried every combination I could think of, but no matter how I type the words in I don't find the software...are we sure these three packages are still available through Adept?  Some very well meaning Ubuntu users recommended I install these if I want AV and firewall software, but I cannot find them for the life of me.  If you know for a fact that any or all of these are available through Adept, please give me the exact syntax to type in to find them.  :confused:   Thanks so much.

BD

---

### Post by MartinG on 2006-01-26
As on the other thread you've started on this, I assure you they *are* there -- the problem is (almost) certainly your /etc/sources.list file, which tells adept which repositories to search.  As installed, (K)Ubuntu does not enable all repositories.  Try this reference to enable the extra ones:
 
 [http://makuchaku.info/amnesty/#extrarepositories](http://makuchaku.info/amnesty/#extrarepositories)

Next run sudo apt-get update (or update in adept), and then you should be able to find what you are looking for.

---

### Post by browndog on 2006-01-26
[QUOTE=MartinG]As on the other thread you've started on this, I assure you they *are* there -- the problem is (almost) certainly your /etc/sources.list file, which tells adept which repositories to search.  As installed, (K)Ubuntu does not enable all repositories.  Try this reference to enable the extra ones:
 
 [http://makuchaku.info/amnesty/#extrarepositories](http://makuchaku.info/amnesty/#extrarepositories)

Next run sudo apt-get update (or update in adept), and then you should be able to find what you are looking for.[/QUOTE]

Thanks Martin.  I'm completely new at this and feeling my way along.  I'll use your suggestion right away.

BD

---

