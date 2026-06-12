---
title: "Problem Installing Ruby"
date: 2006-09-12
forum: Desktop Environments
---

### Post by atraeyu on 2006-09-12
Hello,
After a few weeks of trying to set up a fedora core 5 development server on which to learn ruby and eventually ruby on rails, I decided to switch to Ubuntu at the recommendation of friends.

I just finished a fresh install earlier a few hours ago.  I immediately went to the ruby-lang.com website (to see they just updated!) and went to the [Ruby in 20 Minutes Link]("http://www.ruby-lang.org/en/documentation/quickstart/") and followed the download instructions:

For example, on Debian or Ubuntu apt-get provides an easy and elegant solution:

% apt-get install ruby1.8 irb1.8 rdoc1.8

However - this produces the error: Couldn't find package irb1.8.  When I search packages.ubunto.com it says it is included in the Ruby1.8 package.

I ran the Synaptic Package Manager and had it install: ruby1.8, ruby1.8-dev, lilruby1.8, lilruby1.8-dbg.  These are all version 1.8.4 packages.

I did this, it said everything was installed correctly.  If I use "sudo apt-get install ruby1.8 ruby1.8-dev lilruby1.8 lilruby1.8-dbg it says packages are already installed.

Next step on the ruby website: 

# If you’re using Linux, open up a shell and type irb and hit enter. 

I do this and: bash: irb: command not found

... I'm new to linux, new to ubuntu, and new to ruby.  I've been looking for an answer for several hours now, but I can't seem to find it.

Any idea how I should proceed?
Thanks!

---

### Post by croak77 on 2006-09-13
There is a seperate package called irb1.8. It's in the repo's. So try;
```
sudo apt-get install irb1.8
```

If that doesn't work then try just with 'irb' instead of 'irb1.8'.

---

### Post by mdurham on 2006-09-13
run Synaptic and search for "irb" in names, this will find it.

---

### Post by atraeyu on 2006-09-13
Ah yes - that's the problem.  

sudo apt-get install irb1.8
and
sudo apt-get install irb

Both return: Couldn't find package irb1.8 / irb (respectively)

Searching for "irb" or "irb1.8" in Synaptic returns a single package: "Ruby1.8" which is already installed.  I'm doing something wrong, no idea what it is though. :(

---

### Post by atraeyu on 2006-09-13
Also, searching synaptic for rdoc returns only the "Ruby1.8" package - is it possible that the 1.8.2 libraries were bundled separately, but the 1.8.4 libraries are bundled all together in one ruby1.8 package ... and they just haven't updated the instructions on their site?

---

### Post by mdurham on 2006-09-13
atraeyu, is it possible that you don't have all the repos enabled?
sorry I can't tell you which repo it's in, maybe someone else knows???

---

### Post by atraeyu on 2006-09-13
That's absolutely possible ... I'm completely new to Ubuntu and pretty new to Linux in general (just a bit of fedora experience).  Before searching for packages, should I be adding package repositories?

---

### Post by atraeyu on 2006-09-13
mdurham: You were absolutely correct.  I had to enable the community support repositories(universe) 6.06 source & binary.  I really appreciate the help, thanks!

---

### Post by mdurham on 2006-09-13
atraeyu, I'm glad that you got it to work.
Another Ruby user can only be a good thing.

---

