---
title: "Unable to share folders in Ubuntu Hardy 8.04.2"
date: 2009-03-18
forum: General Help
---

### Post by sefs on 2009-03-18
Hi all I just installed hardy server.  But I am unable to share a folder.  I cannot remember it being this difficult in 7.10 or 8.10.  But somehow i am just missing it.  When I double click on the share folder to open it ... I get the password prompt I enter that information ...but it tells me it cannot view the share.

I've been thru the usual samba set up guides (the same one i used for my desktop 8.10)  but no cigar on 8.04.

What am I missing here.

Thanks.

---

### Post by prince_niceguy on 2009-03-18
have you shared the folders as a root? I found in hardy/interpid, folder shared with root gets displayed correctly.... make sure you give read/write permissions to everyone... to avoid password prompt..

---

### Post by sefs on 2009-03-18
I now am experiencing problems in intrepid...and here is why.

I use to share folders by directly editing smb.conf on intrepid.  I decided change this to right clicking and share options...but the "allow persons to write to this folder" is not being kept across a reboot.

Also the share is unable to be loaded.

But if i put my share config directly into smb.conf that works.

It is the opposite in 8.04...directly editing smb.conf does not work but right clicking and using share options works even across reboots.

when i use findsmb  neither computer can see each other.

---

### Post by sefs on 2009-03-18
I've removed and reinstalled samba on 8.10 by first right clicking and share options.  Samba was automatically installed.

It however prompts me to for a username/password which i want...and works ONLY with my main account.

I tried adding a user2 to users and to samba users but it will not load the share for user2 only for my main user.

How do i make this happen for user 2

---

