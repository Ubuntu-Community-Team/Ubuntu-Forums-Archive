---
title: "Bibus lacks OOo Menu"
date: 2007-05-08
forum: Education &amp; Science
---

### Post by diceratops on 2007-05-08
I am running Bibus 1.3.0 on Feisty (32 bit), with OpenOffice.org 2.2. OpenOffice is running from /opt/openoffice.org2.2 (installed using files direct from the OpenOffice folks), because I was sick of the bad font rendering in the Ubuntu-built version of OOo.

So, my problem is that I do not get the OpenOffice.org menu within Bibus (and hence I am unable to insert references into my OpenOffice documents!). I have double-checked to make sure that my Uno connection is active (and using a pipe). When I go to the preferences menu in Bibus, the "word processor" preferences are always grayed out. If I set it back to OpenOffice.org Writer, the preference doesn't seem to "stick". I'm not sure if this is a separate, or a related issue. Is it something to do with having multiple versions of Python on my machine (2.5.1 and 2.4.2)?

Has anyone else had similar issues? Any ideas? I've got a dissertation to write! ;-)

Andy

---

### Post by akniss on 2007-05-08
Have you tried opening Bibus, and using the First Connection Wizard after installation of the official OOo build?
Help > First Connection Wizard

---

### Post by diceratops on 2007-05-08
Thank you for the tip - this was one of the first things I tried. I have tried to use the "First Connection Wizard," setting Bibus to recognize OOo Writer, but this setting never "sticks." Even when starting as "sudo bibus," it doesn't seem to make a difference. Any further thoughts?

---

### Post by akniss on 2007-05-08
There was a similar post in the Bibus forums.  Pierre, the author of bibus gave this advice:

[QUOTE=Pierre Martineau in Bibus Support Forums]
Have a look in:
/usr/share/bibus/bibus.cfg 
 
Check that the paths are correct in it and eventually correct them, particularly the oopath value (this value depends on the distribution, for debian it is /usr/lib/openoffice/program, for Ubuntu /usr/lib/openoffice2/program, sometimes it is /usr/lib/ooo-2/program, ...) 
 
oopath should contains the OOo shared libraries.
[/quote]

On my working Feisty install, /usr/share/bibus/bibus.cfg contains the following:
```
[PATH]
docdir = /usr/share/doc/bibus/html
licence = /usr/share/doc/bibus/copying
localedir = /usr/share/locale
oopath = /usr/lib/openoffice/program
systemconf = /etc/bibus.config
```

My guess is that the official OOo installation put the OOo shared libraries somewhere else.  If you can figure out where they are, and change the contents of /usr/share/bibus/bibus.cfg to match (the oopath= line), things should work for you.

---

### Post by diceratops on 2007-05-08
No luck on that count either - I had changed it to

oopath = /opt/openoffice.org2.2/program

(which is where my current installation is) but this didn't seem to make any difference.

---

### Post by akniss on 2007-05-08
> **diceratops said:**
> No luck on that count either - I had changed it to

oopath = /opt/openoffice.org2.2/program

(which is where my current installation is) but this didn't seem to make any difference.

Okay... one more try, then I'm out of guesses.  Try starting Writer at the terminal with the following command:
```
oowriter "-accept=pipe,name=OOo_pipe;urp;StarOffice.ServiceManager"
```
and then see if Bibus can find anything.

---

### Post by diceratops on 2007-05-09
No luck on that either - thank you for the help, though! I've tried uninstalling and reinstalling Bibus, but no luck on that count. . .if anyone else has ideas, please let me know.

Thanks,

Andy

---

### Post by vanadium on 2007-05-10
Am am facing the same issue. I replaced the OOo from the ubuntu packages with the packages from OOo. Now, the Bibus OpenOffice.org menu indeed is not there anymore. The uno bridge is working, I changed the path in bibus.cfg, but no avail. My reason for changing was that Ooo on Feisty crashes each time one exits a presentation. I am searching also for a solution and obviously, I&#314;l post back if I succeed.

---

### Post by UI-Freak on 2007-05-18
I have the same problem; I also installed the official OOo because the Ubuntu version crashes big time here. I tried all of the above to no avail. :(

---

### Post by UI-Freak on 2007-06-06
BUMP

Any ideas?

---

### Post by muyiwataiwo on 2007-06-17
I found this thread useful in solving this problem on my Fedora 7 installation, so I thought I should share my experience, in the hope that it will help others still having this problem.

it seems that the *oopath* setting in */usr/share/bibus/bibus.cfg* refers to the directory where the python uno shared library and other python scripts needed by Bibus are kept, and NOT the OpenOffice.org libraries.  These shared libraries are part of the *OpenOffice.org-pyuno* package, and NOT OOo Writer!

To find where these files are stored on my system, I used rpm like so:

> rpm -q --list openoffice.org-pyuno

which told me that the correct place to be looking at is */usr/lib/openoffice.org/program*, not /usr/lib/openoffice.org2.0/program where OOo Writer puts its own libraries!

You may be able to use a similar command in Ubuntu to find out where the pyuno libraries are kept.

I hope this helps.

---

### Post by UI-Freak on 2007-06-24
Didn't help. I am as lost as these guys: [http://sourceforge.net/forum/forum.php?thread_id=1463866&forum_id=380178](http://sourceforge.net/forum/forum.php?thread_id=1463866&forum_id=380178)

---

### Post by halocaridina on 2007-06-26
I've experienced the same problem with Bibus lacking the OOo menu after switching from the Ubuntu version of the package in Edgy to OOo 2.2.

I think it has something to do with the fact that OOo 2.2 appears to use Python 2.3.  I stumbled across this while browsing the OOo 2.2 directory in /opt (note the folder titled "python-core-2.3.4").

I have a feeling that since the python versions don't match (on my Edgy system, I have Python 2.4 and 2.5), the uno bridge is DOA, thus the missing OOo menu in Bibus.

My guess is that if Python 2.3 was available to the system, the menu would reappear.  I've tried symlinks to see if that might work, but it didn't.  

It will be interesting to see if the lack of having Python 2.3 is the root of the problem.

---

