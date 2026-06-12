---
title: "FreeNX remoting into a Windows box"
date: 2008-10-09
forum: Desktop Environments
---

### Post by rstaylor on 2008-10-09
I am having trouble remoting from Ubuntu into Windows using FreeNX (nxserver and client).  I can get a connection and enter credentials.  However as the desktop environment begins to paint I get an error:  
The System cannot find the path specified.
This initial program cannot be started:  /usr/lib/nx/nxdesktop_helper

I have located this file in the Ubuntu server. It is owned by root and has the following permissions rwxr-xr-x.

It appears to me that this is trying to run this as a program ON the windows box as part of the login.  Of course this path does not exist in Windows.

The other thing that supports this theory is that if a user session is already logged in on the Windows machine everything works.

Any suggestions would be appreciated.

Rich Taylor

---

### Post by Jack005 on 2008-10-16
I have the same problem. To get around it, I ran "RDESKTOP" locally on the server to the remote WinXP box.
 
      sudo /usr/bin/rdesktop -f 192.168.x.x

Once I get the signon prompt I enter the user id then I signed off. For some reason that fixed the problem for this particular user and I was able to use FreeNX with this user after. I'm still investigating. Hope this will help.

running Hardy, FreeNX 3.2.0

---

### Post by gerni on 2008-11-08
I've exactly the same problem - the solution from Jack005 works for me, but this helps only for the current session. This is really annoying. Has anybody found a solution?

---

