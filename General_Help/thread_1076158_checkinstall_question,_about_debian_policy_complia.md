---
title: "checkinstall question, about debian policy compliant versioning"
date: 2009-02-21
forum: General Help
---

### Post by jerome1232 on 2009-02-21
Okay so even though I don't really like docks, kiba-dock is supposed to have this really neat physics engine where I can toss around the icons and such so I'd thought I would add some eye candy to play with.

I just started and got akamaru compiled so far (it's the physics engine), I decided to use checkinstall to install the compiled programs for ease of removal.

Right now I'm here.

```

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.1
0.1
0.1
0.1
0.1
0.1
0.1" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

```

So what would be a proper Debian compliant version number I should use? I realize it probably doesn't matter but I imagine it would if I were compiling newer versions of things that actually are in the repositories. So might as well ask now.

edit:

Would it be someting like 0.1-amd64 ?

Thanks in advanced :)

---

### Post by mc4man on 2009-02-21
I forget exactly but probably anything but 0.1 will be accepted.
There are several examples of how to create and set the ver. thru the checkinstall command in these posts

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

---

### Post by mb_webguy on 2009-02-21
It needs a dash plus an extra version number, usually something like the date it was created.  [Here]("http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/")'s a link to a HowTo on creating Debian-compliant packages.  Section 4.1 (very) briefly mentions version numbers.

---

### Post by jerome1232 on 2009-02-21
Thank you for the links, explained it all :) 

Unfortunately checkinstall didn't work tossed out errors (way to far up my terminal screen to recall them after compiling all the components of kiba-dock), make install still did work for getting the programs installed though.

---

