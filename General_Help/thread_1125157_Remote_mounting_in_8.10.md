---
title: "Remote mounting in 8.10"
date: 2009-04-14
forum: General Help
---

### Post by mintonman on 2009-04-14
Hi all,

very sorry if the below question has already been well answered somewhere - I have been searching for a while and can't find the help I need!

I have a desktop running Ubuntu 8.10 - I want to automount at start-up a share on a server running Ubuntu 7.04.

With Gutsy, I had a smbfs line in my /etc/fstab, and this gives me the perfect solution - when I log in, there's a mounted "drive" visible on my desktop - and I can navigate seamlessly to that "drive" when I'm opening a file in OpenOffice, or uploading a file to Gmail.

I just can't get this working in 8.10 :(

There are lots of discussions of this online (I've tried using cifs, tried with nounix, etc) but nothing seems to work.

Is this just an unfixed bug in 8.10? in cifs? Or is there a workaround I could use in my situation? Is there a non-samba way for one ubuntu box to remote mount a shared directory on another ubuntu box?

Without this fixed, keeping our small non-profit a linux-only environment is not going to be possible, I fear - non-technical users need transparent access to the shared files on the server many times each day!

Many thanks for any help!

Mark :)

BTW - line from Gutsy /etc/fstab - 
//server/sharename /mnt/shares/sharename   smbfs  auto,credentials=/root/.credentials,rw,fmask=0777,dmask=0777,uid=1000,users   0 0

---

### Post by askreet on 2009-04-14
> **mintonman said:**
> Is there a non-samba way for one ubuntu box to remote mount a shared directory on another ubuntu box?

I'm going to disregard all of your cifs issues, since there are no windows machines involved using cifs seems kind of pointless.

To answer the quoted, yes.  Use NFS.

Here's a neat tutorial:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

Hope this helps.
- askreet

---

### Post by timcredible on 2009-04-14
i would recommend nfs also since nfs has been around for decades and unix/linux supports it natively.  as for getting smb to work on your 8.10 machine, have you installed the smb client packages via synaptic?  i have 8.10 on one machine, and 7.10 on another, and i share and connect from both to both with smb with no issues (i right-click on the directory to share it, and use Places->Network to mount remote shares).

---

### Post by mintonman on 2009-04-16
Many thanks for this! I knew there must be a more linux-native way to do things. :)

I will set up and configure nfs (nice clear tutorial, by the look of it) - which sounds like it will sort my access from my ubuntu desktops to the server fine.

We _do_, however, occasionally need to boot up a windows machine (when someone sends us a Publisher file that we simply have to see, for example), and we have a couple of old XP laptops in a cupboard for this purpose. 

Can I leave Samba running on the server for that machine to use to see the shared files, and have nfs working simultaneously on the server for desktop access, and will they play nicely with each other if the windows user and I both try and edit the same file (for example)?

Many thanks again,

Mark

---

