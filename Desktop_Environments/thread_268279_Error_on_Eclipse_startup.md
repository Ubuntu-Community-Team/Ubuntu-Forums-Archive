---
title: "Error on Eclipse startup"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Ev.Eli on 2006-09-29
I managed to break my Eclipse setup. I needed the web tools, so I downloaded the package for it and foolishly extracted it into /usr/lib/eclipse. It turns out I had downloaded the wrong package and gotten one containing a full Eclipse 3.2 installation. It didn't start. So I uninstalled all my eclipse related packages, did an rm /usr/lib/eclipse -rf, deleted my .eclipse folder and reinstalled. Unfortunately, there must be some traces of that tarball left on my system, because Eclipse still won't start. How can I fix my Eclipse? Log can be found at [http://syclone.dyndns.tv/host/eclipse.log]("http://syclone.dyndns.tv/host/eclipse.log") because the attachment system seems to be broken for me right now.

---

### Post by marcomangiante on 2006-09-30
Hello,

you downloaded it from the repository or from an eclipse mirror? However, if you install a vanilla eclipse (say that you have downloaded from eclipse or mirror site), all the files are only in the eclipse directory. So, maybe it is a permission problem. Try to extract the files under your home directory and see if you have this same problem. Please also do a research in the forums for eclipse because sometime it has some problems on jvm selection.

--
Regards,

Marco Mangiante

---

### Post by Ev.Eli on 2006-09-30
I'm sorry, I was a bit unclear. I originally installed Eclipse from the Ubuntu repos (and it worked), and then accidentally overwrote it with the web tools tarball.I'm not sure how it could be a permissions problem, since I removed Eclipse through apt and then completely deleted the /usr/lib/eclipse directory. Perhaps you are right though, since it seems to have retained the brokeness after the resinstall. I've been using Sun's JDK 1.5.0 the whole time.

---

### Post by Ev.Eli on 2006-09-30
Bumpity. I really have no idea what to do here, and it would be great if someone could at least point me in the right direction. Thanks!

---

### Post by _duncan_ on 2006-10-01
marcomangiante's post makes a lot of sense.

I originally installed eclipse through the ubuntu repository but uninstalled it completely when I found that the help system doesn't work.

As an alternative, I downloaded the eclipse linux package from the eclipse mirror site, installed it into a folder inside my home directory, opened a terminal, cd into the eclipse directory, and typed the following:

```
java -jar startup.jar
```

That's it! I have a working eclipse 3.2, complete with help files. Adding plugins is a lot easier too since everything is contained within the eclipse folder inside my home directory. No potential for conflict with other eclipse packages you may have thrashed before.

Now if you don't want to use the terminal to start-up eclipse, all you have to do is use the alacarte menu editor, create a new menu item called Eclipse under 'Programming', then point it at startup.jar.

Are you sure you have Sun Java 1.5 properly installed in your system?

---

### Post by Ev.Eli on 2006-10-01
Yeah, I suppose it does, although it does irritate me to have to go around apt. Oh well, at least I'll have a working Eclipse 3.2.

---

