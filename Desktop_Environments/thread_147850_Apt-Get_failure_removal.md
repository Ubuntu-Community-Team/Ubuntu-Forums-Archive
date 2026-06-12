---
title: "Apt-Get failure removal"
date: 2006-03-20
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-20
I recently tried to install Seti@home on my Ubuntu machine, for a lark. 
I used what was supposed to be the normal command:
$ sudo apt-get install setiathome

Now, that in itself isnt the problem. Rather when it tried to get the file(s), it connects to a particular server at UCLA Berkley, which is either down or nonexistent. It times out eventually, throws an error and then stops altogether.
Now Im not bothered that I dont have the program; no big deal.

What bothers me now is that whenever I install any other program, it tries to get this package after all the rest, so Im stuck sitting at this eventually-timing out connection to alien.berkley. etc etc.

My question - how do I clear out the 'buffer' of packages apt-get thinks its supposed to get, so I dont encounter this problem anymore?

---

### Post by dermotti on 2006-03-20
**apt-get clean** shold get rid of cached files....
but you should also run an **apt-get update** to refresh your sources

---

### Post by bluemike807 on 2006-03-21
I just tried the apt-get clean, it didnt work, it's still trying to install the packaged setiathome that it wasnt able to before, even if Im trying to install something else.

Please help!

---

### Post by dermotti on 2006-03-21
**apt-get -f install** not work?
or even **apt-get -m install** is worth a try

---

### Post by bluemike807 on 2006-03-21
In the sense that is removes the Not Fully Installed setiathome program, No, it doesnt work.

It just starts the install process, which consists of it trying to download the necessary files from the server, which hangs (bad address I guess). 

I've apt-get update(d) several times, and I have all the official (Universe and Multiverse) repositories open. I guess I've just got a bad source.

My question is *How do I get rid of it!?!?*

---

### Post by dermotti on 2006-03-21
Mmmm, have you removed the repository from your /etc/apt/sources.list ?

---

### Post by bluemike807 on 2006-03-21
you misunderstand, its not any one repository, rather it is the particular server
(alien.ssl.berkeley.edu|128.32.18.176|:21) which is not responding. There's no mention of it is the sources.lst file.

Here is the output from 
sudo apt-get -f install :

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--16:15:44--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu) .tar
           => `/tmp/fileZc7QDA'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...

It then hangs at this point and I can either wait 10 minutes for it to time out or Ctl-C it. And it always does this, whenever I apt-get install something

---

### Post by dermotti on 2006-03-21
Odd. Is it showing up in synaptic under Status --> Not installed (residual config)?

---

### Post by bluemike807 on 2006-03-21
I didnt think to check Synaptic (d'oh!).

It wasnt under Not Installed, but rather Synaptic had it listed as fully installed. So I blew the crap out of it, and all seems to be well in the Universe again.

Phew.

Thanks for the help!

---

