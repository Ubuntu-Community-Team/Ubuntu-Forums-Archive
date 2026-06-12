---
title: "ReiserFS Max File Size?"
date: 2005-12-15
forum: General Help
---

### Post by polypill on 2005-12-15
I'm running Ubuntu versuib 5.10 with a ResiserFS file system and the kernel package 2.6.12-9. I seem to be hitting a max file size of 4gb. After some research, it appears this is the max size on ReiserFS version 3.5 but was fixed in 3.6.

Is Ubuntu 5.10 using the older ReiserFS version 3.5? How can I check? If it is, can I upgrade without having to compile a custom kernel?

If that isn't my problem, then does anyone have any other suggestions?

---

### Post by ape on 2005-12-15
Breezy is using the 3.6 version of ReiserFS.  It will drop down to 3.5 compatibility mode if you are using an older 2.2 kernel, but I don't think that applies here.<G>

What are you using to create the file?  What errors are you getting regarding the file size?

---

### Post by JsPr on 2005-12-15
Found this:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Looks like it's TB sizes, shouldn't be a problem with 4GB.

---

### Post by polypill on 2005-12-15
I run into the problem when trying to upload large files with SFTP, using the default SSH server and a Filezilla client. I also have the problem when I want to use unrar-free on a file that will create a > 4gb file. Both times I get the error "File Size too Large"

Maybe it is just those 2 applications that wont allow a larger file, but I don't know how to test it another way.

---

### Post by psusi on 2005-12-15
[QUOTE=polypill]I run into the problem when trying to upload large files with SFTP, using the default SSH server and a Filezilla client. I also have the problem when I want to use unrar-free on a file that will create a > 4gb file. Both times I get the error "File Size too Large"

Maybe it is just those 2 applications that wont allow a larger file, but I don't know how to test it another way.[/QUOTE]


Yea, it is the applications, not the filesystem.  By the way, I'm pretty sure that SFTP does not have anything to do with SSH.  You copy files with SSH using the scp command.  I'd be surprised if that has the 4 GB limit.

---

### Post by ape on 2005-12-15
I believe that it's the programs lack of large file support causing this issue.  I was just able to create a 5GB file on my reiserfs partition using the following command:

dd if=/dev/zero of=/DVD_store/swapfile bs=1024 count=5242880

This completed successfully.

Using breezy with the 2.6.12-10 kernel.

---

### Post by polypill on 2005-12-15
[QUOTE=psusi]Yea, it is the applications, not the filesystem.  By the way, I'm pretty sure that SFTP does not have anything to do with SSH.  You copy files with SSH using the scp command.  I'd be surprised if that has the 4 GB limit.[/QUOTE]

I'm pretty sure SSH does have a lot to do with SFTP, I think it tunnels through SSH and is the same as scp. Just an SFTP client gets folder listings so you can navigate.

So it probably isn't the FS, what should I do now? Is there a quick way to create a > 4gb file so I can completely rule out the FS?

---

### Post by polypill on 2005-12-15
[QUOTE=ape]I believe that it's the programs lack of large file support causing this issue.  I was just able to create a 5GB file on my reiserfs partition using the following command:

dd if=/dev/zero of=/DVD_store/swapfile bs=1024 count=5242880

This completed successfully.

Using breezy with the 2.6.12-10 kernel.[/QUOTE]

I just tried this and I could create a file > 4gb, thanks for the tip.

I'm going to see if I can upload a 5gb file using scp

---

### Post by psusi on 2005-12-15
I'm pretty sure that SFTP is just FTP over an SSL connection, like how https is http over SSL.  That doesn't really have anything to do with ssh.  

[QUOTE=polypill]I'm pretty sure SSH does have a lot to do with SFTP, I think it tunnels through SSH and is the same as scp. Just an SFTP client gets folder listings so you can navigate.

So it probably isn't the FS, what should I do now? Is there a quick way to create a > 4gb file so I can completely rule out the FS?[/QUOTE]

---

### Post by polypill on 2005-12-15
[QUOTE=psusi]I'm pretty sure that SFTP is just FTP over an SSL connection, like how https is http over SSL.  That doesn't really have anything to do with ssh.[/QUOTE]

They both run on port 22, unlike http and https.

---

### Post by psusi on 2005-12-15
According to /etc/services, sftp uses port 115.  

[QUOTE=polypill]They both run on port 22, unlike http and https.[/QUOTE]

---

