---
title: "Broken file??"
date: 2005-12-12
forum: Desktop Environments
---

### Post by interse on 2005-12-12
I know that GnuCash is not supported in the Ubuntu official repositories, or at least that is my understanding.  And, this question is not really about GnuCash.  I recently received a list of updates available for my system.  After downloading them, I had an error and received the message that a file was broken and that I should use the Broken Filter to find it.  Tried, could not get the Filter to work.  However, I did find that the program was GnuCash.

The 'error' message was as follows:
Preconfiguring packages ...
(Reading database ... 81418 files and directories currently installed.)
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have removed GnuCash and things are fine.  Question is HOW DOES ONE GO ABOUT FIXING A BROKEN FILE OR RESPONDING TO THE ABOVE MESSAGE?  I suspect that this will not be the last time I receive such a notice.  I can live w/o GnuCash, but would like to know how to proceed under a similar situation.

---

### Post by aysiu on 2005-12-12
You could ```
sudo apt-get -f install
```

---

### Post by TuxDaddy on 2005-12-20
I was looking around in to figure out how to fix the problem with the broken file.

Try this:

1. Open terminal
2. type "apt-get rmove libofx0c102" once completed then
3. type "apt-get install libofx2" once completed install GnuCash by:
4. "apt-get install gnucash"

Hope this helps!

---

