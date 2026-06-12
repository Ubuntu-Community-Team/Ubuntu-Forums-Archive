---
title: "Windows remote access..?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by FynitE! on 2006-09-30
Up until now, ive used windows to access my windows server.

I'd like to be able to do it through ubuntu, too though.


So what is the best remote access program that will let my control my WINDOWS XP server desktop?

---

### Post by mitch.c on 2006-09-30
> **FynitE! said:**
> So what is the best remote access program that will let my control my WINDOWS XP server desktop?

Terminal Server Client comes installed by default.
Applications -> Internet -> Terminal Server Client.

I use it all the time... works fine.

---

### Post by FynitE! on 2006-09-30
What would I need to install onto my windows server for that to be able to access it though? 

Thanks

---

### Post by FynitE! on 2006-09-30
I tried to connect to it, and im getting this error:

VNC connection failed: No configured security type is supported by 3.3 viewer.



(Im using VNC as VNC server is already installed on the server, its what i used to use)

---

### Post by mitch.c on 2006-09-30
> **FynitE! said:**
> I tried to connect to it, and im getting this error:

VNC connection failed: No configured security type is supported by 3.3 viewer.

(Im using VNC as VNC server is already installed on the server, its what i used to use)

Why don't you just use remote desktop (RDP). It's built in to Win XP.
[LIST=1]
[*]Right click **My Computer**
[*]Click **Properties**
[*]Select the **Remote** tab
[*]Enable **Allow users to connect remotely to this computer**
[*]Click **Select Remote Users** (members of Administrators group are enabled by default)
[/LIST]
Then when you connect using tsclient from ubuntu, select an RDP protocol. VNC should work as well, but since I don't have it loaded, so I can't troubleshoot.

---

### Post by FynitE! on 2006-10-01
Thank you.

---

