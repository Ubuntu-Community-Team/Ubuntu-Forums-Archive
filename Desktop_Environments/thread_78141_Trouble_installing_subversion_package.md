---
title: "Trouble installing subversion package"
date: 2005-10-17
forum: Desktop Environments
---

### Post by skeen on 2005-10-17
sorry, I'm new to this.
I'm using Synaptic package manager to intall the subvesion package
(ver 1.2.0 is the one listed)
but I get this error 

[I]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/db4.2/db4.2-util_4.2.52-19ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/db4.2/db4.2-util_4.2.52-19ubuntu4_i386.deb)
  404 Not Found[/I]

Not sure why it cannot find the (dependent) package.  Is there a way to manually track it down and install it?

thanks,
Sam

---

### Post by dbott67 on 2005-10-17
There's a problem with the US archives.  Remove the US from your sources.list file as per this thread:

> By the way, the above sources.list has worked for others with similar problems, as noted in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

---

### Post by skeen on 2005-10-18
I tried again this morn and all was fine.

Thanks again for the reply

Sam

---

