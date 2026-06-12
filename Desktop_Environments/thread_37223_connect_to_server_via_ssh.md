---
title: "connect to server via ssh"
date: 2005-05-26
forum: Desktop Environments
---

### Post by secundar on 2005-05-26
Hi, I'm looking for a way to connect to a local server to edit files - on the server - without copying them to my laptop. I tried samba, and it works, but I cannot seem to access the share from within my application (File->Open...). Nothing is listed in /mnt and I'm not sure where else to look.

I read that using ssh to connect makes it seem like the server is actually local but i cannot make it work. I just get a spinning cursor when trying to browse my Mac with ssh.

Can anyone help this relative newb to ubuntu, gnome, and debian?

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=secundar]Hi, I'm looking for a way to connect to a local server to edit files - on the server - without copying them to my laptop. I tried samba, and it works, but I cannot seem to access the share from within my application (File->Open...). Nothing is listed in /mnt and I'm not sure where else to look.

I read that using ssh to connect makes it seem like the server is actually local but i cannot make it work. I just get a spinning cursor when trying to browse my Mac with ssh.

Can anyone help this relative newb to ubuntu, gnome, and debian?[/QUOTE]
 To connect to server via ssh/sftp, the server must be running the ssh server. If your Mac is not running it, you would not be able to connect to it via ssh. Sorry, I have no Macs, so I do not know how to configure it to run ssh server.

---

### Post by secundar on 2005-05-26
Thanks, but the Mac is running ssh. I can ssh to it using the terminal in ubuntu but the  "Connect to Server" is what seems to timeout. I just get an empty window and a spinning cursor.

---

### Post by shakin on 2005-05-26
[QUOTE=secundar]Thanks, but the Mac is running ssh. I can ssh to it using the terminal in ubuntu but the  "Connect to Server" is what seems to timeout. I just get an empty window and a spinning cursor.[/QUOTE]

Perhaps Macs don't support SFTP, which I think is what Connect to Server uses. OpenSSH supports SFTP.

---

