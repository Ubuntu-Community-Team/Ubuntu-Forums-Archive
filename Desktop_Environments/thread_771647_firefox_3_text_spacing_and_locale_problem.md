---
title: "firefox 3 text spacing and locale problem"
date: 2008-04-27
forum: Desktop Environments
---

### Post by aikishugyo on 2008-04-27
Hi all, I'm using Hardy on AMD64, and for several months now Firefox has been using a weird text spacing: each space character is about the size of 3 or 4 individual characters. This problem only appears in firefox 3, and at the moment I don't have access to firefox 2 on the machine anymore.

I found some threads on this problem, and tried the solution: removing all preferences. This did not work for me. I also purged firefox and mozilla without effect, manually deleting the .mozilla and usr/share/mozilla and /usr/share/firefox directories.

Can anyone shed light on this issue?

I also have some locale issues. Whenever I try to upgrade a package, I get the following:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_PAPER = "en_GB.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

However, I seem to have all locale packages installed, judging by the results of "aptitude search locale". (I manually set the LC__PAPER in .bashrc so that I can get evince to default to A4 paper.)

Best regards,
Gernot

---

