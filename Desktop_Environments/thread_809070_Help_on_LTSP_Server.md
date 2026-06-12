---
title: "Help on LTSP Server"
date: 2008-05-27
forum: Desktop Environments
---

### Post by sjude on 2008-05-27
I love ubuntu Desktop and I have installed within Windows on 3 computers.  I also setup the ltsp-server-standalone on 2 computers with thin clients connected to it for testing purposes.

The thin clients connect to the server without any problems.

Now I want do the same on a freshly formated HDD without windows on it.  I did the following.

On a P4 machine with a 40GB HDD and no CD rom drive, I connected a USB CDrom drive and installed the Desktop version of ubuntu.

Then with the command 
sudo apt-get install ltsp-server-standalone openssh-server

I got the server installed.  Then with the command
sudo ltsp-build-client
to create the client, I get error at the end after all the downloading of files from the Internet.

I have done this many times but after all the downloading it gives errors at the end.

Firstly, can I build-client without an Internet connection.
Is it possible to transfer the installation from the windows computer to the computer without windows.

I spend a lot of time and Internet downloads to get the LTSP Server working - still not working.

Everytime the ltsp-build-client fails I have to delete the /opt/ltsp/i386 directory to start again.  How to backup the downloaded files and use it in apt-get install ltsp-build-client process.

I have downloaded almost all the CDs - desktop, alternate, server and also addon for ubuntu 8

---

### Post by Vince-0 on 2008-06-02
You can do " ltsp-build-client file:///cdrom " with your alternate cd in the cd drive to load the client environment from the CD rather than from the ubuntu repositories.

There is also an option for different architectures eg: -arch i386 

:-)

---

### Post by sjude on 2008-06-02
> **Vince-0 said:**
> You can do " ltsp-build-client file:///cdrom " with your alternate cd in the cd drive to load the client environment from the CD rather than from the ubuntu repositories.

There is also an option for different architectures eg: -arch i386 

:-)

Thankyou.  I solved the problem and got the client build successfully.

---

### Post by Vince-0 on 2008-06-04
Just to clarify - some of the options are:

--mirror file:///cdrom   (to use cdrom files and not internet repos)
--arch i386              (change i386 to amd64 etc)
--kiosk    (kiosk mode for internet cafe type set up with easy login etc)

:guitar:

---

