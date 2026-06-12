---
title: "Installing downloaded applications"
date: 2005-10-24
forum: Desktop Environments
---

### Post by whitesaber on 2005-10-24
I am extremely new to Ubuntu Linux (or any Linux for that matter).  I would like to know how to install applications that I have downloaded from the Internet.  For example, Mozilla Thunderbird.  I have this file downloaded called "thunderbird-2.0.7.tar.gz".  I extract the files contained and have no clue what to do.  Also I downloaded Yahoo Instant Messenger with similiar results.  How do I install these applications?

---

### Post by heimo on 2005-10-25
Easiest way to install software is to use package manager (for example: Synaptic Package Manager):
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage](http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-usage)
Thunderbird is in package mozilla-thunderbird

---

### Post by Knowles on 2005-10-25
well if you can extract you can also se ethere are 2 nice files. 1 says INSTALL the other says README. I suggest you go through both of them and see what they say. Thunderbord I know for a fact is a binary install so its abit different from most compiling you will do. BUt none the less mak esure you read them. Also I would advise you to open up the terminal

Applications > Accessories > Terminal

and do a 

cd <location of extracted path>

cd /home/knowles/sources  << for example

then if you read the install file you will have to do a few commands like

./configure
make
make install

remember never compile in a folder with a space

you have to log in as root to install stuff

su <-- in terminal

if you havent set you root pass word type

sudo passwd root

this probably crap talk through but i am tired its 5 am

---

### Post by xmastree on 2005-10-25
Take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=81336"), it should answer a few questions for you.

---

### Post by whitesaber on 2005-10-25
Wow, thanks.  Ya'll have been quite helpful so far.  I got Mozilla Thunderbird to install using Synaptic Package Manager but I don't see YIM in the package list.  I'm not sure how to proceed...

---

### Post by aysiu on 2005-10-25
[QUOTE=whitesaber]I don't see YIM in the package list.  I'm not sure how to proceed...[/QUOTE] What's wrong with [GAIM](http://gaim.sourceforge.net/faq.php#q16)? If you [enable extra repositories](http://www.psychocats.net/sources.html), you can get even more package selection (though YIM won't be in the package list).

---

### Post by kingsidy on 2005-10-25
just enable the repositories using the "unofficial ubunu guide" and get it from synaptics. that is the easiest way.

---

### Post by aysiu on 2005-10-25
[QUOTE=kingsidy]just enable the repositories using the "unofficial ubunu guide"[/quote] [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) is outdated right now. > and get it from synaptics. that is the easiest way. Yahoo Instant Messenger [isn't there](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=yahoo+instant+messenger&searchon=name&subword=1&version=all&release=all), anyway, even if you add the Universe repositories. GAIM is a better choice (and easier to install).

---

