---
title: "Remote login from Xubuntu"
date: 2007-02-26
forum: Desktop Environments
---

### Post by plumstead21 on 2007-02-26
I have Ubuntu on my main machine and Xubuntu on a clapped-out laptop (both are Edgy) and want to set up remote login from the laptop to the main box.  Looking around it seems that XDMCP is an easy way to do this.  I have set up the main box to accept remote logins as per the [instructions on the wiki]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/RemoteAccess").  Only trouble is I can't work out how to log in from the Xubuntu machine - the instructions on the wiki are geared up to the Ubuntu login screen, which does indeed have the Options menu at bottom left, but there doesn't seem to be an equivalent on the Xubuntu login screen.  How do I login to the remote machine (from the terminal if necessary) ?

I expect I'm being really dim as I can't find this mentioned anywhere else on the forums.  Could anyone please enlighten me?  Thanks :)

---

### Post by maxamillion on 2007-02-26
Command line remote login: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server) (encrypted and secure)

GUI remote login: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access) (two alternatives and neither are secure)

---

### Post by plumstead21 on 2007-02-26
Thanks - I've got SSH up and running, which is useful, but it would be nice to get into the GUI so I can use the more heavy-duty apps that are on the big machine.  As I understand it this can't be done via SSH - is this right? That's why I was keen on going via XDMCP.  The page you linked to is the same one I found, and there's no instructions on how to get it working on a Xubuntu client.

---

### Post by bobpaul on 2007-03-05
```
username@laptop: $ ssh -X username@desktop
Password:
username@desktop: $ gcalctool
```

The "-X" is for X11 forwarding. The calculator will launch and the GUI for the calc will display on your laptop. Look over "man ssh" for more details.

This isn't the same as xdmcp, but it will let you quickly tunnel and run single apps off your desktop, and it's secure.

---

### Post by plumstead21 on 2007-03-05
Great, many thanks for the advice.  And typing gnome-session when logged in via SSH does the trick for extended use of GUI.

---

