---
title: "installing asterisk on ubuntu 8.04 server"
date: 2009-01-09
forum: General Help
---

### Post by hosdes on 2009-01-09
I am using ubuntu 8.04 lts server.  I have installed asterisk by repos, 1.4.17.  I am reading this [http://colt45.chemlab.org/?p=55](http://colt45.chemlab.org/?p=55) and it is recommending to install asterisk by svn instead of repos.

Has anyone had any success with installing asterisk and how?  Also any luck with installing freepbx 2.5.1?

---

### Post by PeterNSteinmetz on 2009-01-19
Also been working on this. It seems like this should really be simpler than it apparently is, since there are packages for most of the evidently required parts. It also seems very desirable to get this working for hardy server, since this is the latest LTS version.

I have the packages asterisk (1:1.4.17~dfsg-2ubuntu1), asterisk-config (1:1.4.17~dfsg-2ubuntu1), asterisk-sounds-main (1:1.4.17~dfsg-2ubuntu1), and asterisk-sounds-extra (1.2.1-1) installed using apt-get install.

Following the instructions for configuration in the Practical Asterisk 1.4 (unstable) book at
[http://www.the-asterisk-book.com/unstable/bk01-toc.html](http://www.the-asterisk-book.com/unstable/bk01-toc.html),

I am able to get voice calls using sip between two softphones. However, the voicemail doesn't play any sounds. I also can't get Playback or Playtones to work on an extension. 

It is unclear to me at this point if this is due to the sounds having been placed in /usr/share/asterisk/sounds or not. There is also the issue of the ownership and group of a number of files as noted at [http://colt45.chemlab.org/?p=55](http://colt45.chemlab.org/?p=55).

It would be very nice to get this figured out and get the wiki page AsteriskOnUbuntu up to date.

---

### Post by PeterNSteinmetz on 2009-03-16
Have now worked out a script to do the install automatically on a base install of Hardy (8.04) server.

Available on the wiki now at [http://wiki.ubuntu.com/AsteriskScriptOnHardy](http://wiki.ubuntu.com/AsteriskScriptOnHardy).

---

