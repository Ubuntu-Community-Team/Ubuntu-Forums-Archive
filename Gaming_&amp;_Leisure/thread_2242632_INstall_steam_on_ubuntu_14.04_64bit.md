---
title: "INstall steam on ubuntu 14.04 64bit"
date: 2014-09-03
forum: Gaming &amp; Leisure
---

### Post by farbod2 on 2014-09-03
Hi,  I've installled steam from ubuntu software center and i got this error:  You are missing the following 32-bit libraries, and Steam may not run: libc.so.6  I've searched and I found that I shoud change my essensial files I just  dont want to harm my System for Game if there is a safe way let me know.  tnx

---

### Post by oldrocker99 on 2014-09-03
Try this:
```
sudo apt-get install libc6*
```

This **will** install a whole raft of files, including the 64-bit and 32-bit versions, but they don't take up a lot of space, and you'll have them all properly installed.

It will **not** break your system at all.

---

### Post by farbod2 on 2014-09-03
> **oldrocker99 said:**
> Try this:
```
sudo apt-get install libc6*
```

This **will** install a whole raft of files, including the 64-bit and 32-bit versions, but they don't take up a lot of space, and you'll have them all properly installed.

It will **not** break your system at all.

Tnx for ur great answer but I got some error !

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcgi-application-plugin-captcha-perl : Depends: libdata-random-perl but it is not going to be installed
 libcloog-isl-dev : Conflicts: libcloog-ppl-dev but 0.16.1-5 is to be installed
 libclutter-gst-2.0-doc : Conflicts: libclutter-gst-doc but 1.6.0-2build1 is to be installed
 libcuda1-304 : Conflicts: libcuda-5.0-1
 libcuda1-304-updates : Conflicts: libcuda-5.0-1
 libcuda1-331 : Breaks: libcuda-5.0-1
                Breaks: libcuda-5.5-1
 libcuda1-331-updates : Breaks: libcuda-5.0-1
                        Breaks: libcuda-5.5-1
 libcunit1-ncurses : Conflicts: libcunit1 but 2.1-2.dfsg-1 is to be installed
 libcunit1-ncurses-dev : Conflicts: libcunit1-dev but 2.1-2.dfsg-1 is to be installed
 libcurl4-gnutls-dev : Conflicts: libcurl4-nss-dev but 7.35.0-1ubuntu2 is to be installed
                       Conflicts: libcurl4-openssl-dev but 7.35.0-1ubuntu2 is to be installed
 libcurl4-nss-dev : Conflicts: libcurl4-gnutls-dev but 7.35.0-1ubuntu2 is to be installed
                    Conflicts: libcurl4-openssl-dev but 7.35.0-1ubuntu2 is to be installed
 libcurl4-openssl-dev : Conflicts: libcurl4-gnutls-dev but 7.35.0-1ubuntu2 is to be installed
                        Conflicts: libcurl4-nss-dev but 7.35.0-1ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

