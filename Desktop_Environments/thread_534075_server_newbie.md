---
title: "server newbie"
date: 2007-08-24
forum: Desktop Environments
---

### Post by Jagged on 2007-08-24
i have no experience in running a server whatsoever, but have fallen in love with linux. i want to learn to create servers. where is a good place to start. i have a desktop just waiting to do something...and it does kinda suck that i just have dial up internet. i also have a laptop running windows vista and a mac running osx panther networked to this computer using two network adapters in the desktop....any ideas?

---

### Post by solar george on 2007-08-25
What type of server,

Web
Print 
Ftp
ect.

---

### Post by mojoman on 2007-08-25
> **Jagged said:**
> i have no experience in running a server whatsoever, but have fallen in love with linux. i want to learn to create servers. where is a good place to start. i have a desktop just waiting to do something...and it does kinda suck that i just have dial up internet. i also have a laptop running windows vista and a mac running osx panther networked to this computer using two network adapters in the desktop....any ideas?

Well, if you use dial-up I suppose web and mail server is useless for you but you could set it up as an ftp-server for internal use. Basically, it would be an extra HDD. That way you could log into it from the other computers (using an ftp-client) and, when connected to the net other could log in as well. You could use it as print server but to me it seems to be a waste of a perfectly good computer, as many routers can perform this service. Perhaps you can use it as both an ftp-server and, if you have a printer, as a print-server as well.

---

### Post by Jagged on 2007-08-25
i like the ftp and print server idea....at some point i want to get a wireless hub...then i can load stuff to the laptop and print without plugging it in all the time:)  now to figure out how to configure a ftp server...oh, i'm using ubuntu desktop edgy presently

---

### Post by solar george on 2007-08-25
> Well, if you use dial-up I suppose web and mail server is useless for you but you could set it up as an ftp-server for internal use. Basically, it would be an extra HDD.

You could still set up a webserver for testing sites and mucking about with web apps on your local network.

As for an ftp server I would advise you just to install the openssh-server and use sftp or scp to access it (ssh encoded ftp).

---

