---
title: "Setting xterm*color0 affects both ANSI black and BLACK"
date: 2009-03-28
forum: General Help
---

### Post by Red Long Johns on 2009-03-28
Using kubuntu 8.04, I'm trying to remap ANSI intense BLACK to orange in xterm. Unfortunately, I know of no other way to change how these colours are displayed than setting an xterm*color<number>.
Setting xterm*color0 affects both black (<esc>[30m) and BLACK (<esc>[90m) while setting xterm*color8 affects only BG BLACK (<esc>[100m).

I assume this odd behaviour is set in some default config file, but I have no idea which one it might be. I hoped that running "sudo grep -ri [[]90m *" in /etc and /sys would help, but the former only gave a "grep: nologin: No such file or directory" error and the latter thousands of warnings and permission denieds.

---

### Post by Red Long Johns on 2009-03-31
It turned out to be an error in the escape sequence sent to me, I guess I should have checked that first... :oops:

Now, to figure out how to mark this thread as solved...

---

