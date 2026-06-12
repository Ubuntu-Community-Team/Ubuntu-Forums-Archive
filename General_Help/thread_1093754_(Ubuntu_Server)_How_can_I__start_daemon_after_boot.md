---
title: "(Ubuntu Server) How can I  start daemon after boot?"
date: 2009-03-11
forum: General Help
---

### Post by c3lica on 2009-03-11
Ok, So i am running Ubuntu Server and would like to have transmission-daemon start automatically after the computer boots up. I do not want it to run as root so rc.local won't work. I would like it to run under my username.

Any ideas?

---

### Post by Ocxic on 2009-03-11
just add it to your start-up applications under: System->Preferences->Session

---

### Post by c3lica on 2009-03-12
I have no GUI... and thus no System->Preferences->Session. It is basically a headless server that I ssh into and control everything from the command line interface. 

Any other ideas?

---

### Post by KayakJim on 2009-03-12
If it has a startup script you could place it in the /etc/init.d/ directory.

---

### Post by c3lica on 2009-03-12
> **KayakJim said:**
> If it has a startup script you could place it in the /etc/init.d/ directory.

Ok, I used the startup script from here [http://trac.transmissionbt.com/wiki/Scripts/initd]("http://trac.transmissionbt.com/wiki/Scripts/initd") but did not have the right permissions to the /var/run/ directory so I changed the PIDFILE=/var/run/$NAME.pid directory to one that I do have permission to. 

When I run this command it starts up fine but it does not start up when the computer boots up. 

```
/etc/init.d/transmission-daemon start
```

Any ideas?

---

### Post by kryptikos on 2009-03-12
> **c3lica said:**
> Ok, So i am running Ubuntu Server and would like to have transmission-daemon start automatically after the computer boots up. I do not want it to run as root so rc.local won't work. I would like it to run under my username.

Any ideas?

You can still use rc.local. You can tell root to switch users to run the daemon under. I give a quick example in this thread :)

[http://ubuntuforums.org/showthread.php?t=1092216]("http://ubuntuforums.org/showthread.php?t=1092216")

---

### Post by c3lica on 2009-03-12
Thanks, that was very simple... I added this to my rc.local and it starts up just like i like this as the correct user.

```
su jon -c transmission-daemon
```

I didn't end up needing the startup script.

Thanks again.

---

### Post by kryptikos on 2009-03-19
No worries, happy to help :)

---

