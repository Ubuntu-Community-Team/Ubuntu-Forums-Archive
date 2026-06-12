---
title: "Group 'admin' does not exist"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Moyerman on 2007-06-02
Perhaps it is time to reinstall? The first problem was "unable to lookup ubuntu via gethostbyname" when I tried to use sudo. After reading several solutions I was able to resolve that. Now during boot I see    
"ERROR: Temporary failure in name resolution" The system will not accept my sudo password. I went into 
recovery mode logged in as root. Opened /ect/sudoers using "sudo visudo" the file looked exactly like the one in the psychocats.net/ubuntu tutorial except the very last line was missing.
#Members of the admin group may gain root privileges 
%admin ALL=(ALL) ALL
Then I went to "nano /ect/group" There was nothing in this file. It was empty. I tried "addgroup joe admin"
and the message was "The group 'admin' does not exist"
Any ideas?

---

### Post by aysiu on 2007-06-02
Maybe [this](http://ubuntuforums.org/showthread.php?p=840154#post840154) might help.

---

