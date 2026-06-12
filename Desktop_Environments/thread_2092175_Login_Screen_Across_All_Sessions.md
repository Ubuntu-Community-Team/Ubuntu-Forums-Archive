---
title: "Login Screen Across All Sessions"
date: 2012-12-07
forum: Desktop Environments
---

### Post by Corelogik on 2012-12-07
I have Ubuntu 12.04 running fine with Cinnamon desktop. Recently I installed MDM window manager to try it out, discovered I didn't like and went back to lightDM.

Everything went fine until reboot, I still got the MDM login screen. I ended up having to edit lightdm.conf to reset to the unity greeter login screen.

This is what I had to change it to;
```

[SeatDefaults]
user-session=cinnamon
greeter-session=unity-greeter

```

Now login screen is restored but I am left with a couple of questions. I have regular Ubuntu, Gnome Shell and Cinnamon installed. Along with all their 2D versions.

1.) Will my edit work across all sessions if I decide to change again, or is that only going to work for Cinnamon?

2.) If the login is just for Cinnamon, how would I set it for all sessions? What would I need to put in for "user-session"?

I realize I could test this myself by simply logging out and choosing a new session, but I prefer to not interrupt my work to do that. Also, that wouldn't help with figuring out what to put in for "user-session" if I need to do something else.

Thank you in advance for your input and advice.

---

### Post by zombifier25 on 2012-12-07
The session is started by the login manager, not vice versa, so yes for 1 and no need for 2.
(also, the user-session config in lightdm.conf sets the default session for newly created users on the system)

But I'm rather curious. How did you revert back to LightDM without running
```
sudo dpkg-reconfigure lightdm
```
Dismiss this if you DID run the command.

It's probably important that you log out later to check that you did in fact revert the login manager back to LightDM.

---

### Post by Corelogik on 2012-12-07
> **zombifier25 said:**
> The session is started by the login manager, not vice versa, so yes for 1 and no need for 2.
(also, the user-session config in lightdm.conf sets the default session for newly created users on the system)

But I'm rather curious. How did you revert back to LightDM without running
```
sudo dpkg-reconfigure lightdm
```
Dismiss this if you DID run the command.

It's probably important that you log out later to check that you did in fact revert the login manager back to LightDM.

I did run ```
sudo dpkg-reconfigure lightdm
``` and then logged out and back in a couple of times. Even one complete reboot. However it kept dumping me into the login screen from MDM until I edited the conf file. Any how, as long as it will use lightDM from here on out if I change the DE at login, I guess I'm good.

I'm going to assume from your post that ```
sudo dpkg-reconfigure lightdm
``` SHOULD, take care of it and all I need to do after is a relog or reboot. At least I know how to fix it if I end up stuck again.

TYVM!

---

