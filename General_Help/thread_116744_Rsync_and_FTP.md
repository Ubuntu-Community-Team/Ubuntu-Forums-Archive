---
title: "Rsync and FTP"
date: 2006-01-13
forum: General Help
---

### Post by ajwagner777 on 2006-01-13
Hey guys, this is probably a newbie question.

I am trying to use rsync to mvoe files to an FTP server.  The equipment does not allow me to use any other method to transfer files.  So i need to know if rsync will allow an ftp connection.  every time i try to sync to my ftp server it tells me connection refused.  any ideas?  should i use another software tool? should i boot the damm thing to the curb?

---

### Post by Mr_Grieves on 2006-01-13
RSYNC is it's own application/protocoll.. you use Rsync in both ends.. not FTP in one and Rsync in the other.

Read about RSYNC: [http://sunsite.dk/info/guides/rsync/rsync-mirroring.html](http://sunsite.dk/info/guides/rsync/rsync-mirroring.html)
Read about RSYNC over SSH: [http://www.jdmz.net/ssh/](http://www.jdmz.net/ssh/)

---

### Post by adamonduty on 2006-01-13
You might also use unison ([http://www.cis.upenn.edu/~bcpierce/unison/)](http://www.cis.upenn.edu/~bcpierce/unison/)). You should be able to mount an ftp server to a local directory (not exactly sure how to do that, but should be easy enough), and then use unison locally to sync the two directories. It requires no extra software on the server. Just remember that unison is different from rsync in that it actually syncs instead of just one way mirroring.

---

