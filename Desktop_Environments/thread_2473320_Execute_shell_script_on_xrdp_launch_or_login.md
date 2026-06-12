---
title: "Execute shell script on xrdp launch or login"
date: 2022-03-31
forum: Desktop Environments
---

### Post by sb2022 on 2022-03-31
Is there a way to run a script when xrdp launches the login window or on xrdp login?

The script can be placed in the right location with ansible but I can't find a way to run it to do what the script does.

The script itself is simply capturing $DISPLAY environment variable to a file.

Don't ask me why we need that variable, it's a long story. We just need to capture that variable when there is a desktop and the reliable way to get it is to get the operator of ansible to xrdp login.

---

### Post by him610 on 2022-03-31
> when xrdp launches the login window
I guess that means you are not using ssh to access your remote machine. If you were, I might be able to give you some advice. I have all of my remote devices running a script when I logon using ssh.

Maybe someone else can help you. Good luck.

---

### Post by ActionParsnip on 2022-04-01
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve?
What does the script do?

---

### Post by sb2022 on 2022-04-01
We need the desktop session to get the $DISPLAY env var. That is required for an app running in docker with X11 forwarding. 

The container is run by Azure IoT Edge Agent and so we don't have a lot of control. We can place the Host env vars in a file mount and have the container read its env vars on run.

Beyond all of that, is there a way to run a script on xrdp login. Simple question.

---

### Post by sb2022 on 2022-04-01
How do you attach the script. I need an active rdp session to capture DISPLAY variable so, not SSH. But I can try doing the same you do and see if that works. Please let me know.

---

### Post by ActionParsnip on 2022-04-01
> **sb2022 said:**
> We need the desktop session to get the $DISPLAY env var. That is required for an app running in docker with X11 forwarding. 

The container is run by Azure IoT Edge Agent and so we don't have a lot of control. We can place the Host env vars in a file mount and have the container read its env vars on run.

Beyond all of that, is there a way to run a script on xrdp login. Simple question.

What do you do on the desktop when you get connected via RDP? What is the purpose of connecting to the system in this way?

---

