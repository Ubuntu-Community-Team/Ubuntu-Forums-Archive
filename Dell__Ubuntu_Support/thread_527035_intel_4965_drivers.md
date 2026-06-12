---
title: "intel 4965 drivers"
date: 2007-08-16
forum: Dell  Ubuntu Support
---

### Post by Nunslaughter on 2007-08-16
i just saw that intel came up with the drivers for the wireless 4965 card....now trying the follow the install instructions, but i can't get far...

i first have to compile mac802.11, and there it goes wrong already:

```
timo@timo-laptop:~/mac80211-9.0.4$ make

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Fout 1
timo@timo-laptop:~/mac80211-9.0.4$ make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Fout 1
 
```

any help on this?

---

### Post by strabes on 2007-08-16
Have you installed the build-essential package?

---

### Post by Nunslaughter on 2007-08-16
yes, that package is installed...

---

### Post by tonyric on 2007-08-16
check your environment variables. make isn't liking them. 

`echo $SHELL` and if it doesn't return as "/bin/bash" then run `bash` and then `export BASH=/bin/bash`

then try to rerun make

Tony

---

### Post by Nunslaughter on 2007-08-17
echo $SHELL returns /bin/bash

so that's okay i think then...

---

### Post by Nunslaughter on 2007-08-17
i downloaded an older version of mac802.11 to try but i get the same error (a bit more)

```
 timo@timo-laptop:~/mac80211-8.0.2$ make

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/09-range-name-rate-but-no-channel.patch
        diff -urp origin/include/net/mac80211.h test/include/net/mac80211.h
 + Applying: pending/10-txpower.patch
        Fix user specified TXPOWER from being overridden by stack.
 + Applying: pending/11-iwlist-channel.patch
        From: Hong Liu <hong.liu@intel.com>
 + Applying: pending/30-fixup-giwrate.patch
        Fix SIOGIWRATE so it actually returns the most recent rate *or* highest
 + Applying: pending/99-mainline-2.6.23-fix.patch
        Add three patches from upstream 2.6.22-rc7 GIT.
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Fout 1

```

---

### Post by bettasbetta on 2008-02-27
Hi everybody,

I have the same exact problem! I too have explored all the possibilities that you have suggested so far (btw, thank you), and none of them seems to be the problem. I'm stuck. :confused:

What can we do? Any other idea? Thanks again for your time

---

### Post by Nunslaughter on 2008-02-28
I updated my gutsy kernel to the hardy one. And the card works without a problem now!

Check this post for info: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

