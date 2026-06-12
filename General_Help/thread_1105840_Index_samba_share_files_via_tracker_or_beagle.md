---
title: "Index samba share files via tracker or beagle"
date: 2009-03-25
forum: General Help
---

### Post by adad on 2009-03-25
I have a server containing a huge number of documents of all kinds: PDFs, CHMs, DOCs, ODTs, TXTs, etc. I access the files via samba shares. The share I'm interested in contains about 100,000 files.

I need some search/indexing application like tracker or beagle that is able to index the files in the samba share, and hold the indexes in my local computer.

This server is not accessible for me all the time, as I am not always at the office, so I disconnect from the LAN where the server resides.

Therefore it's very important that I don't need to re-index the samba shares everytime I dock in the office.

**Questions / Requirements**

1. How do I make tracker/beagle index samba shares?

2. How do I configure it, so that the indexing is not re-made everytime I connect to the share?

---

### Post by CRCarl on 2009-03-25
It is possible to do this beagle or tracker but it is a lot easier to do it with Google desktop. 
 Take a look at it here [http://desktop.google.com/linux/index.html]("http://desktop.google.com/linux/index.html"). You would need to add the path to your samba share to the list of indexed paths.

---

### Post by kimda on 2009-03-26
I wish tracker would be able to index shares as well. Now the only way it would be possible is if you would mount all the shares in your home folder.

---

### Post by adad on 2009-03-27
Hi guys,

thanks for your answers. I really hate it to depend on Google also for my local search. I believe it´s enough to have to go through them for my "external" searches, but for my local info...

How would it be possible to use tracker/beagle to index samba shares?

I really appreciate any hint regarding this.

---

### Post by CRCarl on 2009-03-28
It should work if you mount the share in your home directory.

---

### Post by atti84it on 2009-11-25
could please somebody tell how to "mount a share in the home dir"? (as CRCarl says)

I tried with:[INDENT]sudo mount -t cifs //server/path local_dir/
[/INDENT]and in some way it worked: I could browse through nautilus, but some letters in the path (é, è, etc..) were replaced with "?" or other some strange symbols..
this malfunction doesn't happen if I surf in a normal way (smb://server/path)

thank you!!

---

