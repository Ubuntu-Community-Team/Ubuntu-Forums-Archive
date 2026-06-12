---
title: "Java Eclipse Graphical Corruption after upgrade to 9.10"
date: 2009-10-29
forum: Desktop Environments
---

### Post by sherington on 2009-10-29
Hi,

Apologies if I did not pick the right forum for my question.

I did a full upgrade to Ubuntu 9.10 and I have one problem after upgrading.

I use Java and Eclipse extensively under Ubuntu. I run the latest Sun JDK 1.6.0_16 and Eclipse 3.5.

The problem occurs in the Eclipse editor, e.g. when editing a Java file. 

You get a Javadoc tool-tip popup when you point the mouse pointer at a Java element. This works fine. The issue is that if you use the scroll-wheel to scroll the editor up or down when the Javadoc popup is still visible, the Javadoc popup leaves a black rectangle in the editor. This only happens if you use the scroll-wheel.

I see this problem with the standard graphics drivers and the recommended proprietary nVidia drivers.

I have attached a "before" and "after" screenshot.

Before the upgrade I did not see this problem at all so I don't think it's a JDK or Eclipse bug.

Anyone have any hints on this please?

$uname -a
Linux mark-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

$lspci -grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)

---

### Post by sherington on 2009-10-31
I now run a fresh install of 9.10 (64bit) rather than an upgrade, although I'm not sure this in itself made any difference.

In case anyone else sees the problem I reported, it is solved for me now and I think it may be related to:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/446148](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/446148)

This bug report makes it clear that there's a wider SWT+GTK issue than just Eclipse/Java.

I didn't notice at first, but the same problem also causes problems with buttons ignoring mouse-clicks etc.

The solution for me was as per the links in that bug report, i.e. to do this:

$export GDK_NATIVE_WINDOWS=1

If I don't specify this flag, I get a momentary black rectangle as described earlier but it disappears so it's not so bad.

But if I DO add this flag, the previously described popup works flawlessly - no black rectangle at all.

---

### Post by TLArevo on 2010-11-13
Could you please explain what you did with little detail I'm eclipse newbie I have the same issue please help to fix it :)

---

