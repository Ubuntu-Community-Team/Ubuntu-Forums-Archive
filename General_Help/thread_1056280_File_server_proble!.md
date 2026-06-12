---
title: "File server proble!"
date: 2009-01-31
forum: General Help
---

### Post by Adeang on 2009-01-31
I have just installed xubuntu on my older computer, and I have a windows vista computer, and would like to store my media and other files on the xubuntu computer, so basically I want to have it as a file server

I have tried installing samba, but I can't get anything to work

so can you please tell me how to do this from scratch, lets just say I have a clean install of xubuntu 32 bit!

how do I make it a file server?

---

### Post by Iowan on 2009-01-31
[Here]("https://help.ubuntu.com/community/SettingUpSamba") is a good Samba help page. Xubuntu does some things a little different than Ubuntu, but hopefully the Samba server setup is the same.

---

### Post by HermanAB on 2009-01-31
The easiest file server to get to work is FTP, so install proftp or vsftp and use filezilla on Windows.  Proftpd and vsftpd work out of the box - no configuration required.  Using that, you can get files moving about easily.

The next problem is Samba and for that you may want to look at this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by Adeang on 2009-01-31
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/SettingUpSamba") is a good Samba help page. Xubuntu does some things a little different than Ubuntu, but hopefully the Samba server setup is the same.

that was the guide I was talking about in previous from previous post, I got stuck after I installed it.

---

### Post by Adeang on 2009-01-31
> **HermanAB said:**
> The easiest file server to get to work is FTP, so install proftp or vsftp and use filezilla on Windows.  Proftpd and vsftpd work out of the box - no configuration required.  Using that, you can get files moving about easily.

The next problem is Samba and for that you may want to look at this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

I think you lost me, and I opened up the synaptic package manager or whatever and searched for proftpd and vsftp and could not find either, so then I went to that url you posted and it was telling me about some wizard for installing samba and I searched for wizard in the synaptic thingy and couldnt find that either.

Please remember I have no idea what I am doing so please step by step.

---

