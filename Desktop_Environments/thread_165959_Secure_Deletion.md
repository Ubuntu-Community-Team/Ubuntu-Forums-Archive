---
title: "Secure Deletion"
date: 2006-04-25
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-04-25
I'm looking for a secure way of deleting files totally on Ubuntu 5.10 Breezy Badger, but so far I see that using any journaling filesystem means secure deletion isn't guaranteed (I'm using Ext3 as default).

In that case, is it best to encrypt files tagged for deletion before sending them to the waste bin? Assuming someone wanted to get at my old password keys or financial documents etc., they'd have to not only recover the file from deletion, but crack a 4 kilobyte cipher. Would that do it?

I hear that a copy of the file may be kept elsewhere when encrypting the original, if so, is there a way to stop this? No point in having an encrypted folder if the original is buried somewhere without protection.

---

### Post by bswilson on 2006-04-25
Why not try one of the various secure delete programs our there that are open source, such as [Wipe?]("http://wipe.sourceforge.net/")

---

### Post by Admiral Valdemar on 2006-04-25
Because, with a journaled filesystem the chances are the file will be stored elsewhere in some form, which fsync can't deal with.

---

