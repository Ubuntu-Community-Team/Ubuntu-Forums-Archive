---
title: "Unfortunately, I need to uninstall Ubuntu"
date: 2005-10-02
forum: Desktop Environments
---

### Post by AdeptPaladin on 2005-10-02
Don't get me wrong, it's not the distro's fault that I'm doing this.  I like Ubuntu and have had the most success getting it to work out of any distro I've dealt with so far.  However, due to space concerns and my wife's insistance, I need to go back to a pure windows solution.  Once my other PC is back up and running I'll be loadin Ubuntu back onto there and getting back into the thick of it.

So... how do I do it?

When I installed Ubuntu, I did a dual boot system  (HH 5.04/WinXP-SP2).  However I have OEM install CD's so no 'recovery console' option to fdisk /mbr or fixboot with.  How do I go about removing Ubuntu and restoring the ntloader and mbr?

---

### Post by yabbadabbadont on 2005-10-02
If the install didn't backup the original mbr somewhere, and I can't find one on my machine anywhere, then you are kind of stuck.  Since you have installed SP2 on WinXP, you should be able to install the recovery console from the SP2 directory or CD if you have one.
Here is a Microsoft knowledgebase article on the issue (which I had to use myself).  I think method 3 is the one you need to look into.
[http://support.microsoft.com/default.aspx?scid=kb;en-us;898594](http://support.microsoft.com/default.aspx?scid=kb;en-us;898594)

---

### Post by GreyFox503 on 2005-10-02
You may have already thought of this, but just in case...

Could you borrow someone else's WinXP CD that has a full recovery console?  Most people I know use this "windows" thing. :)

Of course, most people might have your OEM-version also...

You would only need it for a little while to restore your MBR.  Sounds like you already know how to do it.

---

### Post by yabbadabbadont on 2005-10-02
Actually, the article I pointed him to I found because I tried to install the recovery console off of my WinXP CD after I had already updated to SP2...  it don't like that at all.  So, unless he can borrow a new WinXP CD that already has SP2 on it, he will have to try Microshaft's workarounds.

---

### Post by Gezzer on 2005-10-02
u can use a 98SE boot floppy to fdisk the partition and reset the MBR
at the A> write
fdisk /mbr

that will reset the mbr to the windows defaults ...

---

### Post by jeffjj on 2005-10-02
> However, due to space concerns and my wife's insistance
If you can afford it get her a Mac. That is what I did and it turned out great. Not only are we a complete Unix family (Mac and Ubuntu) but we never have any problems. Spyware, Adware, viruses, lockups, memory issues, ect are just things I read about on eweek.com. She is thrilled with the Mac and I am thrilled that I do not have to support Windows. A true win (no pun intended) all the way around.

---

### Post by oddflux on 2005-10-02
"due to space concerns" That quote made no sense to me personally.
Also try things like fdisk, they'd come in handy when you want to delete a partition. :)..

---

