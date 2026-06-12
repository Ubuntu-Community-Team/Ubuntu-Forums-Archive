---
title: "How to Setup Online File Storage?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by mbmccormick on 2005-11-30
How do I set up my personal file storage from my Ubuntu machine? I know it needs a connection, and always on, but where do I go from there? What do I do?

---

### Post by anil_robo on 2005-11-30
DO you mean how to set up FTP from Ubuntu? If that is the case, try to find some info on forums about FTP and you'll be done. If not, please try to post specific problems so that others can know what is it that you're talking about exactly.

---

### Post by anil_robo on 2005-12-05
1. Make sure you have purchased a domain name, and some webspace.
2. Login to your domain/webspace and create an ftp account for yourself, if one doesn't exist already
3. Note down the ftp path (e.g. ftp.yoursite.com)
4. First, check the ftp path is working : Open firefox, and type the ftp path there, and press enter. Firefox should ask you the ftp username and password. Enter username and password to get into your ftp area. If all goes well, it means your ftp account is working.
5. Now close firefox, and click Places--> COnnect to server 
6. Enter the particulars of your account
    (e.g. service type: ftp with login - if you enter username and password
      server name: the ftp address you entered in firefox
      leave port empty if you don't know which port
      folder: try leaving empty at first. If it doesn't work, try httpdocs. If that too doestn't work, call / email your webspace provider
      Name used for connection: Type in any name e.g. "my online storage")
7. Click connect
8. A new folder named "my online storage" or the name you entered for the network will be formed on your desktop.
9. Double click on this folder - it should ask you for password (if you set ftp with login)
10. Enter the password, and you shall see your files in Nautilus
11. To send files to your ftp account, simply drag and drop them on this desktop folder.

Hope it helps. If it doesn't please post so that I can find some other way for you. Have a great day!

---

### Post by mal on 2005-12-05
This would be a pretty good way to store files for people who need to work on computers in different locations (like me).

However, what about security?  I guess it would not be very safe to leave sensitive information in an unsecured webspace.  Would it be possible to set up an encrypted file system that could be accessed through ftp?

Any comments welcome.

Mal

---

