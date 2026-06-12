---
title: "M1330 fingerprint reader on Intrepid"
date: 2008-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shingalated on 2008-10-29
The fingerprint authentication on my M1330 stopped working after an upgrade to Intrepid.  I went through the steps to enroll my fingerprints in think finger, and that worked and verified no problem.  The common-auth file looks okay it still has the:
auth    sufficient      pam_thinkfinger.so
line in it.  Is anyone else experiencing this problem?

---

### Post by Shadowline on 2008-10-30
I had the same problem on my M1530.... the solution is to hit your "Enter" button after you swipe your finger...supposed to be a bug fix down the road I believe...

---

### Post by shingalated on 2008-10-30
Strange...

---

### Post by drsaamah on 2008-10-31
I did a clean install of Intrepid today so I haven't had time to mess around with ThinkFinger yet, but when I did an upgrade to Intrepid Beta a few weeks ago, I remember the upgrade involving some changes to the common-auth file.  So even if the line regarding thinkfinger is in there, the remainder of the file is probably coded differently in such a way to affect ThinkFinger's operation.
If you want to try, find a copy of the old default common-auth file, and edit it to thinkfinger's preference.  Then back up your current common-auth file, and replace it with the Gutsy one.  If it ends up breaking your system, you can just boot into into the root shell and delete the Gutsy version and replace it with the Intrepid one.

---

### Post by buster2209 on 2008-10-31
Just upgraded from 8.04 to 8.10

Thinkfinger isn't working

I have re-installed the software (via synaptics), enrolled my finger print successfully but there is no option at login reading 'password or swipe finger'

bug???

---

### Post by bigbrovar on 2008-10-31
I was expecting some things to break in ibex and when the finger print reader didnt work i wasnt too surprised.. i think we should be pro active about this and file a bug in launchpad or something .. after all Ubuntu is us

---

### Post by badrunner on 2008-10-31
The fingerprint reader actually works fine, its just X.org no longer processes the fake enter key signal properly, so you need to swipe finger then press enter.

You may also need to run the supplied script to renable pam support for thinkfinger as it was probably overwritten

---

### Post by shingalated on 2008-11-01
It seems like the swipe and then press enter only works about 30% of the time...

---

### Post by kalyp on 2008-11-03
there's a solution for the "enter" problem here: [http://www.eastwoodzhao.com/ubuntu-810-intrepid-ibex-thinkfinger-fingerprint-reader/](http://www.eastwoodzhao.com/ubuntu-810-intrepid-ibex-thinkfinger-fingerprint-reader/)
works fine for me... without the keyboard problems mentioned...

---

