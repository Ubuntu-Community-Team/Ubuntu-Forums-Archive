---
title: "Setting up SSH access"
date: 2012-05-25
forum: Desktop Environments
---

### Post by JspPeterson on 2012-05-25
Hello, I have installed SSH-openserver on a ubuntu desktop. I forwarded in my router correctly and all that stuff. I try to connect, and no matter what, I always get a "Permission Denied" error when I type my password in. Any help? Or is there a way i can temporarily remove all passwords. I can't even connect if I try to connect from the machine itself.

---

### Post by papibe on 2012-05-25
Hi JspPeterson.

Is it working from another machine in your LAN using just its short hostname?

Are you trying to access it using a public IP or dynamic name from outside your network?

Regards.

---

### Post by QIII on 2012-05-25
Regardless of where you are trying to connect from, if you are using an SSH with password setup (not your normal Ubuntu session log in, that's different), you should not.  Alter your config file so you are not using an SSH password but a public/private key combination, SSH 2.  OpenSSH supports a 4096 bit key.  Someone attempting a brute force attack would probably be still trying after the sun burns out.

I'm on my cell right now and can't add links, but there are a couple of very good Ubuntu Community wikis that might be very helpful.

---

### Post by JspPeterson on 2012-05-26
> **papibe said:**
> Hi JspPeterson.

Is it working from another machine in your LAN using just its short hostname?

Are you trying to access it using a public IP or dynamic name from outside your network?

Regards.

It is not working with any. I can't even connect from the machine hosting it itself.

And I am not familiar at all with SSH config, so QIII, could you post me a simple config file or tell me what to alter in it? Using the normal ubuntu login would be fine but I have no idea how to set it up.

---

### Post by papibe on 2012-05-26
Using the triple verbose options can give us some clues.

Could you post the result of this command from the machine itself?
```
ssh -vvv localhost
```
Regards.

---

### Post by QIII on 2012-05-26
A lot of links.  Look at #2 in the right hand column for some basic tips.

[Configure OpenSSH](https://help.ubuntu.com/community/ssh/openssh/reconfiguring/)

Some of those have basic troubleshooting help.

But run with Papibe's request because it will probably help to significant narrow the search for a resolution.

---

