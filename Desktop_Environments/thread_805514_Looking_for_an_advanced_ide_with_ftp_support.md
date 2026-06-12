---
title: "Looking for an advanced ide with ftp support"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Zedzero on 2008-05-24
As an immigrant from windows, i'm very used to notepad++. And to my surprise, notepad++ doesn't have an official linux port. Since I'm a php developer, i need an ide. There are lots of them, including kate, kdevelop, bluefish. I have tried almost all available ides, but i didn't feel comfortable with any of them.

What all of them lack is a specific feature of notepad++: editing remote files via ftp without any hassle. It allows the developer to seamlessly edit any remote file. It just uploads them when you save. That's it.

Of course i am going to need other standard features like syntax highlighting, improved indentation control, code folding, optional code completion.

can anyone please recommend an ide for ubuntu? (kde applications are preferred, but gnome is ok too)

---

### Post by GeneralZod on 2008-05-24
> **Zedzero said:**
> 
What all of them lack is a specific feature of notepad++: editing remote files via ftp without any hassle. It allows the developer to seamlessly edit any remote file. It just uploads them when you save. That's it.


You should probably explain what aspect of this kate failed at, as it can easily edit text files over ftp:/ (or any other kio_slave protocol, for that matter).

---

### Post by Zedzero on 2008-05-24
I didn't know kate has ftp support. Thanks.

---

### Post by Coombabah on 2008-05-24
> **Zedzero said:**
> I didn't know kate has ftp support. Thanks.

I didn't know notepad++ had ftp support under windows.

If it has ftp support it may have sftp support.
My windows using friends have been using notepad++ with winscp, making a local copy of the server files and using winscp to update the remote server files when notepad++ changes the local copy.

I haven't used ftp for quite some time we usually use ssh/sftp to connect to/edit files on our servers. We are not allowed to use ftp anymore for security reasons.
If your server supports ssh you could use kdevelop/quanta for you php ide and edit the remote files via sftp.
This way you wouldn't be sending your server passwords out in plain text like you do with ftp.

---

### Post by eriqjaffe on 2008-05-25
You could use curlftpfs to mount the remote FTP site (sshfs if you want to mount sftp) and just point the IDE towards the mount point.

---

