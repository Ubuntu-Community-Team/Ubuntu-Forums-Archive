---
title: "Change terminal text color based on IP adress"
date: 2009-04-18
forum: General Help
---

### Post by tengblad on 2009-04-18
Hello y'all, I have a problem I hope you can help me with!

At work we have a multitude of different environments - several test environments as well as multiple live environments. To reduce the chance of accidentally doing something in a live environment when I really should've been messing about on one of the test ones, I would like to set up bash so that the text/background color of my shell session changes depending what IP I've ssh:ed into. One selection of colors for 10.0.x.x, another for 10.1.xx, yet another for 10.2.x.x and so on. I've been looking for a way to do this, but I've not been able to find a good solution. 

Does anyone have any suggestions?

---

### Post by Brucevdk on 2009-04-19
If you're using GNOME Terminal I'd probably go with different profiles and then have some helper script to launch terminals by having a list of IPs/hostnames associated with a particular profile. That way you could do something like: 

```

launch-terminal ubuntuforums.org

```

Here's the command to launch a gnome-terminal with a particular profile and connect to the host using SSH.

```

gnome-terminal --window-with-profile=$PROFILE -e "ssh $REMOTEHOST -t '$SHELL'"

```

If you don't want to launch a new window but have a tab open instead you'll have to patch gnome-terminal, see: [http://bugzilla.gnome.org/show_bug.cgi?id=83203](http://bugzilla.gnome.org/show_bug.cgi?id=83203)

If you're not using GNOME Terminal you could probably still do something similar.

Others prefer something like SSHMenu or the GNOME Terminal Launcher.

---

