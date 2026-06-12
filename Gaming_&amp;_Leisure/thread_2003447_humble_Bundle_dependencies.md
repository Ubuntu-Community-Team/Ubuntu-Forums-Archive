---
title: "humble Bundle dependencies"
date: 2012-06-14
forum: Gaming &amp; Leisure
---

### Post by Jack Vermicelli on 2012-06-14
Halfway on topic (since OP refers to these in particular), is anyone having the same problems as me, and/or would anyone have a solution for me?

I assigned "apt" to Ubuntu Software Center (which I had never used before) in order to install the games. They showed progress bars (which eventually went away), but nothing seemed to be installed so I ran them again, and now have 2 of the 4 games I bought installed.

However, for Limbo, I get ```
The following packages have unmet dependencies:

limbo: Depends: limbo-bin (= 1.0-0ubuntu4) but it is a virtual package
```I was emailed a repo to add in order to install Psychonauts, but not knowing anything about the format required, I copied the entire box into my sources, in the format ```
deb https://XXXXXXXXXXXXXXX@private-ppa.launchpad.net/commercial-ppa-uploaders/psychonauts/ubuntu precise main
``` I still get told that there's no such package in my sources when I try to install it through the software center however.

What am I doing wrong? Thanks.

edit:

I shouldn't've assumed that Ubuntu Software Center would update its lists when it runs. :- P    I ran apt-get update and now at least have Psychonauts available, but I'm getting a familiar message from it now also: ```
The following packages have unmet dependencies:

psychonauts: Depends: psychonauts-bin (>= 1.2) but it is a virtual package
```Any solution?

---

### Post by Perfect Storm on 2012-06-14
Post moved to its own thread.

---

### Post by cha5on on 2012-06-23
I don't know if you've contacted the humble bundle support team, but I did recently for the same issue and got back the following response:

> Hi cha5on,

We have emailed Canonical regarding the errors you are receiving, and we have also included this Ubuntu forum thread in the email (as this may be your post or the same issue) [http://ubuntuforums.org/showthread.php?t=2003447](http://ubuntuforums.org/showthread.php?t=2003447)

We will update you when we receive a response.

Sincerely,
Melinda
Support Ninja
Humble Bundle

Hopefully that means this will be resolved soon!

---

### Post by enroxorz on 2012-06-24
I'm having the same issue. I started a thread in Absolute Beginners, but I will dump my issue here


Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The folloowing packages have unmet dependencies:

swordandsworcery: Depends: swordandsworcery-bin (= 1.56-0ubuntu2) but it is a virtual package

The following packages have unmet dependencies:

limbo: Depends: limbo-bin (= 1.0-0ubuntu4) but it is a virtual package

The following packages have unmet dependencies:

lonesurvivor: Depends: lonesurvivor-bin (= 1.11d-0ubuntu2) but it is a virtual package

The following packages have unmet dependencies:

psychonauts: Depends: psychonauts-bin (>= 1.2) but it is a virtual package

---

### Post by zoopster on 2012-06-24
Post the error message you receive when trying to install psychonauts-bin using "sudo apt-get install psychonauts-bin". That will tell us what dep is missing (or any of the others that are having a problem) and we'll look into it further.

---

### Post by oldrocker99 on 2012-06-24
Interestingly, I had no problems whatsoever installing Psychonauts, and, in fact, Synaptic updated it yesterday.

---

### Post by cha5on on 2012-06-26
Unfortunately, it looks like those of us with 10.04 are out of luck for installation via software center:

> 

Hi cha5on,

We have emailed Canonical regarding the errors you are receiving, and we have also included this Ubuntu forum thread in the email (as this may be your post or the same issue) [http://ubuntuforums.org/showthread.php?t=2003447](http://ubuntuforums.org/showthread.php?t=2003447)

We will update you when we receive a response.

Sincerely,
Melinda
Support Ninja
Humble Bundle 


The downloadable packages on the humble bundle site itself do work, but some might take a bit of trickery to get working.  If you have questions about a specific game I can try to help sort out how to get things working.

---

