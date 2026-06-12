---
title: "Full encrypted system with ESSIV"
date: 2006-03-12
forum: Desktop Environments
---

### Post by QuestionsQuestions on 2006-03-12
I recently tried the full encrypted system howto at [http://www.ubuntuforums.org/showthread.php?t=120091](http://www.ubuntuforums.org/showthread.php?t=120091).  I followed the original poster's instuctions step by step (except for inserting the "-d /dev/urandom" switch when using cryptsetup to create the swap partition as suggested in a reply later in the thread) and everything works fine.

However, I wanted to try using stronger encryption (aes-cbc-essiv:sha256).  I've tried several things - basically, as I understand it, I should just be able to specify "-c aes-cbc-essiv:sha256" when using cryptsetup to create each partition, and "cipher=aes-cbc-essiv:sha256" for each line in /etc/crypttab to let the system know about it.

When I restart, it dies with kernel panic, just like it would with the wrong passphrase (passphrase is correct, though).  Is there another config file I need to modify somewhere to let the system know I'm using ESSIV?

Thank you.

---

