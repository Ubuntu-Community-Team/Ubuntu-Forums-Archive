---
title: "Trouble installing Beagle"
date: 2006-02-15
forum: Desktop Environments
---

### Post by carpe_noctum on 2006-02-15
Hello I'm trying to install beagle and this is the error I get. Is there a quick way around it ? 

The following packages have unmet dependencies:
  beagle: Depends: libgconf2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libglade2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libglib2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libgnome2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libgtk2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
E: Broken packages

---

### Post by kaamos on 2006-02-15
You have added 3rd party repositories for the mono packages (*-cil), so beagle probably won't install unless you downgrade the packages that have filefind.net in the version to the original ubuntu ones. Also comment out the filefind repository and run "sudo apt-get update".

---

### Post by carpe_noctum on 2006-02-15
Thanks. I believe that was because of automatix messing with some of my apt settings. I'm kinda new to apt..removed the offending packages and installed beagle...which picked up the right stuff.

---

