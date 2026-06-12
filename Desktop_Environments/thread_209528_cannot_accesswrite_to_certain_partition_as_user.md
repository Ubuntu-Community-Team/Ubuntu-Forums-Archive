---
title: "cannot access/write to certain partition as user"
date: 2006-07-05
forum: Desktop Environments
---

### Post by kazuya on 2006-07-05
(1) Why is it that there are some partitions that I cannot change their permisions even as root to allow other users to write to? - This was an issue on one of my Ubuntu installs two days ago.

These partitions are regular reiserfs and ext3 partitions for data storage. I should be able to write or download files to those drives as a user, but even as root, I cannot change those partition permisions?

Any work around?

(2) If I had a user, e.g john, and I was going to reinstall, but preserve user john and his profiles in Ubuntu; how do I do that?

---

### Post by xrchris on 2006-07-05
1) Read about 'chmod' here > [http://catcode.com/teachmod/](http://catcode.com/teachmod/) as i think this is probably what you require or alternatively read up about the 'chown' command.

---

