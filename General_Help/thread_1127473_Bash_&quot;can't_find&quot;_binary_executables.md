---
title: "Bash &quot;can't find&quot; binary executables"
date: 2009-04-16
forum: General Help
---

### Post by EQvan on 2009-04-16
Hi...

I am working on a custom hand-held device which runs a variant of Ubuntu Linux, 2.6.18. I have a set of 4 binary files (for oprofile) which have been known to run in this environment, but when I install them to /usr/bin, I can't run them: I get this message;
[FONT="Courier New"][INDENT]root@ldogberry:/usr/bin# ./ophelp
-sh: ./ophelp: not found[/INDENT][/FONT]
This happens when I specify the full path, when I run from the /usr/bin directory -- it happens no matter what. Bash even does command-line completion on the file -- and then turns around and instantly claims the file is not found.

I've checked all of the permissions on the files -- they appear to the the same as the other files in the /usr/bin directory, which work correctly:
[INDENT][FONT="Courier New"]root@dogberry:/usr/bin# ls -al opreport ophelp oprofiled objdump
-rwxr-xr-x 1 root root 550216 Sep 10 2008 objdump
-rwxr-xr-x 1 root root 27008 Jan 1 06:42 ophelp
-rwxr-xr-x 1 root root 591308 Jan 1 06:30 opreport
-rwxr-xr-x 1 root root 278321 Jan 1 06:30 oprofiled[/FONT][/INDENT]
Does anyone have any idea what might be causing this problem?

---

### Post by 505 on 2009-04-16
Maybe you have a version that was compiled for another platform. I believe that would also result in that message. Check the output of 'file ophelp' to see what kind of file it is (e.g. executable for what platform).

---

### Post by EQvan on 2009-04-16
Hi... thanks for the suggestion.  I built these binary images myself, using the same cross-compiler I usually use for development on this platform.  Just for luck, I went ahead and did as you suggested, and sure enough, the binary looks OK -- it's an ELF 32-bit executable for the ARM, which is right.

In fact I generated these binaries about 6 months ago, and at that time, running on a platform with the same kernel version and root filesystem, and it all worked.  I'm very sure I have all the required dependencies in place (and in any case, I shouldn't see this kind of an error message for a shared library).

It appears to me that there's some kind of permission issue... something that causes the shell to believe that the binary file is missing...

(OH, and I fibbed about the shell!  I'm running "ash", not "bash"!  Ash is generally similar, but smaller, and omits a few features (like arrays, for example).

---

