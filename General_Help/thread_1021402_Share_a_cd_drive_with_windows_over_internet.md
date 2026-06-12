---
title: "Share a cd drive with windows over internet"
date: 2008-12-25
forum: General Help
---

### Post by ipburbank on 2008-12-25
I posted this in networking, but this is a question that is only kinda related there, so I figured that I'd post it here to so that more people can see:

> This is a networking question among other things: I have a samsung nc10, which doesn't have a cd drive. I also have a desktop computer with 2 cd drives. So my question is can I access some the cd drive from the nc10 (running windows home edition, the desktop running ubuntu)? I know that with windows there is a feature in workgroup that lets you do that, sharing drives among a home network, but I need to go from ubuntu to windows.


~any help would be great - istvan.

---

### Post by albinootje on 2008-12-25
> **ipburbank said:**
> I posted this in networking, but this is a question that is only kinda related there, so I figured that I'd post it here to so that more people can see:


You could do that with samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I think the default samba config file in /etc/samba/smb.conf even has a cdrom drive example in there.

Erhmm, I got confused. 
Sharing that over internet is in the subject of your posting.
In the body of your posting you talk about "home network".

Using samba (or worse ... NFS) over the internet is *not* recommended.
You need the ports 135/137 and 445 open, and some ISP's already block those ports.
Apart from that you would have to tighten the security of your samba config.

---

### Post by skippymo on 2008-12-25
man it is a pain for that to even remotely work.....go get a drive enclosure and take out one of your cd drives and put it in there....problem fixed usb cd drive.

check out dealnews.com for cheap enclosures

---

