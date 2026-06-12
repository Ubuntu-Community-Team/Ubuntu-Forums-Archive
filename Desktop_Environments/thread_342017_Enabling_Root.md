---
title: "Enabling Root"
date: 2007-01-19
forum: Desktop Environments
---

### Post by infinitezero on 2007-01-19
I have tried to enable root without any success, gmd or kdm will not start. Is there another was to enable root for a graphical login?


iz

](*,)

---

### Post by taurus on 2007-01-19
Why don't you use sudo if you need to configure something.  Any reason why you need to log in as root?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mcduck on 2007-01-19
logging in to desktop as root is just about the worst possible thing to do.. Why do you want to do that?

---

### Post by infinitezero on 2007-01-19
I would like to just have a root (super user) file manager so I can just drop file where I need across user accounts. If that could be done I would be happy, I don't always feel like using a terminal.

---

### Post by taurus on 2007-01-19
<Alt>F2 -> gksudo nautilus

---

### Post by NESFreak on 2007-01-19
> **taurus said:**
> Why don't you use sudo if you need to configure something.  Any reason why you need to log in as root?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

this link also contains the info on how to enable graphical root login.
> In Gnome

    *

      Open System --> Administration --> Login Screen Setup
    *

      Click on the security tab
    *

      Check Allow root login

In KDE

    *

      Open Konqueror and open the /etc/kde3/kdm/ folder
    *

      Right click the kdmrc file and then Actions --> 'Edit as root'
    *

      On line 246 should be AllowRootLogin=false change it to 'true'
    *

      Save and exit.

even though a graphical root login is EVIL. I thing that whenever somebody asks for it you should warn him, but still give him the information. He might have a good reason for it. And the forums are here to give him the information.

NESFreak

---

### Post by infinitezero on 2007-01-19
You DA MAN!!!

Coming from the SuSE side of things this no root is killing me.


Once again thank you.


iz

---

