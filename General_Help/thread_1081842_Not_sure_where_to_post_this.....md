---
title: "Not sure where to post this...."
date: 2009-02-27
forum: General Help
---

### Post by EvoIX_MR2006 on 2009-02-27
I am having an interesting issue with Apache2 and Ubuntu.

I have a test file that is on Ubuntu 8.10 JeOS on VMWare.  Server speeds are generally very good, with other servers on the ESX host functioning great.  When I try accessing our site or downloading the test file via HTTP; it's extremely slow.

When I download the test file, or any other files for that matter, using SSL configured VSFTPD; the speeds are great -- 1.7-2.0 MB/s.

This is where it gets interesting.  If, after I download the file(s) via VSFTPD, and then immediatley go to our website, the files are quick again -- back to 1.7-2.0 MB/s.  This remains the case for another 15-20 minutes before going back down to 2-300 bytes/s.

Any help is greatly appreciated.

Thanks!

---

### Post by EvoIX_MR2006 on 2009-02-27
21 views and nothing?  :(

That's what I figured...wierdest problem I've ever seen.

---

### Post by kmac on 2009-02-27
If you have a personal ISP, check with them. Some ISPs do not allow personal web servers to be set up, and they may be set up to restrict traffic when they notice funny stuff going on through port 80. I'm the last one to talk to about networking in the least, but I did get a screamfest from my ISP when they found out I had a personal web server.

---

