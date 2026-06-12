---
title: "Need help to install GUI on new ubuntu server 9.04"
date: 2009-07-01
forum: Desktop Environments
---

### Post by JohnyBoy123 on 2009-07-01
Hi Friends,      I need help in installing and get RDP of GUI of new ubuntu server 9.04.      The situation is I have a website that is using air application, and I have new ubuntu server. Now I need to get that site running on new ubuntu server.     problem is Ubuntu server dont have GUI and I need GUI to install air application.  I've installed all other required software for site running but untill I get the GUI interface i cant install the air application.   I've installed the ubuntu-desktop on server and tried to run the GUI through different options like ssh tunnel, vncviewer, vpn, etc....  but all are having problems at some stage , may be I m missing some steps.    My purpose is to install GUI correctly on ubuntu server and get access to that GUI.  I have ubuntu client version is installed in my local pc and also have windows xp installed in local pc.  But not sure which is the best way to install the GUI on server and get the RDP of server GUI.   I can roll back all the installation on server and can start from fresh installation on server , but need some guidance.   Please help me by guiding the best way to do this.   Thanks a lot  in advance.

---

### Post by hetx on 2009-07-01
If I'm not misunderstanding the question you just need to start up the GUI first with start x =)

---

### Post by JohnyBoy123 on 2009-07-01
Hi Hetx,    Thanks for quick reply.  But as I understand we can initiate GUI using this command only if we have physical access to server , i mean using terminal on server itself.  But I m accessing server through ssh using putty and other ssh clients. when I use this command it show error that cant start GUI,  \dev\tty0 file not found and some other errors . please guide me if I m wrong.

---

### Post by hetx on 2009-07-01
Seems you don't even need to install the desktop for that. According to this thread

[http://ubuntuforums.org/showthread.php?t=258961](http://ubuntuforums.org/showthread.php?t=258961)

the VNC server should handle it for you. Make sure it is started.

---

### Post by JohnyBoy123 on 2009-07-01
Hi Hetx,  vnc worked , I've installed vnc4server and did vncviewer on my local ubuntu and it started the rdp , but its only showing 3 checkboxes on screen and nothing else i dont understand how to proceed , i can check or uncheck those options through mouse but what next ? how to proceed? any idea?

---

### Post by JohnyBoy123 on 2009-07-01
I've installed ubuntu-desktop and now i can see comand terminal in rdp. 
 but when I type startx its shows following error. Is this becuase server may be not having display card? or anything else? 

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)

 giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

---

### Post by ezacon on 2009-07-04
i use nomachine nx server. it is the simplest and moore eficient protocol to remote x.
[http://www.nomachine.com/](http://www.nomachine.com/)
they have linux and windows clients

---

