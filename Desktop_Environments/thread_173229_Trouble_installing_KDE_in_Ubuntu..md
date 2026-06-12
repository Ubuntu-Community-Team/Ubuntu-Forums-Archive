---
title: "Trouble installing KDE in Ubuntu."
date: 2006-05-10
forum: Desktop Environments
---

### Post by deadyeti on 2006-05-10
Hello, I recently installed Ubuntu and I would like to try out the KDE desktop environment as well as Gnome to see which one I prefer.  I have found several places to tell me how to go about this but I keep coming up with problems and I figured this would be the best place to find answers for a linux newbie like myself.

XXXXX@fujitsu-laptop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

I have tried a few other options with the same outcome.  Im not sure what to do about this.  THanks in advance for any help on the matter.

-Yeti

---

### Post by louis_nichols on 2006-05-10
well... it means you probably on't have the needed repositories for that. Try to build yourself a complete list [here]("http://www.ubuntulinux.nl/source-o-matic"), then import the keys and everything and retry installing kubuntu-desktop. There is a slightly easier way, but I think this one is better in the long run.

---

### Post by deadyeti on 2006-05-10
Unfortunately my skill level is not high enough to have much of a clue about what I should do at this point with the link you provided.  Maybe I will just learn to love Gnome.

---

### Post by louis_nichols on 2006-05-10
Don't worry! Noone was born already knowing stuff. Sorry I wasn't more explicit.

I think, at this point, as a good investment for your future experience with (k)(x)Ubuntu, or any other Linux distro for that matter, you should read [this page]("https://wiki.ubuntu.com/Repositories?highlight=%28repos%29")

There is also a link there to a page that shows you how to add extra repositories. Start by following that one, then I think you'll know what you need to do with the link I posted.

---

