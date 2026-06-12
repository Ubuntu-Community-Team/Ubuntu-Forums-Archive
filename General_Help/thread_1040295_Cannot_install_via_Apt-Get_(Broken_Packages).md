---
title: "Cannot install via Apt-Get (Broken Packages?)"
date: 2009-01-15
forum: General Help
---

### Post by insertnewsn on 2009-01-15
Hey everyone..

After reinstalling Ubuntu due to a faulty HDD, I can no longer install anything (well, mostly anything) via apt-get without it complaining that there are broken packages.

I've tried doing a "sudo apt-get -f install" and doing the graphical equivalent in Synaptic, but the problem persists.

The error occurs with no matter what I'm trying to download, but just for reference, this is an example of the errors I'm receiving:

"sudo apt-get install virtualbox-2.1"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-2.1: Depends: libqt4-network (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
                  Depends: libqtcore4 (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
                  Depends: libqtgui4 (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
E: Broken packages

```

I've tried removing the dependent packages and reinstalling them, but to no avail.

Has anyone else had this problem before? Or does anyone know where I could even begin to fix this?

Any help would be greatly appreciated!

---

### Post by 2hot6ft2 on 2009-01-15
> **insertnewsn said:**
> Hey everyone..

After reinstalling Ubuntu due to a faulty HDD, I can no longer install anything (well, mostly anything) via apt-get without it complaining that there are broken packages.

I've tried doing a "sudo apt-get -f install" and doing the graphical equivalent in Synaptic, but the problem persists.

The error occurs with no matter what I'm trying to download, but just for reference, this is an example of the errors I'm receiving:

"sudo apt-get install virtualbox-2.1"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-2.1: Depends: libqt4-network (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
                  Depends: libqtcore4 (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
                  Depends: libqtgui4 (>= 4.4.3) but 4.4.0-1ubuntu5 is to be installed
E: Broken packages

```

I've tried removing the dependent packages and reinstalling them, but to no avail.

Has anyone else had this problem before? Or does anyone know where I could even begin to fix this?

Any help would be greatly appreciated!
you can try

```
sudo dpkg --configure -a
```

this will fix any packages if it stopped during the install.

---

### Post by insertnewsn on 2009-01-15
Thanks for your reply..

I'm not sure what happened here, but after I tried a bunch of things, the problem has subsided.

I think by changing my sources (from columbia's mirror to a different mirror) the problem was fixed.

Thanks though!

---

