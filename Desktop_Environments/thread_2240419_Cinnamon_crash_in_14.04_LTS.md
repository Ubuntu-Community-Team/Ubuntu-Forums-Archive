---
title: "Cinnamon crash in 14.04 LTS"
date: 2014-08-19
forum: Desktop Environments
---

### Post by cecilieaux on 2014-08-19
Ever since I downloaded and installed the Cinnamon DE (I hate Unity), I have been getting a message about an "internal error." I authorize sending the error and close the window and everything seems fine until next time I turn on the computer and log in.

I wish I knew where these error are stored because it has a plethora of information, but there seems to be no way to copy and paste from the window. 

The package that fails is cinnamon 2.2.13ubuntu1 [LP-PPA-lestcape-cinnamon]

The problem is titled "cinnamon crashed with SIGABRT in_lbc_message()" and there is a long list of XSessionErrors, most of them having to do with the theme file for an app having no name or file, which I take to mean it doesn't know about some items installed by Ubuntu since it is originally a Mint DE (it looks for Nemo, for example).

Anyone familiar with this? (Please don't argue that Cinnamon is a distro, which it isn't; its a desktop environment.)

TIA,
C

---

### Post by cecilieaux on 2014-08-19
Found more details in a lof file, as follows ...
> 
ERROR: apport (pid 2820) Tue Aug 19 22:44:33 2014: called for pid 2241, signal 6, core limit 0
ERROR: apport (pid 2820) Tue Aug 19 22:44:33 2014: executable: /usr/bin/cinnamon (command line "cinnamon --replace")
ERROR: apport (pid 2820) Tue Aug 19 22:44:33 2014: debug: session gdbus call: (true,)

ERROR: apport (pid 2820) Tue Aug 19 22:44:48 2014: wrote report /var/crash/_usr_bin_cinnamon.1000.crash

Does anyone get what happened?

---

### Post by The_Weaver on 2014-09-29
I get this problem as well.

---

