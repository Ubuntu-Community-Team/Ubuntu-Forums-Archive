---
title: "Trying to get Novell Iprint to work on Ubuntu??"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Georgie-o on 2007-04-26
Has anyone had any luck with this?  I downloaded the Novell client, used alien to convert to a .deb and then installed.  I can't figure out what to do from here to get the gui or interface to run.

---

### Post by Road King on 2007-05-10
In the Systems menu, under Preferences -> Sessions, and for StartUp Programs, add a new startup program with Name: Novell iPrint Listener and for Command: /opt/novell/iprint/bin/iprint-gnome-init

In your .profile, add these lines:

```

# if iprint installed, add it to PATH and MANPATH
if [ -f /etc/profile.d/novell-iprint.sh ]; then
        . /etc/profile.d/novell-iprint.sh
fi

```

There's also a link missing for Firefox to find the plugin.
cd to /usr/lib/firefox/plugins/ and enter this command:

```

ln -s /opt/novell/iprint/plugin/npnipp.so

```

This should get you to the point you can go to:

[http://iprint.your.domain/ipp](http://iprint.your.domain/ipp)

and install a printer.  

I still haven't gotten authentication to work printing from applications, but it works using iprntcmd at the command line.

Hope this helps some.

---

### Post by rorzer on 2007-05-29
Hi,  thanks for the info.  I've managed to install a printer from my university's iprint server, and progammes queue the print jobs to my localhost cups server correctly, but the jobs are not sent to the remote iprint server.  

The cups printer gui says that the job status is "Paused: job-hold-until-specified".

This guy here [http://groups.google.co.nz/group/novell.support.iprint/browse_thread/thread/d5a9cab51bce0156/9d82e95e642793aa%239d82e95e642793aa]("http://groups.google.co.nz/group/novell.support.iprint/browse_thread/thread/d5a9cab51bce0156/9d82e95e642793aa%239d82e95e642793aa")
seems to be having the same problem.

Any clues?

Rorzer

---

### Post by seffius on 2007-08-29
Hello!  To add on to this, I followed the instructions posted above but Firefox refused to load the iPrint plugin (I checked via [http://about:plugins](http://about:plugins)).  The Novell iPrint Listener refused to start because it complained about missing libglitz?  I ended up having to install lib-glitz by running:
```

apt-get install libglitz-glx1

```
Then the Firefox plugin worked!

---

