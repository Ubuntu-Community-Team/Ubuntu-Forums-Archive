---
title: "Nautilus won't see my files"
date: 2010-06-02
forum: Desktop Environments
---

### Post by cristian.llamas on 2010-06-02
Since a couple of days back mostly all the folders and files I had on my download directory are not visible in Nautilus. Some of them are still there, but the majority it's like vanished.
The folder is where everything I download with Transmission goes into.

The tricky thing is that all those files are visible through the terminal, pcman file manager or konqueror, but not Nautilus, which is very annoying.

I've tried reinstalling Nautilus from Synaptic, checking the 'show hidden files' option, checking and changing files and folder permissions and I also checked that there's no hidden instance of Nautilus running.

I have Ubuntu 10.04 (upgraded from a 9.10) and the files are on a ext4 drive. Nautilus version is 2.30.1

Any ideas?

---

### Post by cristian.llamas on 2010-06-02
Quick update, I tried booting up with a Ubuntu liveCD and the problem was exactly the same, so I figure it must have something to do with the properties of the files, permissions or something like that.

---

### Post by cristian.llamas on 2010-06-04
Ok, so I finally solved the issue in a very simple way. This problem was ocurring only with one folder, so I just created a new one and moved all files and folders from the terminal using the mv command. Then I removed the original folder, renamed the new one to the same old name (so that all programs and links pointing to it kept working) and everything is fine now!

---

