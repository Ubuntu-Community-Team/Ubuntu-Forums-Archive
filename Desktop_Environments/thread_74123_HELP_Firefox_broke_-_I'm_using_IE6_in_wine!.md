---
title: "HELP Firefox broke - I'm using IE6 in wine!"
date: 2005-10-10
forum: Desktop Environments
---

### Post by linuxNewb on 2005-10-10
OMG I'm having to use my IE6/wine install (intended for compatability testing only) because during a synaptic upgrade I got the following error. Firefox does not open anymore. Please help!!!

...
Preconfiguring packages ...
(Reading database ... 71736 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Emerzen on 2005-10-10
Have you tried uninstalling firefox ('completely uninstall') and reinstalling via synaptic?  I would do that 1st.  If that fails, I'd also try:

sudo dpkg-reconfigure firefox

and see if  that fixes it.

---

### Post by linuxNewb on 2005-10-10
I did what you said. When I clicked the firefox icon, nothing happened. Then I found that the process 'firefox-bin' was running, so I killed it. Then I clicked the firefox icon again, and everything is working properly!!! Thank you for your quick (and helpful) response.

---

### Post by Emerzen on 2005-10-11
Glad to help!

---

### Post by g33k on 2005-10-11
I'm having the same issues and am writing this from my XP box.  I think it has something to do with the backports repo.  My thinking is that some package affiliated with firefox was retrieved from an unoffical repo and now the official updates have broken firefox.

I'm working on fixing my box now, but I just installed dillo as an interim solution (and a good backup graphical web browser).

apt-get install dillo

---

### Post by barry_s on 2005-10-11
I don't have a solution, but as a recent convert from XP I thought it was worth mentioning that I had a similar probelm with Firefox on that platform. It didn't appear to start, but when I checked Task Manager it showed firefox as running.  Once I killed that, it started fine. The probelm happened regularly until Firefox 1.07 came along. 

Barry

---

### Post by Emerzen on 2005-10-11
g33k,

Are you running Hoary or Breezy?  If Breezy, I would remove the (Hoary) backports and do a complete reinstall as above.  If that fails, try the command I listed above.  Hoary backports shouldn't break Breezy, but you should be sure.

---

