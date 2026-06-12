---
title: "Rekonq headache"
date: 2011-10-15
forum: Desktop Environments
---

### Post by linuxcanuck on 2011-10-15
I am using Kubuntu 11.10 64-bit. I have several browsers installed. I use them for different things. Rekonq after installing the Kubuntu 11.10 (clean install) started acting up. This problem happens only in Rekonq and only with anything Google.

When I go to any Google page it switches language to Catalan which I do not read or use. I go to the account settings (and search settings) and change it to English and go back to the search and it is in English. If I close the tab or open an new one it is again in Catalan. I have repeated this several times. If just does not want to change. Rekonq has no language pack in the repositories.

My settings in KDE are Canadian English. Rekonq should use that. My home page for Rekonq is Google.ca (for Canada not Catalan). I changed it to Google.com but it is still in Catalan.

I use Google extensively and my language settings are all in English Canada on all acounts. I have not had this problem with Rekonq before and it shows up in no other browser.

I am scratching my head on this one. I have searched the web and the forum and this seems to be unique to me. I want to use Rekonq but will switch to Chrome or something else if it persists.

Roy

---

### Post by JoeNotCharles on 2011-10-16
I'm having the same issue.  My language is set to en_CA.UTF-8 - that's "ENglish CAnadian".  Something somewhere must be interpreting the CA as the language code "Catalan" rather than the country code "English".

---

### Post by JoeNotCharles on 2011-10-16
I just found that this is filed in the bug tracker: [https://bugs.kde.org/show_bug.cgi?id=283927](https://bugs.kde.org/show_bug.cgi?id=283927)

Apparently it was fixed on Oct 13 and the fix should be in the 0.8 stable release "in a few days".

---

### Post by linuxcanuck on 2011-10-17
I fixed it in a round about way. I deleted the Favourites for Google which always seemed to bring Google up in Catalan no matter what I did. Changed my settings to Restore With last open pages and not home page. Went to Google.ca and exited and checked my settings were indeed English. It came up in English when I reloaded Rekonq. Added Google.ca to the Favourites and changed the setting back to Home Page and it works in English every time.

This could be coincidental with a fix from the KDE folks Because I upgrade several times a day, but it was nice to see it come up English, not that I have anything against Catalan. :)

Thanks,
Roy

---

