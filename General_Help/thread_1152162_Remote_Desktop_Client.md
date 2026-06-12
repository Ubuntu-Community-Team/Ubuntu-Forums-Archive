---
title: "Remote Desktop Client"
date: 2009-05-07
forum: General Help
---

### Post by amadeus266 on 2009-05-07
I use my Ubuntu Laptop at work and connect to a Windows 2003 terminal server with Remote desktop client. There are idle time settings on the server and when the time is up, Remote desktop client says "an error has occurred" and will reconnect in 30 seconds. How do I stop this behavior? If I have been away from my TS session for more than 15 minutes, the session is supposed to close. This is the policy at work. I come back after say 20 minutes and the session is restarted showing my user name and waiting for my password. The network policies also dictate that the server is NOT supposed to show the last logged in user and is set up correctly on the server end. This also needs to be changed. B.T.W. I refuse to go back to Vista on this laptop. It has been nothing but trouble.

---

### Post by Brandon Williams on 2009-05-07
Are you using 'Terminal Server Client' (tsclient)? Or are you running rdesktop on from the command line? I can't remember if the restart behavior you describe is a feature of tsclient or rdesktop.

If you are running tsclient, with runs rdesktop for you, try running rdesktop directly from the command line.

---

### Post by amadeus266 on 2009-05-13
> **Brandon Williams said:**
> Are you using 'Terminal Server Client' (tsclient)? Or are you running rdesktop on from the command line? I can't remember if the restart behavior you describe is a feature of tsclient or rdesktop.

If you are running tsclient, with runs rdesktop for you, try running rdesktop directly from the command line.

I haven't used rdesktop since Mandrake 9.1 but I think I can remember how to set it up. Thanks

---

### Post by XCan on 2009-05-13
It would be really good to have an option in the gui to remove the reconnect behaviour. I've more than once stumbled upon the scenario where I'm sitting physically at a machine and my ubuntu box, which was connected to the windows machine, kept kicking me out every 30 seconds.

PS. I do know that removing the password in tsclient would stop it from automatically logging in, but that's not the point here. :)

---

### Post by amadeus266 on 2009-06-03
I don't save my passwords so that isn't an issue. I did find a workaround... I installed grdesktop. It doesn't have as many features but also doesn't have the reconnect problem.

---

