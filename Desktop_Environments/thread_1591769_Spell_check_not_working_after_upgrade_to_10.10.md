---
title: "Spell check not working after upgrade to 10.10"
date: 2010-10-09
forum: Desktop Environments
---

### Post by james_xxx on 2010-10-09
Since upgrading to Maverick yesterday afternoon, I have noticed that spell-checking does not seem to be working in some programs.

I am writing this post in Chromium-browser, and spell-check seems to be working. It does not seem to work, however, in Firefox or Thunderbird.

Any suggestions?

---

### Post by sendblink23 on 2010-10-09
> **james_xxx said:**
> Since upgrading to Maverick yesterday afternoon, I have noticed that spell-checking does not seem to be working in some programs.

I am writing this post in Chromium-browser, and spell-check seems to be working. It does not seem to work, however, in Firefox or Thunderbird.

Any suggestions?

I actually just noticed it as well on my 10.10 RC fresh install(all latest updates) on FF its not working the spell-check, but on Chromium it works just fine

---

### Post by james_xxx on 2010-10-10
I am glad to hear that I am not the only one.

If there are others with this problem, maybe we'll some sort of fix for it soon.

---

### Post by james_xxx on 2010-10-11
bump

---

### Post by james_xxx on 2010-10-11
OK, it appears that spell-checking is indeed working in Thunderbird. The problem was just that, after upgrading to Maverick, Thunderbird was spell-checking for another language. 

After setting the spell-checker to American English, things were back to functioning as they should.

Sadly though, this problem persists in Firefox. I have checked Kubuntu's spell-check settings and the settings in Firefox, but see no problem with how things are currently configured.

Any suggestions would be welcome.

---

### Post by jmdlcar on 2010-10-11
I'm using Ubuntu 10.10 and spell check did not work so I found out I had to turn it on now it works.

---

### Post by james_xxx on 2010-10-11
May I ask how you turned it on?

I now have spell-check working in the majority of applications. It seems to be solely Firefox that is now having this problem.

It does appear that spell-check is trying to work in FF, it's just that every word gets marked as having been misspelled. It is as if it is trying to spell-check for another language (as had been the case for me in Thunderbird).

At this point, I may log-in to a Gnome session, and check whether or not this might be a Gnome setting bleeding over into KDE.

---

### Post by james_xxx on 2010-10-11
OK, spell-checking is now working in FF.

Firstly, when I logged-in to a Gnome session, and navigated to the settings for languages/spell-check, etc., a dialog box popped up telling me that not all of my language support packages were fully installed, and asking whether or not I wanted to install them. I selected 'yes', and it downloaded and installed several packages.

I then logged back in to KDE, but spell-check still did not work correctly in FF. 

Finally, I noticed that if I right-clicked while in a dialog box (like this one), it showed some options for spell-checking. Again, FF was not set to use English. No idea why this would have changed, but after selecting American English there, all seems to be well.

---

### Post by bingotailspin on 2011-02-21
I had this issue because the English dictionary was not installed from myspell.  I used the software center to search for and install the myspell-en-us package and that fixed it for me.

Previously, the Thunderbird > Edit > Preferences > Composition > Spelling > Language tab had no possible values.  Now it shows English/United States.  Not sure how that was missed.

Running 10.04 64bit fresh install on this machine.

---

