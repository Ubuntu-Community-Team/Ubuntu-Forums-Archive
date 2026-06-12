---
title: "Accessing FTP mount through samba"
date: 2009-03-03
forum: General Help
---

### Post by Bleh7777 on 2009-03-03
Is it possible to access an FTP mount mounted with curlftpfs through samba from Windows?

If not, does anyone know a way I can accomplish this?  I'm looking to have an (almost) seamless interaction between a remote FTP server and my local server that I can also access through Windows.

Windows' current FTP mapping right now isn't very good as I can't modify the remote files, rather I have to download and upload again.

---

### Post by CrucifiedEgo on 2009-03-03
I don't see why not.  Have you tried mounting an FTP account using curlftpfs, and then sharing it with samba?  if it doesn't work, why?  any errors?

---

### Post by Bleh7777 on 2009-03-03
I shared the parent directory but the mount point didn't show up.  I also tried sharing the mount point itself but Windows said that it was inaccessible, which is obviously false, because I can access it from my server.

---

### Post by Bleh7777 on 2009-03-03
I found someone else having what appears to be the same problem over at [http://markmail.org/message/zb23cqcfk6rmwxmp](http://markmail.org/message/zb23cqcfk6rmwxmp) but he didn't receive a response.

---

### Post by dcstar on 2009-03-03
> **Bleh7777 said:**
> Is it possible to access an FTP mount mounted with curlftpfs through samba from Windows?

If not, does anyone know a way I can accomplish this?  I'm looking to have an (almost) seamless interaction between a remote FTP server and my local server that I can also access through Windows.

Windows' current FTP mapping right now isn't very good as I can't modify the remote files, rather I have to download and upload again.

The FTP protocol is a file transfer based protocol (FTP - **F**ile **T**ransfer **P**rotocol - geddit?), it does not have the capabilities to access parts of or modify remote files. It simply copies whole files from one place to another.

The reason other protocols exist (like SMB) is because of the limitations of previous protocols. Having "access" via one protocol does not mean you have the same functionality that is available via other protocols.

---

### Post by Bleh7777 on 2009-03-03
But surely there must be a way to mount the remote filesystem such that it can simulate a local filesystem?

The most I'm going to do is save text files for a website, so is there the ability to automatically copy a file down on access and send it back up on save?  curlftpfs already does this as I can use nano to edit a file on the remote file system, so I presume it's just copying it back and forth on modification.  Since that already works, why can't the interface be extended to work with samba shares?

---

### Post by Bleh7777 on 2009-03-04
If this isn't possible through curlftpfs, is it possible through any other method at all?

---

