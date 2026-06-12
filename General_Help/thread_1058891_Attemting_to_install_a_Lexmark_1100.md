---
title: "Attemting to install a Lexmark 1100"
date: 2009-02-03
forum: General Help
---

### Post by ex-para on 2009-02-03
I am attemting to install a Lexmark 1100 all in one in Ubuntu 8.04 but this is as far as I get and I have tried a few times.
Any ideas please.

barrie@barrie-laptop:~$     sudo mkdir lexmark 

[sudo] password for barrie: 

barrie@barrie-laptop:~$ cd lexmark

barrie@barrie-laptop:~/lexmark$ wget [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

--14:36:33--  [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

           => `CJLZ600LE-CUPS-1.0-1.TAR.gz'

Resolving [www.downloaddelivery.com](www.downloaddelivery.com)... 12.120.2.110

Connecting to [www.downloaddelivery.com|12.120.2.110|:80](www.downloaddelivery.com|12.120.2.110|:80)... connected.

HTTP request sent, awaiting response... 200 OK

Length: 4,301,167 (4.1M) [application/x-gzip]

CJLZ600LE-CUPS-1.0-1.TAR.gz: Permission denied



Cannot write to `CJLZ600LE-CUPS-1.0-1.TAR.gz' (Permission denied).

barrie@barrie-laptop:~/lexmark$ 

barrie@barrie-laptop:~/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory

tar: Error is not recoverable: exiting now

tar: Child returned status 2

tar: Error exit delayed from previous errors

barrie@barrie-laptop:~/lexmark$ 

barrie@barrie-laptop:~/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

bash: install.tar.gz: Permission denied

barrie@barrie-laptop:~/lexmark$ 

barrie@barrie-laptop:~/lexmark$ tar -xvzf install.tar.gz****

---

