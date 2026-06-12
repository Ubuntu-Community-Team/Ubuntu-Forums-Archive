---
title: "Strange Compiz bug on Gutsy"
date: 2008-04-27
forum: Desktop Effects &amp; Customization
---

### Post by Fixman on 2008-04-27
Since yesterday, only some desktop effects worked (not all). If I go to appareance, it tells me advanced desktop effects are installde and, if I go to ccsm, I can tick some of them, but they won't activate. If I close and re open ccsm, they are not ticked. Any suggestion?

---

### Post by Fixman on 2008-04-27
Halp!

---

### Post by acelin on 2008-04-27
Why isn't this in the main support categories?

---

### Post by p_quarles on 2008-04-27
Moved to Desktop Effects & Customization. 

1) Please select an appropriate forum area for your question.
2) Don't bump a thread within 24 hours of initially posting it.

---

### Post by vikasvishnu on 2008-04-30
> **Fixman said:**
> Since yesterday, only some desktop effects worked (not all). If I go to appareance, it tells me advanced desktop effects are installde and, if I go to ccsm, I can tick some of them, but they won't activate. If I close and re open ccsm, they are not ticked. Any suggestion?

hmm.. looks like your compiz profile is messed up, friend! try removing your user settings for compiz.

Open up a console, make sure you are in your Home directory and give the below commands:

> rm -rf .compiz  # if you are using 7.10 or previous versions
rm -rf .config/.compiz  # if you are using the new Hardy Heron

Logout and login to your account. Start Compiz. This should automatically create a new compiz config and should solve your issue.. 

-:Vikas:-

---

