---
title: "apt-get update (urgent) (Solved)"
date: 2005-11-12
forum: Desktop Environments
---

### Post by akurashy on 2005-11-12
Well I was in ubuntu irc, and well there were some answers on how to fix the GPG error thing, well I took the time and checked. 

they said to do 

sudo rm -rf /var/lib/apt/lists/*

i did, well now i can't update

david@akulinux:/var/lib/apt/lists$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.


is there a way to fix this? i'm kinda nervous >< *first time apt-get update breaks*

---

### Post by cvmostert on 2005-11-12
oops you deleted all your list files! well, im not an expert but thats how its looks... try and get the files back... probably copy it from someone... 

i also get the GPG error... i will rather not rm anything...

---

### Post by aysiu on 2005-11-12
Have you tried [Googling the error?](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=%22E%3A+Lists+directory+%2Fvar%2Flib%2Fapt%2Flists%2Fpartial+is+missing%22&btnG=Search)

---

### Post by cvmostert on 2005-11-12
nope, :-) will do... 

funny how reliant one can become on this ubuntuforums!

---

### Post by cvmostert on 2005-11-12
i found this in a thread..... try it... remember i am no genius in linux, own risk...

Try this from

[http://www.linuxquestions.org/questi...&highlight=GPG](http://www.linuxquestions.org/questi...&highlight=GPG)

1) Restore the default keys in Synaptic (settings > repositories > authentication > restore desault keys

2)

code:

sudo apt-get clean



3) Change the repositories (/etc/apt/sources from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) to [http://archive.ubuntu.com](http://archive.ubuntu.com) This actually got rid of one of the BADSIG instances but I still had one......

4) Commented out the cd in /etc/apt/sources

Finally::

5) I found on another forum, the suggestion to create a new /var/lib/apt/lists folder. (you also need a new lists/partial folder...) I renamed my old lists folder then created a new one with:

code:

:/var/lib/apt$ sudo mkdir -p lists/partial



Then one more

code:

sudo apt-get clean


code:

apt-get update

This worked for me (so far) but I don't seem to be getting many updates. Thanks to jkmb111.

---

### Post by akurashy on 2005-11-12
Well I followed the restore thing and when to the terminal and typed the apt-get clean and it did not work =/

---

### Post by akurashy on 2005-11-12
wait nvm!

got it working :D

---

