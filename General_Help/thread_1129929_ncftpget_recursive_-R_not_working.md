---
title: "ncftpget recursive -R not working"
date: 2009-04-19
forum: General Help
---

### Post by manolo_asdf on 2009-04-19
hi,

I want to download ftp folder recursively with ncftpget. I am using the -R option but it does not work.

Doing following does not download anything:
ncftpget -T -R -v -u user -p pwd server.com /home/tmp /www

Appending an asterix does download something but not recursively (only files from /www/ are downloaded no directories).
ncftpget -T -R -v -u user -p pwd server.com /home/tmp /www/*


what is wrong here?
thanks.

---

