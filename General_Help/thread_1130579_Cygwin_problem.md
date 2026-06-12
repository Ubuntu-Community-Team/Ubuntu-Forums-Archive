---
title: "Cygwin problem"
date: 2009-04-19
forum: General Help
---

### Post by runnner on 2009-04-19
I installed Cygwin on my Windows PC to remote access a ubuntu server.

After Cygwin install finished, I clicked the cygwin icon on the desktop to run it. I first ran "startxwin.bat" to start X window.
A window with a X icon on the top left title bar appeared, it seemed it was the X window, I am not sure for I am new to Cygwin.

I then typed "ssh -X root@remote_IP_here" in the new X window, and got error:
Warning: untrusted X11 fowarding setup failed. xauth key data not generated

Warning:No xauth data; using fake authentication data for X11 fowarding

However, if I typed "ssh -X root@remote_IP_here" in the Cygwin's command line window  not in the new opened X windwo, the connection is ok.

Where is wrong and how could I work around this problem? Thank you!

---

### Post by runnner on 2009-04-21
Who could tell me where is wrong? Thanks!

---

