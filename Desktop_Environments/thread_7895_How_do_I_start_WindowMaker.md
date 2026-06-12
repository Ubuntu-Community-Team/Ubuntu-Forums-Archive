---
title: "How do I start WindowMaker?"
date: 2004-12-12
forum: Desktop Environments
---

### Post by sonetti on 2004-12-12
Installed WindowMaker-0.91.0 (no problems with the installation)  I can't figure out how to start the program, it doesn't appear under applications, nor as a session option when I logon.

I opened xterm and ran this command "sudo startx wmaker" which installed a folder "GNU.step for the current user" in my home directory, but I still can't figure out how to start WindowMaker.  ....mostly I get "server for display already active".  Any advice appreciated.

---

### Post by heruwdp on 2004-12-12
hello,

create a file and named it windowmaker.desktop
place that configuration to your /usr/share/xsession

[Desktop Entry]
Encoding=UTF-8
# Custom entry 
Name=windowmaker
Comment=Finally
Exec=windowmaker
Icon=
Type=Application

after that, you can login to your windowmaker from session options
hope this help
:)

---

### Post by sonetti on 2004-12-12
thanks heruwdp, yes it did help, bigtime! .... now I can start windowmaker at login, another bonus, when I sign-out of windowmaker there's an option to start other windows managers, icewm, blackbox, etc ..... many thanks for the help.

---

### Post by maxim_86ualb2 on 2005-01-03
how can I get this working for blackbox I am still a newb at this....

---

