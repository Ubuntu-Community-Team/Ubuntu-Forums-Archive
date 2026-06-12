---
title: "acrobat reader temporary hang / freeze on startup"
date: 2009-02-16
forum: General Help
---

### Post by alexyz on 2009-02-16
Adobe Reader 8.1.3 from mediabuntu repository.

When executing acroread, the whole system freezes for 5-10 seconds.  After running once, it usually starts up normally for a while but sometimes the freeze reappears.

Finally found the answer here

[http://www.adobeforums.com/webx/.59b4dde4](http://www.adobeforums.com/webx/.59b4dde4)

To fix, edit /usr/bin/acroread .  That's a symlink to target /usr/lib/Adobe/Reader8/bin/acroread .  Comment out where the environment variable ACRO_ENABLE_FONT_CONFIG is set, as follows (for me was around line 400):

# Enable this if you want Adobe Reader to cache Font-config fonts 
# ACRO_ENABLE_FONT_CONFIG=1
# export ACRO_ENABLE_FONT_CONFIG

I didn't entirely understand the bug report and there may be a better way to do this, but no more hang.  This was driving me crazy for months, couldn't find anything on the forums.

---

### Post by Tobi-fp on 2009-02-16
You could always have installed another reader, there are many open source alternatives

---

### Post by crpenaherrera on 2011-08-05
Hi Alexyz,

thanks for your post. I was looking for this fix for so long, I'm glad I found it now. Like it or not, Adobe is a good platform with some pros in front of other open source alternatives. Anyway, it is a shame that neither them and the open source alternatives are always perfect. We got to look for work arounds almost always to keep our ubuntu working flawlessly, and that is something Canonical should be working hard in change it.

Anyway, in my case I'm in Ubunut 11.04 updated from 10.04 (did nothave time to install everything again), and in my case the fix was to edit the same file found in /opt/Adobe/Reader9/bin/acroread ; by deleting the # where the environment variable ACRO_DISABLE_FONT_CONFIG is set, as follows (for me was around line 480):

# Enable this if you donot want Adobe Reader to cache Font-config fonts 
  ACRO_DISABLE_FONT_CONFIG=1
  export ACRO_DISABLE_FONT_CONFIG.

Hope this works to anybody else having this problem. 

Cheers to everyone

CP

---

