---
title: "BZFlag"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by clevedonal on 2006-10-29
I got Dapper up and running while wife and kids were away last week, copied all my bookmarks/files from my Suse box.
I've been BZflagging in peace - However my boy also likes to play BZ, but when he logs on as a user and tries BZ, the screen pops up then disappears immediately. (No such probs with Suse) I've tried looking at his permissions but cannot seem to see any real difference in mine to his except i'm admin. 

I cannot seem to be su under his logon using either my password or his?  (is this a different query?) 

Box:
Athlon 2000+
1GB ram, 200GB Win2000, 200gbKubuntu
Nvidia card, (drivers installed via automatix)

(I'm not very good at BZ - i'm sure some of you have whacked me good) :mrgreen:

---

### Post by Perfect Storm on 2006-10-29
Try start BZ up via the terminal and post the outcome thereafter.

---

### Post by clevedonal on 2006-10-29
> **Artificial Intelligence said:**
> Try start BZ up via the terminal and post the outcome thereafter.

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x135
  Serial number of failed request:  122
  Current serial number in output stream:  124




Thanks for your prompt reply AI

---

### Post by clevedonal on 2006-10-31
> **clevedonal said:**
> I got Dapper up and running while wife and kids were away last week, copied all my bookmarks/files from my Suse box.
I've been BZflagging in peace - However my boy also likes to play BZ, but when he logs on as a user and tries BZ, the screen pops up then disappears immediately. (No such probs with Suse) I've tried looking at his permissions but cannot seem to see any real difference in mine to his except i'm admin. 

I cannot seem to be su under his logon using either my password or his?  (is this a different query?) 

Box:
Athlon 2000+
1GB ram, 200GB Win2000, 200gbKubuntu
Nvidia card, (drivers installed via automatix)

(I'm not very good at BZ - i'm sure some of you have whacked me good) :mrgreen:

if anyone can help with this i'd be pleased!

---

### Post by MkfIbK7a on 2006-12-26
have the same excact problaem

---

### Post by Perfect Storm on 2006-12-26
and it's bzflag from the repo?


wert613, do you have the same card as clevedonal?

---

### Post by Cannaregio on 2007-01-22
Similar problems here with edgy
Worked fine in dapper.

Here the output:

```
bzflag
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x156
  Serial number of failed request:  144
  Current serial number in output stream:  146

```

---

### Post by MkfIbK7a on 2007-02-07
ok the problem with mine was the graphics card hope this helps :D

---