```

now what ?:/

---

### Post by farbod2 on 2014-09-03
Solved with : sudo apt-get install '^libc6.*'
^_^

---

### Post by oldrocker99 on 2014-09-03
I may have not given you the best answer:oops:, but I am very glad you fixed the problem!

---

### Post by pinportal on 2015-04-28
Hey man, this   sudo apt-get install '^libc6.*'    worked for me too!

Using Lubuntu 14.04.2 LTS 64bits.

Thank you very much!!!   :D

---

### Post by brian62 on 2015-04-28
> **farbod2 said:**
> Solved with : sudo apt-get install '^libc6.*'

Cool! I didn't realize you could use wildcards when installing using apt-get.

---

### Post by Cameron_Ferguson on 2015-05-09
i got an error to but mine is "libGL.so.1" if any body could help i would really appreciate it

---

### Post by kahwin-lee on 2015-05-11
> **Cameron_Ferguson said:**
> i got an error to but mine is "libGL.so.1" if any body could help i would really appreciate it

Having the same problem here :

Error
You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1

then STEAM client pop up : Fatal Error : Failed to load steamui.so

---

### Post by ILoveTacoTuesday on 2015-05-13
Hey dude,
I had the same problem but then I rebuilt steam and it worked.
Try:
sudo apt-get install steam

That should try and re-build everything and be good to go

---

### Post by gabe-kelly on 2015-06-06
Hi I had this problem too and after following the advice of the thread to the end, my problem was solved. A HUGE THANK YOU to you guys for the solution.

---

### Post by Tehepic on 2015-06-10
> **oldrocker99 said:**
> Try this:
```
sudo apt-get install libc6*
```

This **will** install a whole raft of files, including the 64-bit and 32-bit versions, but they don't take up a lot of space, and you'll have them all properly installed.

It will **not** break your system at all.

I got this when I tried that

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

How to fix this?

ubuntu 15.04

---

### Post by andrejshekerov on 2015-06-13
It seems like you have some other processes running (software center, synaptic etc.). Make sure you are not downloading anything at the moment and try again. If that doesn't work, try rebooting your pc or disconnect and then connect to your network. Hope I helped!

---

### Post by williamrespinola on 2015-06-26
Hey man, this   sudo apt-get install '^libc6.*'    worked for me too!

Using Lubuntu 14.04.2 LTS 64bits.

Thank you very much!!!   :grin:  [2] haha!

---

### Post by Letlaka on 2015-08-07
> **farbod2 said:**
> Solved with : sudo apt-get install '^libc6.*'
^_^

This also solved my problem =d>" title="Applause" style="cursor: pointer;">

---

### Post by philippe-mosca on 2015-08-22
```
sudo apt-get install '^libc6.*'
``` followed by ```
apt-get install steam
``` worked perfectly fine for me, thanks a lot ! :D

---

### Post by arno5341 on 2015-08-29
> **ILoveTacoTuesday said:**
> Hey dude,
I had the same problem but then I rebuilt steam and it worked.
Try:
sudo apt-get install steam

That should try and re-build everything and be good to go

I m on 14.04.3 and re-building worked for me thanks.

---

### Post by deron3 on 2015-08-31
I hate to admit it, but I'm a Windows guy.  Trying Ubuntu for the first time.  Kinda like leaving the Empire, and joining the Relabels.  How do I use the 
"sudo apt-get install libc6*" fix?  What are the steps.

---

### Post by oldrocker99 on 2015-09-01
> **deron3 said:**
> I hate to admit it, but I'm a Windows guy.  Trying Ubuntu for the first time.  Kinda like leaving the Empire, and joining the Relabels.  How do I use the 
"sudo apt-get install libc6*" fix?  What are the steps.

1. Open a terminal.
2. Type
```
sudo apt-get install ^libc6*
```

And that should do it. **sudo apt-get install [name of package]** is how you install software in Ubuntu, or any Debian-based distribution.

The sudo at the beginning of the line (pronounced su-doo, not su-dough) means "super user do." It is how you start any command that requires root (administrator) access. You'll be prompted to enter your password, and nothing will show up on the screen when you type it in. If you entered it correctly, the process will start. If you didn't, you'll see "Sorry, try again." You have three tries to enter it correctly.

Any other questions, just (please) ask! And a hearty **WELCOME** to the Ubuntu community, and the *best* OS there is, with more advantages over Windows than you can shake a mouse at.

---

### Post by ethan27 on 2015-09-01
Easiest solution:
```

sudo apt-get install steam
```

---

### Post by oldrocker99 on 2015-09-02
> **ethan27 said:**
> Easiest solution:
```

sudo apt-get install steam
```
He's right, you know; it's exactly how I installed it. The advice given above was for people (and there seems to be quite a few) who have had trouble.

There is this:
```
sudo apt-get purge steam
sudo apt-get install steam
```
which will no doubt work. (I think)

---

### Post by Snipa299 on 2015-09-03
I don't know what I'm doing wrong, but whenever I try the install code for Steam it says that the package cannot be found. I THINK I'm using some form of Debian, but I don't know how to check. My original hardrive died with Windows on it so I installed Linux on a new one because it was free.

EDIT: I found another article on the Debian Wiki and the Ultimate Guide to LInux for Windows Users ([http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html))

---

### Post by ethan27 on 2015-09-03
Snipa I'm not sure if you can or not sense I've never done this before but you might be able to use a different Package Manager. In the article you gave us it lists three different APTs. Advanced Packaging Tool (APT), Yellowdog Updater (YUM), and ZYpp (libzypp). Not sure it will work but just give it a try and it might just solve your problem.

---

### Post by wrynn-cz on 2016-01-17
> **farbod2 said:**
> Solved with : sudo apt-get install '^libc6.*'
^_^
Thanks

---

### Post by ryner-tom on 2016-04-04
> **farbod2 said:**
> Solved with : sudo apt-get install '^libc6.*'
^_^

Thanks a lot! Chiming in 1,5 years after your reply to the Steam related matter. 

Your fix solved my problem!

Cheers/Tom

---

### Post by doublebackslash on 2016-05-15
DO NOT DO THIS. A friend tried it and now I get to spend the next X hours of a perfectly good evening untangling the mess of libs that it installed and failed.

This was always bad advice. Asterisks are bad advice unless you, the person that owns the box, know full well the consequences.

Just think of every asterisk like a little notice saying *This will end badly more often than not.

---

### Post by doublebackslash on 2016-05-15
> **oldrocker99 said:**
> Try this:
```
sudo apt-get install libc6*
```

This **will** install a whole raft of files, including the 64-bit and 32-bit versions, but they don't take up a lot of space, and you'll have them all properly installed.

It will **not** break your system at all.

This is what it wanted to install on my system 15.10. This is some of the worst advice ever given. DO NOT DO THIS.
[http://pastebin.com/ePK9Trnb](http://pastebin.com/ePK9Trnb)

---

### Post by luthonda on 2016-11-22
[COLOR=#000000]sudo apt-get install steam

worked to me!
is better than [/COLOR][COLOR=#000000]sudo apt-get install libc6*
not recomended[/COLOR]

---

### Post by sirjrz on 2017-01-19
2017 (sudo apt-get install '^libc6.*') still working, you guys Rock!

---

