---
title: "Enigmail Package Broken by Update"
date: 2005-12-15
forum: Desktop Environments
---

### Post by gilgongo on 2005-12-15
Shouldn't think many people are running Thunderbird with Enigmail so I'm not going to put this on the Wiki, but should I report a bug?

I installed the Enigmail package for Thunderbird with Synaptic. If you check for a new version using Thunderbird's internal extensions update function, the new version (0.93.0) breaks the installation ("Enigmime service not available").

So: if you're running Enigmail, don't update it!

I had to fix it by uninstalling first the Synaptic package, then the extension from within Thunderbird, then re-installing the package again. Prefs are retained though so it's no biggie.

---

### Post by kwalker on 2005-12-21
Using kubuntu and Adept, I ran into the same issue.  So far I haven't been able to get it to work reliably again.  I am using Thunderbird 1.0.7 

When I go to [http://enigmail.mozdev.org/download.html](http://enigmail.mozdev.org/download.html) it looks to me like version v0.93-tb10-linux.xpi is what I ought to be using.  I have tried the tb10 version, the tb15 version and the tb version.  All produce the same error.  I have also tried installing the version that Adept installs from the ubuntu repositories.  I get the same error.

So, in answer to the question you have posed, it does seem to me to be a bug.  But then again, it could easily just be me, it usually is.

If you have a solution please let me know.

---

### Post by kwalker on 2005-12-21
I have had some confirmation on the Enigmail list that someone there has found that the version used in the Ubuntu repositories of both TB and enigmail no longer work together and the ubuntu version of TB does not work with the Enigmail package from the mozdev site.  That matches my experience.

The suggestion is that I should ditch both and just install TB and enigmail from the mozdev site and that will work.

Should I?  What do I lose by doing that? Will it work?

Ken

---

### Post by rosslaird on 2005-12-21
[QUOTE=kwalker]The suggestion is that I should ditch both and just install TB and enigmail from the mozdev site and that will work.
Should I?  What do I lose by doing that? Will it work?
[/QUOTE]

Well, I don't know about enigmail, but I have just installed TB 1.5 by going directly to the moz site. If you know how to launch TB from a downloaded directory, the only thing you lose is your profile (although, I'm on IMAP, and if you use POP, maybe you lose your mail as well...).

Anyway, the new TB is quite nice: in-line spell checking works very well, and there are lots of new bells and whistles.

Ross

---

### Post by kwalker on 2005-12-25
On a mailing list, I got this suggestion:

>>You might run into problems because you install a)
>>mozilla-thunderbird-enigmail package together with b) enigmail
>>extension through extension mnager. First remove the extension
>>installed manually, then use mozilla-thunderbird-enigmail (maybe
>>reinstall the package one more time).

Based on that, I did the following:

First I went to Tools|Extensions and uninstalled the enigmail extension
and restarted TBird.  That got rid of it.

Then I downloaded the Ubuntu version from the ubuntu site and installed
it this way:

sudo dpkg -i mozilla-thunderbird-enigmail_0.92.1-0ubuntu05.10_i386.deb


When I restarted TBird, it noticed and got me to restart it again.

The menu showed up with the old Enigmail dropdown rather than the new
OpenPGP dropdown.

When I tried to open messages that I have which are encrypted, it gave
me the same error message mentioned earlier as did Enigmail|Tools|About.

I went to the extension manager and asked it to update the extension and
it did, telling me it was getting it from the mozdev site.  That seemed
to work and now I am able to decryt messages and the title bar showing
whether keys are valid again seems to be working.  I am not confident of
this for a couple of reasons.  I got this far once before and it stopped
working but also because when I go to About OpenPGP I get

Running Enigmail version 0.93.0.0 (20051006)
Warning: Incompatible Enigmime version 0.92.1.0

So, I will see how it goes and it is at least working, but I have my
doubts.  Maybe I am just a pessimist!

Have a Cool Yule all,

---

### Post by kwalker on 2005-12-25
Well, that didn't last long.  After restarting the program, no more enigmail.  The only solution left seems to be to change distros.  Is there another solution?

---

### Post by three_sixteen on 2006-01-15
[QUOTE=kwalker]Well, that didn't last long.  After restarting the program, no more enigmail.  The only solution left seems to be to change distros.  Is there another solution?[/QUOTE]

I'm bumping this in hopes of finding someone whos been able to fix this problem.

---

### Post by nekr0z on 2006-03-20
Well, don't download Enigmail from mozilla.com, they have Windows version there. Uninstall Enigmail and download one from [http://enigmail.mozdev.org/download.html](http://enigmail.mozdev.org/download.html) instead.

At least this worked for me.

---

### Post by freek_zero on 2007-08-24
After reading everything google found on this issue, I finally discovered my problem was as described above: I had one version installed via apt, and another (with the same version # mind u) via the extension manager. i deleted both, then reinstalled mozilla-thunderbird-enigmail via apt, and everything was fine. note that i was using the version of thunderbird selected by apt also, so an exact version match is obviously important.

---

