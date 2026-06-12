---
title: "Cannot open links by clicking on them in Thunderbird"
date: 2011-12-26
forum: Desktop Environments
---

### Post by fmstasi on 2011-12-26
I recently switched to Oneiric Ocelot in its default installation after a couple of years with Kubuntu, and a few additional years using KDE on Debian, so there is a bunch of hidden directories in my home I am taking with me since, oh, at least six years, maybe more.

When I click on a link in a mail message, if firefox is not active, it is launched and regularly opens the link; however, if it is already running (as i usually the case), I get the well-known message "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

I renamed the .mozilla directory in my home directoy and created a new firefox profile, but nothing changed. Then I tried to follow the suggestions given [here]("http://hsmak.wordpress.com/2009/09/03/howto-force-thunderbird-to-open-links-in-firefox/"), but the mentioned config keys do not exist anymore, and creating them did nothing.

Does anybody else have this problem? Any idea I could try?

---

### Post by ageofsteam on 2012-07-24
I'm having this exact same problem.  Has anyone solved it yet? :(

It's bothering me so much to have to copy and paste links into the firefox address bar just to open them...

---

### Post by MikeMacDonagh on 2012-09-10
I had this problem too and eventually fixed it. The problem was the way my Unity launcher was invoking firefox with some extra command line parameters, just removing them from the "Exec" line in the firefox.desktop launcher fixed the problem - I wrote up the steps on my [blog]("http://mikemacd.wordpress.com/2012/09/10/cant-open-links-in-firefox-on-ubuntu-when-its-open-fixed/").

---

