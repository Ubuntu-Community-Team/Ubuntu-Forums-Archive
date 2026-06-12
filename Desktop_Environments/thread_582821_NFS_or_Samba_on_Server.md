---
title: "NFS or Samba on Server"
date: 2007-10-20
forum: Desktop Environments
---

### Post by McHenry on 2007-10-20
It appears to me that Ubuntu desktops can connect to Windows shares (samba) out of the box with no additional packages required such as NFS etc.

With this being the case would it not be better to share files on the server using Samba as opposed to NFS as this way the clients can connect straight away ?

Thanks in advance...

---

### Post by kidders on 2007-10-21
Hi there,

The best practice is probably to use whatever file sharing protocol is most native both to your clients & servers, so that shared files behave in a way that is as natural as possible for your users.

To take an extreme example, consider sharing files between a Linux box and a Mac using Microsoft's file sharing protocols. You'd essentially be forcing your machines to emulate a way of working with files that is incompatible with both of them, despite the fact that they each manage filesystems in almost exactly the same way. As a result, users would have a very "unnatural"-feeling experience. For example...
[LIST]
[*]Users would find it difficult to manage permissions & ownership effectively, and would experience unexpected, quirky behaviour.
[*]Users would be forced to obey Microsoft's file naming restrictions. As a silly example, it would be impossible to call a file "C:\", despite the fact that neither party to the file sharing connection would have any problem with it. As a result, applications may inexplicably fail to perform rename operations, or file creations, that ought to have been inconsequential.
[/LIST]

Basically, it's nice to try to share files in a way that will behave as closely as possible to the way your users' own files work. Linux can do a pretty good job with a wide variety of sharing protocols, so imo it's the client OS that gets the casting vote, when the OSs on both sides of a connection are different. When sharing files with another Linux box though, it surely makes no sense *not* to use NFS.

Another common scenario is where files are to be shared with a variety of operating systems. Unfortunately, if Windows is one of them, there is often no realistic choice apart from Samba, because of MS's lack of interoperability with other platforms, and it's poor support for platform-independent protocols (eg WebDAV).

I hope that helps.

---

