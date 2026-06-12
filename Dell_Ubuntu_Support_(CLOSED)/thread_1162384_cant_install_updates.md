---
title: "cant install updates"
date: 2009-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by therumblebox on 2009-05-17
it says i need to update, but it wont let me check for updates. and every time i download the updates, they wont install. i really hate this thing.

---

### Post by coffeeaddict22 on 2009-05-21
Hi,
Welcome to Ubuntu!
First up, I understand the feeling- I spent a few days getting wireless going myself once- but posting "I hate this " in a forum is unlikely to get you lots of keen helpers.  We can't fix your problem, we can only make suggestions, but you're going to have to do the work.  Because of that,  you've got to kinda sound like you might be willing to work with the help (at least a bit  :-) ).

I'm not 100% certain what your problem is.  What version of Ubuntu are you running?  if you open a terminal and type in ```
uname -a
``` you'll get a line of info that you can post back/ do whatever you like with; it tells you most of the details of what's version is on your machine.

A common problem has been the package manager not updating properly.  What tends to happen is the system tells you it wants to update, but then will only do a partial upgrade.. and then does it again the next day.. and again... and so on.  If that's the problem, in a terminal type ```
sudo apt-get update
``` and see if that fixes it.  If it doesn't, can you be a bit more specific about the problem?

---

