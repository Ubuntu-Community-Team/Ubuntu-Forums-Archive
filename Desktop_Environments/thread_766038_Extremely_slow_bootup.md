---
title: "Extremely slow bootup"
date: 2008-04-24
forum: Desktop Environments
---

### Post by aerojad on 2008-04-24
Hello there.  I just started fresh with Kubuntu 8.04 today and I am noticing that Kubuntu is hanging while loading for an awful long time - upwards of two minutes - for a system that booted Ubuntu Gusty (and others before) in half a minute maybe.  How can I figure out what is wrong?

Oh, and I've done some searching and noticed people talking about screen sizes on boot and looking for them, already checked and that file was filled out properly so that's probably not the issue.

Other than that, June will be 2 years of *Ubuntu for me, love you guys!

---

### Post by angry_johnnie on 2008-04-25
Have you tried disabling usplash during boot, to see what the error is, or where exactly it is being delayed?

I had a similar problem once, with Feisty, and was able to fix it doing [this]("http://ubuntuforums.org/showthread.php?t=470730").

Only I didn't delete anything (chicken :-)).

I just commented out the lines I didn't want.

Hope that helps.

---

### Post by aerojad on 2008-04-25
Alright, I disabled usplash and here is what I am getting:

sd 8:0:0:0:0: [sdc] Assuming drive cache: write through
hub 1-0:1.0: Cannot enable port 3. Maybe the USB cable is bad?

That first error repeats four times, the first two starting out with 7's

That second error eventually ends with a red [FAIL] indicator, and then the boot process completes - but those are the two places it is hanging up.

And oddly enough, on a re-reboot, the USB error didn't occur, so maybe it's intermittent?  The first error happened both times though.

---

