---
title: "Mono fails to install/uninstall"
date: 2011-01-13
forum: Desktop Environments
---

### Post by chomafin on 2011-01-13
Specifically, libgtk2.0-cil, seems to be giving me a world of trouble. 
I tried to install mono so that I could use an application. When it went to install libgtk2.0-cil, everything broke. I've tried to reinstall, purge, remove, and each time it fails. I've gone through a few iterations of trying to get things to remove cleanly to start fresh, so there are a few packages that are dependent on libgtk2.0-cil causing issues as well.. but thats to be expected. 

```
me@home:/media$ sudo apt-get purge libgtk2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono0 libgluezilla libglib2.0-bin libglib2.0-dev libmono-dev libjs-xmlextras libgdiplus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libglade2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 2,978kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176376 files and directories currently installed.)
Removing libglade2.0-cil ...
rm: cannot remove `/usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac': No such file or directory
dpkg: error processing libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil ...
rm: cannot remove `/usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac': No such file or directory
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried, and cannot locate the files it notes; `/usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac. I tried to create them real quick with touch, it removes what I make but still does not uninstall and still gives the err.

Can anyone offer assistance on removing this so that I can start fresh?

---

### Post by chomafin on 2011-01-14
Would there be a better sub-forum to take this to by chance?

Sorry for being antsy.

---

### Post by directhex on 2011-01-14
> **chomafin said:**
> Specifically, libgtk2.0-cil, seems to be giving me a world of trouble. 
I tried to install mono so that I could use an application. When it went to install libgtk2.0-cil, everything broke. I've tried to reinstall, purge, remove, and each time it fails. I've gone through a few iterations of trying to get things to remove cleanly to start fresh, so there are a few packages that are dependent on libgtk2.0-cil causing issues as well.. but thats to be expected. 

```
me@home:/media$ sudo apt-get purge libgtk2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono0 libgluezilla libglib2.0-bin libglib2.0-dev libmono-dev libjs-xmlextras libgdiplus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libglade2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 2,978kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176376 files and directories currently installed.)
Removing libglade2.0-cil ...
rm: cannot remove `/usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac': No such file or directory
dpkg: error processing libglade2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libgtk2.0-cil ...
rm: cannot remove `/usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac': No such file or directory
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libglade2.0-cil
 libgtk2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried, and cannot locate the files it notes; `/usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac. I tried to create them real quick with touch, it removes what I make but still does not uninstall and still gives the err.

Can anyone offer assistance on removing this so that I can start fresh?

Looks like the package didn't install fully, so it's getting confused.

Try this:

echo "/usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll" | sudo tee /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
echo "/usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.8.glade-sharp.dll" | sudo tee /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac

Should fix it up enough to remove... although I wonder why it's broken in the first place

---

### Post by bababooey on 2012-05-19
I tried the solution above, previously i just used touch to add the 2  files to trick dpkg into thinking its there and to remove libgtk2.0-cil  but during the process it would erase the 2 files, and then fails to  uninstall or purge the package. i've used both apt and aptitude since  aptitude allows more options for removing packages. but i still cant rid  this dang package and its blocking me from updating, installing,  upgrading packages on my fresh 12.04 system. Anyone found another  solution?

btw libgtk2.0-cil is a dep. for mono

---

### Post by directhex on 2012-05-19
> **bababooey said:**
> I tried the solution above, previously i just used touch to add the 2  files to trick dpkg into thinking its there and to remove libgtk2.0-cil  but during the process it would erase the 2 files, and then fails to  uninstall or purge the package. i've used both apt and aptitude since  aptitude allows more options for removing packages. but i still cant rid  this dang package and its blocking me from updating, installing,  upgrading packages on my fresh 12.04 system. Anyone found another  solution?

btw libgtk2.0-cil is a dep. for mono

You get *EXACTLY* the same error when you run the two echo commands above, then remove the package?

---

### Post by ngwad on 2012-05-21
Hi,

> **directhex said:**
> You get *EXACTLY* the same error when you run the two echo commands above, then remove the package?


Yep, me too. I tried to execute :

  while echo -n "" ; do touch /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac ; done

But It doesn't work.
Finaly, I had to edit 
/var/lib/dpkg/info/libgtk2.0-cil.postrm  and /var/lib/dpkg/info/libglade2.0-cil.postrm 
to put "return 0" after "#!/bin/sh" 

(and maybe suppress last lines of /var/lib/dpkg/info/libgtk2.0-cil.list and /var/lib/dpkg/info/libglade2.0-cil.list )

---

### Post by directhex on 2012-05-21
> **ngwad said:**
> while echo -n "" ; do touch /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac ; done

Sorry, I don't understand. Did you try what I suggested or not? Those files need content for the GAC registration to be handled correctly, you can't just touch them

---

### Post by Clonkonaut on 2012-06-06
Hi!

I'm running debian Squeeze for a start but wanted to ask if there's anything new on this. Google brought me here because of the exact same problem. I can't install or uninstall mono-runtime (or libgdiplus) because of this:


[I]Entfernen von libglade2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: Fehler beim Bearbeiten von libglade2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Entfernen von libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: Fehler beim Bearbeiten von libgtk2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Entfernen von libglib2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: Fehler beim Bearbeiten von libglib2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Fehler traten auf beim Bearbeiten von:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

(that's removing)

I'm glad for any help provided.

---

### Post by directhex on 2012-06-06
> **Clonkonaut said:**
> Hi!

I'm running debian Squeeze for a start but wanted to ask if there's anything new on this. Google brought me here because of the exact same problem. I can't install or uninstall mono-runtime (or libgdiplus) because of this:


[I]Entfernen von libglade2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.8.glade-sharp.installcligac
dpkg: Fehler beim Bearbeiten von libglade2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Entfernen von libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: Fehler beim Bearbeiten von libgtk2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Entfernen von libglib2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac
dpkg: Fehler beim Bearbeiten von libglib2.0-cil (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
configured to not write apport reports
                                      Fehler traten auf beim Bearbeiten von:
 libglade2.0-cil
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

(that's removing)

I'm glad for any help provided.

Blow away the "bad" .installcligac files from /usr/share/cli-common/packages.d, uninstall, reinstall.

But I have to stress: your situation is absolutely impossible unless you either have disk corruption, or have done some VERY evil things to your mono install.

---

### Post by Clonkonaut on 2012-06-07
Hey thanks for answering :)
The packages.d directory is empty, so nothing to blow away. Should there be something in it?

If it's a disc corruption, I hope that my vServer provider will take of this ;)

I don't know what kind of bad things I did to mono. I had a clean install of the OS, then installed mono-runtime, afterwards mono-complete because I was lacking some files I needed for my application.
Then I had the probably stupid notion that mono-runtime is now consuming disc space and I removed that. That's when the errors showed up.
I tried to fix it with a "clean" install of mono-complete again but removing/installing is now impossible.

Anything I could do except deleting stuff from /usr/share/cli-common/packages.d then?

---

### Post by Clonkonaut on 2012-06-07
Okay, I solved it. Got the solution from here: [http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/#post3040967]("http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/#post3040967")

> I had a similar problem and what i found that worked for me was going into /var/lib/dpkg/info and deleting everything that had that name and you may also have to go into /var/cache/apt/archives and do the same thing. I'm fairly new to linux so if this breaks anything i am sorry. i haven't run into any problems yet that this has caused.

Thanks for help though :)

---

