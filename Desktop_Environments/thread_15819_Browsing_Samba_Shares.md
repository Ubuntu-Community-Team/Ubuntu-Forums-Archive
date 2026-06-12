---
title: "Browsing Samba Shares"
date: 2005-02-17
forum: Desktop Environments
---

### Post by mdr on 2005-02-17
hmmm
I am having trouble using Nautilus (2.8.1 current warty release) to browse Samba shares on my linux server.

Have installed smbclient and samba to no effect
Response is really slow or not at all and then often nautilus hangs and does not even display local files.  On restart of Gnome all is then well again.

I am really just trying to achieve samba net browsing via a desktop icon and failing miserably.  Is there something basic I am missing or is Nautilus just not up to scratch?

 ](*,)

---

### Post by benjamin on 2005-02-17
Take a look to  [www.ubuntuguide.org](www.ubuntuguide.org)

Benjamin

---

### Post by mdr on 2005-02-18
hmm thx for the pointer but I had already been there.

however that does not explain slow performance of Nautilus in displaying the shares does it ?

or at least not that I noticed.  I did however do a search and found that adding the server to the hosts file does make performance slightly better.

I am still hoping that the speed would be better though.
Sigh perhaps I am going to have to use NFS.....

---

### Post by brousch on 2005-02-22
Samba slows down for me only in network folders where I have a lot of files. So if you are opening right to a folder with a lot of files it might always seem slow.

The only solution I know of for this problem is to break down the files into a folder hierarchy.

BTW, I have had this problem with samba for many years on different computers.

*I should say that this a problem on the server's samba server, not with the client. MS clients accessing the shares with many files are also slow.*

---

### Post by mdr on 2005-03-08
in this instance the samba shares run really well under windows.

having Hoary at home the newer versions of nautilus seem better when browsing shares there.

will wait and see for when Hoary goes final.

---

