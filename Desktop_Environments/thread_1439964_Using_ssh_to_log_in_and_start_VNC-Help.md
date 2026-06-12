---
title: "Using ssh to log in and start VNC-Help"
date: 2010-03-26
forum: Desktop Environments
---

### Post by Tsquad on 2010-03-26
Hello, im running ubuntu 8.10 on an old desktop pc of mine as a server. I have ventrilo and an ssh sftp server set up. I originally did all this through vnc. My problem is that it is headless, i had a power outage at my house and i cant log into the pc to start my server services because my vnc software has not yet started as i have not been able to log back in. 

Id really rather not bring a mouse/keyboard/monitor over to it. Because i have SSH set up, and have been able to log onto the ssh part of it(i dont know ssh to much except for the ftp), im wondering if i can log the pc into the desktop so it would start the vnc sfotware from my ssh connection.

---

### Post by asmoore82 on 2010-03-26
Check out the Howto in my signature.

---

### Post by Tsquad on 2010-03-29
Thanks for the reply, but that guide says that you need to be running 9.10 or above and im running 8.10. will this be a problem? Im guessing so.

---

### Post by asmoore82 on 2010-03-29
You might not be able to do the Upstart job part.
But you could use a very similar setup and ssh in and run the vncserver command manually.

---

### Post by Tsquad on 2010-04-23
> **asmoore82 said:**
> You might not be able to do the Upstart job part.
But you could use a very similar setup and ssh in and run the vncserver command manually.

Can someone explain this a little more? It sounds like this will do what i need but im not exactly sure how to acomplish it.

When i log into my box using putty ssh, does that put me at the terminal command line? and from there i can execute some sort of start vncserver command? 

My server has been out of action for a while now and id like to get it back up and running(and producing more heat in my room xD

---

