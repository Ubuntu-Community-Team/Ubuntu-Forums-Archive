---
title: "compiz/emerald don't load propper"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by joetaxpayer on 2007-09-28
I can't seem to find anyone having a similar problem, so I started this new thread.  I tried to install ElmonGW's CF update script and ran into a host of problems I couldn't fix.  So I located all the files on my computer with the words compiz, emerald, or ccsm and removed them with rm -r.  I then used the gusty repos to install compiz, compiz-config-settings manager, and emerald (along with all the dependencies it automatically marked).  

Now when I restartX, emerald isn't loaded and compiz doesn't function.  "compiz --replace -c emerald &" makes the window boarders disappear and compiz doesn't work.  I noticed that when I disable my compiz/emerald startup script, the regular gtk themes will work, and compiz loads, but none of the settings work.  The weird part is now, if I select restore to defaults in compiz and restartX, emerald and compiz load automatically with compiz in default settings (startup script still disabled).  I can then change any setting and they will work for the session, but I have to restore compiz to defaults before I logout or else everything is messed up again when I login.

I'm thinking maybe I deleted a file that would normally tell X how to load compiz, but mostly I'm clueless.  I'm not even sure how to troubleshoot this problem.  Any help is appreciated.

BTW running gusty 64.  Thanks.

---

### Post by carnagex420x on 2007-09-28
i am having the same problem with my 32bit version on my dell 1420, i have the newest nvidia driver installed as well, i am hoping this will be fixed with an update soon,but i stil have sum effects...remember gutsys still just a BETA. its still a big step up from Tribe 5.

---

### Post by joetaxpayer on 2007-09-28
Yeah, I thought that maybe the problem was a result of my fooling around with compiz, but if your having the same problem, I guess it is probably gutsy.

---

