---
title: "msttcorefonts"
date: 2006-02-18
forum: Desktop Environments
---

### Post by racecat on 2006-02-18
Alright, I've got a new load of K and I'm trying to load msttcorefonts. I tried both Adept/Synaptic and the CLI per the Wiki Unnofficial users guide. Here's what I get:


```
bill@ubuntu2:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  msttcorefonts
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B/22.1kB of archives.
After unpacking 168kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 81666 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu2_all.deb) ...
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--16:14:57--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--16:15:07--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--16:15:17--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--16:15:27--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--16:15:37--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--16:15:47--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill@ubuntu2:~$                                                             
```

which tells me they are no longer available from sourceforge. I have a tar file of them I saved from my Hoary install. What do I do with it? If I remember, I was working with a prerelease of Breezy on a test machine and ran into this. I think I untar'ed the file and just put it where it belonged, but it really didn't work. I've got to start making notes. My memory is failing me. Argh!

Any ideas are greatly appreciated.

BTW I, as a previously devoted Xfce user, I loaded it. Ran it for a day and came back to K!

Thanks,
Bill

---

### Post by jrib on 2006-02-19
msttcorefonts should be in multiverse, have you enabled it?  Or maybe it uses something from sourceforge while installing... What does 'apt-cache policy msttcorefonts' say?

---

### Post by racecat on 2006-02-19
[QUOTE=_jason]msttcorefonts should be in multiverse, have you enabled it?  Or maybe it uses something from sourceforge while installing... What does 'apt-cache policy msttcorefonts' say?[/QUOTE]

Thanks for the reply. I do have multiverse enabled and actually installed the msttcorefonts package (I've since removed it or it would show up as installed) but, as the terminal in my previous post shows, it's not actually able to get the fonts from sourceforge. At least that's the way I'm reading it. "Apt-cache policy msttcorefonts gives" me

```
bill@ubuntu2:~$ apt-cache policy msttcorefonts
msttcorefonts:
  Installed: (none)
  Candidate: 1.2ubuntu2
  Version table:
     1.2ubuntu2 0
        500 http://archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
bill@ubuntu2:~$
```


I thought of something this morning. When I get some time this afternoon, I'm going to un'tar what I've got and use the KDE font installer utility. I'll keep you posted.

Thanks again,
Bill

---

### Post by racecat on 2006-02-21
Okay, I extracted the fonts and used the KDE font installer. I got on the problem website (Roadrunner with flash installed) with Firefox. I am missing the fonts (on the web page) exactly like my Hoary install before installeing msttcorefonts through Synaptic (when sourceforge had them). I tried installing them both in my personal fonts and the systemwide fonts. I think Konqueror sees them. If I knew how to get a flash plugin into Konqueror, I'd test it. Hmm!

What am I missing? Does the KDE font installer not put them where they are needed for Breezy, or is it a Firefox issue? My understanding was that fonts are placed in one of a couple of places and all applications look there for them. Can anyone shed a little light?

Well, any help would be appreciated. Thanks.

Bill

---

