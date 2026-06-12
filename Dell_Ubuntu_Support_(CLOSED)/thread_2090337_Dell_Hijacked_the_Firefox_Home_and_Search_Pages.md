---
title: "Dell Hijacked the Firefox Home and Search Pages"
date: 2012-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sunrise611 on 2012-12-01
I recently received a Dell laptop preinstalled with Ubuntu 10.11.

I cannot change the settings that Dell set for the Firefox Home and Search pages that default to Yahoo with a link crediting Dell.  

The home page points to [www.yahoo.com/?fr=dell-in-home](www.yahoo.com/?fr=dell-in-home) and the default search engine is Yahoo.

First I changed the Home Page preferences in Firefox but that did not stick.

Then I changed settings in about:config and none of those changes stuck either.  The settings that I changed were:

browser.startup.homepage=______
browser.search.default.rename = ______
browser.startup.homepage-override.buildID (reset)
browser.startup.homepage-override.mstone (reset)

There might have been one or two others that I tried to change.

However, I am still forced to use Yahoo for my home page and search engine.  

Dell Support was unable to help me!  They simply claim that they do not know why my changes are not sticking and recommended that I uninstall and reinstall Firefox to see if that works.

I am a newbie to Ubuntu and do not know how to easily uninstall and reinstall Firefox and should not have to do that.

I think there is a way to change the settings in a Firefox javascript but am not sure if that will work or how to go about that either.

---

### Post by SeijiSensei on 2012-12-01
Close firefox, then go to your home directory, enable the display of "hidden files," and locate the folder called .mozilla.  Delete it.  Now open Firefox again.  It should create a new configuration for you from scratch.  Do you still have the same problem?

---

### Post by gbrainin on 2012-12-02
Under Tools->Add Ons there is a section for Extensions.  One of these is likely to be the culprit, and you can turn it off.

---

### Post by Sunrise611 on 2012-12-03
Thanks, Gbrainin!  That did the trick!

I found the offending extension that was added to the extensions in Firefox and disabled it.  

Then I was able to set my Preferences for the Home Page.  

I also went back into about:config and changed the default search engine from Yahoo to Google in browser.search.default (name and URL).  

Now it's working perfectly and it was an easy solution!  

Boo on Dell for installing the extension and the Support Tech for not knowing that they installed it!

P.S.  For those that are unfamiliar with Firefox extensions, you can find them in your Firefox menu under Tools - Addons - Extensions.

The offending extension is one that is created by Canonical.  I can't recall the exact name of it but it should be easy to spot and disable.

---

### Post by gbrainin on 2012-12-04
Glad that helped!

---

### Post by pratiwir on 2013-03-25
It seems that Dell is adding a software application on new Ubuntu laptops. It can be removed with this command
# sudo apt-get remove yahoo-browser-defaults
See Jeff's post near the end of [https://answers.launchpad.net/ubuntu-certification/+question/208660](https://answers.launchpad.net/ubuntu-certification/+question/208660)
It took several days to find this and I would classify the application as malware because there is no information given to the owner about what they have done. However, if you use firefox, like yahoo as your home page, and don't want to be able to re-launch tabs from the last session, then it might not bother you.

---

