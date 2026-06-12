---
title: "NTFS file system incompatibility?"
date: 2008-11-26
forum: Desktop Environments
---

### Post by s_raiguel on 2008-11-26
Just had a kind of odd thing happen that I don't quite understand. With Thunderbird running under Ubuntu 8.04, I received a message with an attachment. Thinking the attachment, a Word document, would be better dealt with under Windows, I saved it in my Windows Documents directory, then as an afterthought decided to save the email as well, using Thunderbird's save as/file. When I got back to Windows, there was the attachment, which opened just fine. but the email, saved as a .html, refused to open. "File not found" said Windows, although the name was right there in the directory. Same with trying to copy, move, or delete this file. I even tried and old command line trick, using rmdir -S, to get rid of the file, directory, and all - "directory not empty". Finally, I was able to get rid of it by restarting Ubuntu, going to the Documents directory, and simply deleting the file, which deleted without further incident. So, does anybody understand what was going on here, because I don't. Did it have something to do with the fact that the email had an attachment, perhaps putting some kind of reference to the attachment in the saved email, a pointer whose object Windows was now unable to access? Or is there something not-quite-compatible with the way that Linux-flavored Thunderbird evokes the save function when confronted with NTFS?

---

