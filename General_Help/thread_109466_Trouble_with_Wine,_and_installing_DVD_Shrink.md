---
title: "Trouble with Wine, and installing DVD Shrink"
date: 2005-12-28
forum: General Help
---

### Post by OscarGortez on 2005-12-28
First off i'm using the [http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/) guide to try and do this.  I've skipped the whole DVD decrypter section (though i did go back and now when i try to install it, wine gives me a "NSIS ERROR.    Error writing temporary file. Make sure your temp folder is valid." pop-up and a failure status of 2).

Installing DVD shrink I got though, I had to change the config file for wine by going to it through file browser, since the root terminal wouldn't see it, and opened a new file when i tried to edit it.  I also had to speficy the directory that the DVD shrink install file was in when I ran the WINEDALLOVERRIDES command since the exact command on that site didn't work for me.  

Now once it's finished installing DVD Shrink, I can launch it and it'll run buut it won't see the DVD in my drive.  And once I close the program, I try to open it again by going to applications, debian, wine, ., DVD shrink 3.2 and it just gives me a failure status of 1.

Any ideas of what i'm doing wrong or is going wrong? also if you know of any program for Linux that's just as good as DVD shrink I'd be willing to try that, a Friend suggested DVDrip but my repositories suck so when I tried to download that to give it a try I just got an error.

---

