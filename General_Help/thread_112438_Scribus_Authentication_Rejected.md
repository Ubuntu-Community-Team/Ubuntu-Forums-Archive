---
title: "Scribus Authentication Rejected"
date: 2006-01-04
forum: General Help
---

### Post by wacole on 2006-01-04
I installed Scribus using Synaptic and ran it from the Gnome  Applications|Office menu.  The splash screen displayed, then went away and nothing else happened.  So I completely uninstalled Scribus throught Synaptic and reinstalled.  Same problem.  So I decided to run the application from the root terminal.  Here's what was displayed:

[I]root@PenguinBeach:/usr/share # scribus
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Bus error[/I]

BTW I did upgrade from Warthog.  Maybe that has something to do with this?

What is this all about, please?

Thanks,

Bill Cole

---

### Post by stuporglue on 2006-01-04
> root@PenguinBeach:/usr/share # scribus
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Bus error

Up to the "Bus error" part is because you're running a GUI program as root when it's not root that started that GUI session. You can do it because root can do pretty much anything, but it just whines a litt.e

I don't think the "Bus Error" is part of the GUI authentication thing, and may be related to why scribus isn't working. What happens if you try to start scribus from a terminal as your normal user?

---

### Post by wacole on 2006-01-04
Thank you very much, indeed, for the quick reply.

Here's the result from running as non-root terminal:

[I]wcole@PenguinBeach:~$ scribus
Bus error[/I]

No authentication whining ... just the bus problem again.

BTW, I had Scribus running under Warthog.

Thanks again,

Bill Cole

---

### Post by daibak on 2006-01-04
[QUOTE=wacole]Thank you very much, indeed, for the quick reply.

Here's the result from running as non-root terminal:

[I]wcole@PenguinBeach:~$ scribus
Bus error[/I]

No authentication whining ... just the bus problem again.

BTW, I had Scribus running under Warthog.

Thanks again,

Bill Cole[/QUOTE]
This afternoon I followed Scribus' advice to update to their new version released yesterday/2006-01-03. Very straightforward if follow these steps:
First, told Synaptic to do a Complete Removal of the existing Scribus version - I think it was 1.2.2.1; did a Reload of the repositories.
Second, added the [Custom]("http://http://docs.scribus.net/index.php?lang=en&page=install-dpkg") Repositories in Synaptic exactly as Scribus lists them for Breezy Badger; again did a Reload. I'm careful to click OK after I add each individual Repository.
Third, did a search in Synaptic for Scribus and opted to install both the new stable and unstable 1.3-cvs versions, including the EN documentation.
Synaptic gave warning about non-authentication of two keys which ignored. Typed *scribus* in terminal and it launched 1.3. Now I can appreciate a Help button that actually works in Synaptic.

---

### Post by daibak on 2006-01-04
Sorry, just saw I botched the URL in last post to the Scribus Custom Repositories so I've corrected that to what it should have been
[http://docs.scribus.net/index.php?lang=en&page=install-dpkg](http://docs.scribus.net/index.php?lang=en&page=install-dpkg)

As an aside, how mistyping a double http:// leads one to Microsoft beats me!

---

### Post by wacole on 2006-01-04
Thanks very much for the repository info.  

I did all that, downloaded the 1.3.1-cvs version and, after a complete removal of 1.2.2.1, marked for install.

Got the splash screen and then - arrrgh! - the same message:

[I]wcole@PenguinBeach:~$ scribus
Bus error[/I]

Maybe I need to do a full re-install of Breezy?

Thanks much.

---

### Post by daibak on 2006-01-04
[QUOTE=wacole]Thanks very much for the repository info.  
...
Maybe I need to do a full re-install of Breezy? ...[/QUOTE]

Don't think so, I've had Bus error too before with other apps. Something to do with the device mapping of wine/Picasa2 or wine/something, probably DVD Decrypter or DVD Shrink. All I can recall is Complete Remove and Install all over of the misbehaving app did the trick using Synaptic. Suggest re-check all mounted devices, power on/off, load/eject, working properly before a re-install.

---

### Post by wacole on 2006-01-05
Thanks again.  Will try these out and report back.

BTW I found this when Googling "Bus error":

[I]If the program displays this message:

	Bus error
or
	Segmentation fault

... then the program was trying to access a memory location outside its
address space.  The computer detected this problem and sent a signal to your
program, which caused it to abort.

Things that cause bus errors and segmentation violations are typically
out-of-bounds array references and/or references through uninitialized or
mangled pointers.  Look very closely in your program for bizarre things like
that. [/I]

Makes it sound like an application problem ....

---

### Post by wacole on 2006-01-09
In the interim Ubuntu released 1.2.4.1 Scribus through their update tool.  I downloaded and installed [after uninstalling my 1.3 version of Scribus] using the Ubuntu native tool.

Sad to report, same issue

*Bus Error*

---

### Post by daibak on 2006-01-12
[QUOTE=wacole]In the interim Ubuntu released 1.2.4.1 Scribus through their update tool.  I downloaded and installed [after uninstalling my 1.3 version of Scribus] using the Ubuntu native tool.

Sad to report, same issue

*Bus Error*[/QUOTE]

If you haven't yet solved this issue my automatic Breezy Update notified me I could update to a newer version, which I did. If you care to check out the new Scribus version numbers they're in attached thumbnail of today's screenshot.

---

### Post by wacole on 2006-01-15
Thanks to everyone for your help.  The issue seems larger that Scribus so I'm going to take a deep breath and do a reinstall.

---

### Post by datelus on 2006-09-16
reinstall wont do teh trick. dident for me. Shows: scribus segmentation fault
](*,)

---

