---
title: "firefox crashes with segmentation fault when not root"
date: 2005-12-18
forum: General Help
---

### Post by RobertLos on 2005-12-18
Little problem,

when I start firefox either from the menu or from the command prompt it crashes with a segmentation fault in most (but not all) websites. It seems to be java(script) related. Firefox does not crash when invokes using

% sudo -H firefox &

but then the ights are different.

Any suggestions. How can I debug or get more information?

I run Breezy Badger. It used to work OK but went wrong after an update.

---

### Post by Kevinator on 2005-12-18
You can pobably fix it by creating a new profile.

mv ~/.mozilla ~/.mozilla_backup

Then run Firefox. You might want to copy some things (such as bookmarks) from the old profile to the new.

---

### Post by RobertLos on 2005-12-18
Dear Kevinator,

thanks. Tried that, but it did not work.

Robert

---

### Post by alien8 on 2005-12-28
[QUOTE=RobertLos]Little problem,

when I start firefox either from the menu or from the command prompt it crashes with a segmentation fault in most (but not all) websites. It seems to be java(script) related. Firefox does not crash when invokes using

% sudo -H firefox &

but then the ights are different.

Any suggestions. How can I debug or get more information?

I run Breezy Badger. It used to work OK but went wrong after an update.[/QUOTE]

Hi Robert,

here's an idea:

start firefox as your normal user but call it using:

strace firefox -safe-mode

in my case this showed a whole heap of output ending with...

open("/usr/local/share/fonts/ttf/msfonts/tahoma.ttf", O_RDONLY) = -1 EACCES (Permission denied)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---

and true enough - tahoma.ttf was chmod'd to 700. - sudo'd you'd not have this problem.

a quick sudo +chmod later and all worked fine again.

HTH 

//alien

---

