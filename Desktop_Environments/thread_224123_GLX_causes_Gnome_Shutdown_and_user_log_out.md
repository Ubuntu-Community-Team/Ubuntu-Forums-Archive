---
title: "GLX causes Gnome Shutdown and user log out"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Ted_Smith on 2006-07-27
Hi

Whenever I try to execute glxgears, glxinfo or view the GLX settings from 'Applications' --> 'System Tools' --> 'NVidia XServer Settings' Gnome shuts down, logs me out and reloads and I land at the login prompt of Gnome. 

I'm not sure what has gone wrong? How can I fix this? 

Thanks

Ted

---

### Post by Ted_Smith on 2006-08-23
This is till happening, and I noticed it crashes out totally if I try to select a screensaver. 

I'd really appreciate some guidance on how to troubleshoot this.

---

### Post by -deadcats on 2006-08-23
You might try seeing what the output of typing glxinfo into Terminal says...

regards,
-dc

---

### Post by Ted_Smith on 2006-08-25
Thanks, but as per original post, executing any such app causes the problem of the GNOME logout or X-Org crash, so I can't capture the output to determine what is going wrong.

---

### Post by ese5 on 2006-09-02
Was having the same problem myself.  Simply reinstalling the linux drivers from nvidia fixed it in my case.

---

