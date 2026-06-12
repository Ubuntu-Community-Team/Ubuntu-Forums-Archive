---
title: "Creating space?"
date: 2009-02-20
forum: General Help
---

### Post by magh-87 on 2009-02-20
I've been searching for the forums for the past few days trying to find answers to my question so I apologize if I missed the answer I'm looking for somewhere.

A while ago I turned my WinXP tower into a Ubuntu 8.04 computer. Everything is great so far and I'm still learning quite a bit and for whatever I don't know, there is usually an answer somewhere on the forums for me. 

What I'm looking to do with this computer is allow a select group of people (primarily friends and family) to access my computer and upload their music, videos, whatever files they don't have room for on their own computer anymore but will need again in the near future.

My issue is that I don't know how to go about this as I've never really attempted something like this before but I have the hard drive space and my friends have the contents.

Any help would be greatly appreciated!

Thanks in advance 

Magh

---

### Post by taurus on 2009-02-20
One way is to install a ftp server (something like vsftpd) on your machine and create accounts for your friends/family members.  Then, they can upload whatever they want to their own $HOME using their account on your machine.  And if they need those files later, then can just download them from your machine again.

---

### Post by Woody1987 on 2009-02-20
Are you copying them locally or over the internet? If its over the internet you could set up and ftp server on your machine and then allow them to upload, if locally you could try setting up and nfs share or samba share if they are using windows.

---

### Post by magh-87 on 2009-02-20
Thank you very much for the quick replies!

I've installed vsftpd but I have to go to work so I'll configure it tomorrow after I get up (late night shifts). I'll let you know how it turns out.

Thanks again :)

Magh

---

### Post by magh-87 on 2009-03-02
So I've been working at this for the last week and I can't seem to get this to work for me. Nothing seems to be working for me, which is really frustrating. Is there a good tutorial for this that is pretty much a step by step since this is taking quite a bit of time.

---

### Post by rsay on 2009-03-02
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html]("Setting up a server with proftpd")

---

