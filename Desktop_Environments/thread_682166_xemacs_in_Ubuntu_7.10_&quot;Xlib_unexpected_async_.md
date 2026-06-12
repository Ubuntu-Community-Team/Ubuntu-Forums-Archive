---
title: "xemacs in Ubuntu 7.10: &quot;Xlib: unexpected async reply&quot;"
date: 2008-01-29
forum: Desktop Environments
---

### Post by Jared Oberhaus on 2008-01-29
I've been using xemacs in Ubuntu 7.10 happily for quite some time, but since the beginning, every once in a while, I get output like this:

```
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006a7
  Serial number of failed request:  1617067
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006a8
  Serial number of failed request:  1617068
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006a9
  Serial number of failed request:  1617092
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006aa
  Serial number of failed request:  1617113
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006ab
  Serial number of failed request:  1617173
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006ac
  Serial number of failed request:  1617243
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006ad
  Serial number of failed request:  1617311
  Current serial number in output stream:  1617066
X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x30006ae
  Serial number of failed request:  1617391
  Current serial number in output stream:  1617066
Xlib: unexpected async reply (sequence 0x18baae)!
Xlib: unexpected async reply (sequence 0x18babf)!
Xlib: unexpected async reply (sequence 0x18bc38)!

```

When this happens, my xemacs session seems 100% operational, however, keyboard commands to switch focus between the frames (that's emacs talk for a separate X-Window) do not make it look like focus has actually changed to the other frame--but it has, when I type I am typing in the other frame. Sometimes, however, this type of problem results in a complete lockup of xemacs, but that's rare.

Restarting of course clears up this problem until it happens.

When I Google for this string, I only get things that are 5 years old or more, and not Ubuntu related. This seems like a new thing. Perhaps this is because of the way I use xemacs? I am using a single xemacs session with two side-by-side frames (X-windows).

---

### Post by Jared Oberhaus on 2008-02-12
Anyone see this issue with "Xlib: unexpected async reply"? Or is it only me?

Maybe I should be using GNU emacs instead of XEmacs... :(

---

### Post by jlr_0 on 2008-04-08
I do have the exact same problem when using XEmacs with Ubuntu.

I hope I will find a solution  very soon because I do not want to switch to Emacs.

--
René

> **Jared Oberhaus said:**
> Anyone see this issue with "Xlib: unexpected async reply"? Or is it only me?

Maybe I should be using GNU emacs instead of XEmacs... :(

---

### Post by jlr_0 on 2008-05-14
Solved!

Switch to Ubuntu 8.04.

--
Rene

---

