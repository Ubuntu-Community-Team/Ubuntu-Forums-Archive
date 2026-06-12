---
title: "launcher referencing NAS file from Thunderbird"
date: 2009-03-15
forum: Desktop Environments
---

### Post by Tarzan_MonkeyMan on 2009-03-15
I'm a MS Windows user, who has become fed up and recently switched ot Ubuntu.  I had some experience with UNIX many years ago.  I'm using a network with a NAS.  I keep my E-Mail profiles on the NAS, so that I can access them from any computer on the network.

I mounted the NAS to the directory:  /mnt/NAS

I'm using Mozilla Thunderbird as my E-Mail client (which I highly recommend) and the following command works nicely from the command line (the sudo IS needed):

sudo thunderbird -profile "/mnt/NAS/E-Mail Files/Thunderbird Profiles"

However, when I created a desktop icon Launcher I couldn't get it to work.  It appears to think I don't have permission to access the NAS profile files.  I've tried changing various directory/file permissions, but this didn't seem to make a difference.  I've tried using gksudo and gksu, but no luck either.  

Anyone have any other suggestions or an explanation as to why I can't duplicate in the Launcher what does works in the command line?

---

