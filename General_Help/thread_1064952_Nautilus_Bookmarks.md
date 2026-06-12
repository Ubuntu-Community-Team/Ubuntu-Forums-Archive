---
title: "Nautilus Bookmarks"
date: 2009-02-09
forum: General Help
---

### Post by Gramps on 2009-02-09
Several times I have saved the samba mounted drive on XP computer in my Nautilus bookmarks. Each time it last for several days and then just disappears. That is the only bookmark that I use so I really don't know if it all bookmarks or just the ones to an external machine.

Any ideas on this?

---

### Post by jonlemur on 2009-02-09
Could it be that the computer hosting the drive is being shut down every couple of days?  Aside from that, I don't know of what could removing the bookmark.

---

### Post by Gramps on 2009-02-09
The computer that host the drive runs most of the time, it doesn't get shut down that often. The laptop that the bookmark is disappearing from however is shut down nightly.

So are the book marks in Nautilus are only good while the the 2 computer are connected?

---

### Post by jonlemur on 2009-02-09
No, they should be good indefinitely as far as I know.  I have a bookmark on my Ubuntu laptop connected to a Windows share on the network, and it stays even when I turn off my laptop.

[Someone else]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/300616") was having an issue that sounds similar, and he found that it was a problem with pcman file manager.  Could that be it?

---

### Post by Gramps on 2009-02-09
> **jonlemur said:**
> No, they should be good indefinitely as far as I know.  I have a bookmark on my Ubuntu laptop connected to a Windows share on the network, and it stays even when I turn off my laptop.

[Someone else]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/300616") was having an issue that sounds similar, and he found that it was a problem with pcman file manager.  Could that be it?

Well now that is really interesting. I do run pcman from time to time. So I just checked and by bookmark was gone and I hadn't rebooted. So I made a new one and then closed Nautilus and opened Pcman, no bookmark for the smb connection. Closed Pcman and opened Nautilus and as the bug report said the bookmark was gone. I did this several times with the same result. 

That's a bummer I like PCman as I can switch to admin from within it if needed, guess I will try turning this on for Nautilus and get rid of PCman.

Thanks for for guiding me to the solution to this problem.

---

