---
title: "Choosing a port for AutoOrtho for XPlane"
date: 2023-09-21
forum: Gaming &amp; Leisure
---

### Post by SciGuy1872 on 2023-09-21
Hi.  When trying to run the AO/XP combination and check the Log.txt after the crash, I find a line that says there was an error 5; Socket already occupied.  I was told by someone that AO has the default port of 5000 and that changing this in .autoorth.conf might fix this error.  Since I have never really messed with ports, I thought I would ask here about the port number I should replace in the file.  I have Ubuntu Mate 22.04.
```
  sudo netstat -ntlp | grep LISTEN  

    
  tcp        0      0 127.0.0.1:27060         0.0.0.0:*               LISTEN      3439/steam          
tcp        0      0 127.0.0.1:41401         0.0.0.0:*               LISTEN      3439/steam          
tcp        0      0 0.0.0.0:27036           0.0.0.0:*                 LISTEN      3439/steam          
tcp        0      0 127.0.0.1:631           0.0.0.0:*                 LISTEN      5855/cupsd          
tcp        0      0 127.0.0.53:53           0.0.0.0:*                 LISTEN      981/systemd-resolve
tcp        0      0 127.0.0.1:57343         0.0.0.0:*               LISTEN      3439/steam          
tcp        0      0 127.0.0.1:37869         0.0.0.0:*               LISTEN      3439/steam          
tcp6       0      0 ::1:631                 :::*                              LISTEN      5855/cupsd  
 

```

---

### Post by SciGuy1872 on 2023-09-22
Hi.  I tried to run the sim, but got the same error 5: 
  0:00:34.475 E/NET: (RakNet) Init: Failed to start RakPeerInterface, error was 5 (SOCKET_PORT_ALREADY_IN_USE)! 
    
  On this attempt, I edited the authoortho to be web ui port 27060 

 [INDENT]     [ ]("https://forums.x-plane.org/index.php?/forums/topic/294343-autoortho-use-log-says-error-5-socket_port_already_in_use/#")     Quote  
When you want to create a new file system on Windows, other than FAT or NTFS,
you need to develop a file system driver. Developing a device driver that works
in kernel mode on windows is extremely technical. By using Dokan, you can create
your own file systems very easily without writing device drivers. Dokan is
similar to FUSE (Linux file system in user space) but works on Windows. 

  

 
 [/INDENT]  This bit of info seems to indicate that Dokan is for Windows--I have  Ubuntu Mate; do I need it?  What else should I try to get the AO/XP  combination working?

---

