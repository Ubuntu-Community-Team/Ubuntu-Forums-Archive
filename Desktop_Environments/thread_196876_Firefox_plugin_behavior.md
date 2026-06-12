---
title: "Firefox plugin behavior"
date: 2006-06-14
forum: Desktop Environments
---

### Post by GreenfrogCT on 2006-06-14
Here's a wierd one I can't quite figure out.  Dapper 6.06 with all updates, Firefox  1.5.0.4 latest build.   My Firefox installation and plugins work just fine, except for an occasional problem with pages that include multimedia.  

Example:   The weather page of my local NBC affiliate  [ http://www.nbc30.com/weather ]("http://www.nbc30.com/weather") always gives me a couple of error dialogs relating to Totem not being able to display .gif images - and I can't find where a .gif image is associaed with Totem.

On that page I get:

"Totem could not play http://images.ibsys.com/sh/images.spacer.gif"  and "Totem could not play http://www.nbcweatherplus.com/wxp/images/MediaPlayerControl/TheEndVideo.gif"

There are a few other places where I get similar errors.  Not sure if they are using Microsoft APIs that are causing this, but running Firefox on my Windows partition I don't have a problem.

Any ideas?

:mrgreen:  Ribbit

---

### Post by yager on 2006-06-14
I opened your link and had no problems.  I used Automatix to put in all of the codecs that do not ship with Ubuntu.  I know that .GIF has a colorful history around patents and who is allowed to use the format or not so that may be one of those formats Ubuntu is not allowed to ship with due to legal issues.  Have you used Automatix or maybe EasyUbuntu to fill in the missing pieces to Ubuntu?

---

### Post by GreenfrogCT on 2006-06-15
:cool: Thanks for the tip on Automatix.  That did the trick -- I thought I had all the required codecs loaded, but I was one wrong frog. ;) 

Anyway Automatix is worth a look for those who would like to add some things into their Ubuntu installation that are not part of the default install.  Check out

[http://www.ubuntuforums.org/showthread.php?t=177646]("http://www.ubuntuforums.org/showthread.php?t=177646")

Thanks again!

:mrgreen:  Ribbitt

---

