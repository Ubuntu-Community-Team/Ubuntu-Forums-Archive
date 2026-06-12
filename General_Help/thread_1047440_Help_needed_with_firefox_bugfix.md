---
title: "Help needed with firefox bugfix"
date: 2009-01-22
forum: General Help
---

### Post by sancho panza on 2009-01-22
Firefox currently suffers from extremely poor page-zoom as discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=841739").

This is a bug and is being [worked upon here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908"). The developer working on this bug needs some input from nvidia/ati graphics card users.
All users interested in helping (preferably on intrepid), please run the test described in [this comment]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908/comments/33") and post the output, along with which version of ubuntu you are using and you display driver (output of the "lspci | grep Display" command or "lspci" command if the first doesnt work) and post your response under that bug-report.

The test is completely harmless, it just executes a few Render operations and dumps the results to .png files that can be safely deleted afterwards.

Thanks,

---

### Post by sancho panza on 2009-01-22
bump.

---

### Post by mgol on 2009-01-22
I posted my results in the bug report.

---

### Post by marty4k on 2009-03-03
The firefox zoom bug still exists in Jaunty Alpha 5 with the proprietry NVIDIA driver (180.35) and is driving me nuts.

Output of repeat-test_i686 now pasted into the bug report.

Regards,

Martin

---

