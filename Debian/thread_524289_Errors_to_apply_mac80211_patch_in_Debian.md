---
title: "Errors to apply mac80211 patch in Debian"
date: 2007-08-12
forum: Debian
---

### Post by fd9_ on 2007-08-12
I'm trying to apply the mac80211 patch in Debian, because I'm trying to get wifi working, and I got this after doing "sudo make patch_kernel":

```

Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
scripts/generate_modified: line 41: rsync: command not found
Applying patches and scripts from pending/.
scripts/generate_modified: line 87: rsync: command not found
 + Applying: pending/09-range-name-rate-but-no-channel.patch
        diff -urp origin/include/net/mac80211.h test/include/net/mac80211.h
patch: **** Can't change to directory post/ : No such file or directory
-----patch failure output-----

pending/09-range-name-rate-but-no-channel.patch failed. Terminating.
If patch or script failed, check pre/ and post/ for current stage.
make: *** [modified] Error 1


```

Then I tried doing it again (make patch_kernel) and the error was a little different:

```


Checking kernel compatibility in:
        /lib/modules/2.6.22-1-686/source//
grep: /lib/modules/2.6.22-1-686/source//drivers/base/core.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires device_rename compat
   - Requires ilog2 compat
Building compatibility version in 'compatible/' directory:
Copying compatible/ from modified/...done
scripts/generate_compatible: line 52: rsync: command not found
 + Running: ilog2.sh
        IEEE80211_STYPE_QOS_DATA's mask is 0x0080
scripts/generate_compatible: line 96: rsync: command not found
sed: can't read post//net/mac80211/ieee80211.c: No such file or directory
Failure running ilog2 compat script
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

```

Any ideas? I have no idea what this means.

---

### Post by benuski on 2007-08-15
If you're using kernel 2.6.22, which is in Sid, mac80211 is already built in.

---

### Post by fd9_ on 2007-08-15
I'm using Lenny, which I believe still has the 2.6.21 kernel. I tried downloading the pre-compiled kernel from the repositories, could this be the reason why I'm having problems?

What exactly is the difference between downloading the kernel from the repos and downloading it from kernel.org?

---

### Post by angryfirelord on 2007-08-16
kernel.org simply provides the source code to the kernel. You have to compile it in order to use it. The advantage of compiling is that you can tweak it, but compiling can take hours.

Debian's kernels, OTOH, are pre-built and in binary form. All you have to do is point your sources to unstable, get the updated kernel, and then put your sources.list back to lenny.

---

