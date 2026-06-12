---
title: "Compiz Fusion w/o Internet connection."
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by Espreon on 2007-07-26
I would like to setup Compiz Fusion on a computer with no Internet connection, so what are all the dependencies of all the Compiz Fusion (with all Extra and unsupported plugins), no KDE stuff?

---

### Post by Happy_Man on 2007-07-26
Uh.... you can manually download all the files from the git repos using one of the many scripts available on the internet using another computer..... then transfer all the files in their file structure to the computer in question.... but that's a lot of hassle. Generally, if it's a question between "internet not working" and "whatever"... fix internet before whatever.

Having said that..... what's up with your internet?

---

### Post by Espreon on 2007-07-26
There is nothing wrong with my Net connection, it is just that the comp I am trying to install it on does not have a wireless card or an eternet card. I know how to deal with getting the files to the Netless comp, I am just asking what dependencies I'll need to download that are not included with a fresh install of Feisty. The comp I am using right now is the only device in my house (other than my Wii) that has Net access.

---

### Post by tact on 2007-07-27
What an interesting question.  I dont really have an answer but I guess a process that might work, and also keep your synaptic database up to date even without a network connection might go like this:
1.  on another feisty machine with a network connection, make sure to add all the software sources for Compiz-Fusion etc to list of repos in /etc/apt/sources.list

2. do a sudo apt-get update on the machine with the network connection
3. copy the sources.list to the machine with no connection
(now the part I have no detail on...not sure its possible even..)
4. find the databases that are downloaded whenever you do a sudo apt-get update and copy those to the machine with no connection.

This would have your non-networked machine with a fully updates list of files available in all the repos (including the Compiz stuff).  Your synaptic package manager will know whats installed on that system.

You could then run synaptic, checking all the packages you want (for compiz) and then see what dependencies are added for each item you select.   This is a "dry run" of course.

Then on the networked machine you can grab all the needed packages, burn to CD and back to the other machine install thru synaptic from CD

process only, theory only.  sorry if its mis-info or boring.

---

### Post by Espreon on 2007-07-27
Interesting, I will try it out tomorrow.

---

### Post by spayne22 on 2007-11-30
hi,
i was just wondering. i am operating on a MacBook Pro with internet, and i have ubuntu Gutsy installed on my dell dimension 4550, can anyone tell me how i install Compiz Fusion on the computer w/o internet. The computer with internet is not on Ubuntu so i cant download the updates from repository here.  Also could someone tell me which is the right one to install.
Thanx

---

