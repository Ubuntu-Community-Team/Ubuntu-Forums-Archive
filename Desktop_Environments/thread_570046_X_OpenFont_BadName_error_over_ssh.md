---
title: "X_OpenFont BadName error over ssh"
date: 2007-10-07
forum: Desktop Environments
---

### Post by sirjis on 2007-10-07
Certain programs that I try to run over ssh with X forwarding (I've tried with both -X and -Y) fail with an error related to X_OpenFont.  For example, if I try to run Cadence circuit simulation software, I get the following error:

```
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  16
  Current serial number in output stream:  31
```

What programs can I run to try to determine *which* font is the troublesome one?  I tried running with strace but I'm not sure what I should be looking for -- there weren't any obvious calls with font names before the stderr write calls.

This error is not limited to this specific software -- I have seen this same error in previous semesters using software from other companies.  Some software works fine though.

---

### Post by sirjis on 2008-01-08
Just in case someone finds this, I have solved my problem (or at least found a workaround):

This error only shows up in xgl/beryl, not in the default gnome interface.  Just changing the session type on the login screen fixed all of the problems.

---

