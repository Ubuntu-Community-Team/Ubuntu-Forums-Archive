---
title: "OpenOffice install gone bad... 9.04"
date: 2009-05-02
forum: General Help
---

### Post by 300Z on 2009-05-02
Hi, I just recently installed Studio 9.04 and everything worked great till today when I tried to install open office from the add application then the computer froze during the install, after restarting the machine neither the add/remove applications, update manager nor synaptic package manager works due to an "incomplete" open office install it keeps telling me to run 'sudo dpkg --configure -a' from terminal and every time I do the computer freezes, then I tried it as root and it just doesn't do anything and tells me to reboot.

What can I do? I tried searching but didn't find any help regarding this case.

Thank you.
Leo

---

### Post by 300Z on 2009-05-02
Bump any1? :(

---

### Post by ludwigg77 on 2009-05-02
Hi There, same thing is happening to me. Hopefully we can solve this. I will let you know if I find something
Rgds, Greg

---

### Post by joeyknuccione on 2009-05-02
Just trying to help here, have you tried:

Backup all data

uninstall open office (from command line)

find any old folders that were not removed from the uninstall

reinstall

I'll let you find the uninstall commands so's I don't offer potentially damaging instructions.

---

### Post by 300Z on 2009-05-03
Just did a clean reinstall of Studio but didn't install open office this time and so far things are looking good. :)

Leo

---

### Post by mapsight on 2009-05-05
I'm having the same issue after a fresh install of Jaunty (32-bit i386, Ubuntu Studio version)... hangs on mailmerge.py, and this freezes the system when the automatic update fires up shortly after logging in.  I've tried to run:

```
sudo dpkg --configure -a
```

from the command line, even running in rescue mode from the install DVD, but it hangs every time.

---

### Post by 300Z on 2009-05-05
I read and tried everything I could for a day but nothing worked, so a fresh reinstall was the only way to go.

---

### Post by ludwigg77 on 2009-05-05
Hi Leo, 

Did you get open office to work properly after this fresh rebuild?
It did not work for me so I am curious to know.
Cheers, 
Greg

---

### Post by fuxwald on 2009-05-19
Same problem: Clean installation of Ubuntu Studio 9.04. Installation freezes at the same point. Did anyone find a solution for this problem?

Maybe I will install Ubuntu 9.04 and add the rt-kernel and all other packages needed for audio-editing as I did before but that's a lot of work for such a :-# bug.

---

### Post by scouser73 on 2009-05-19
I had same problem installing Openoffice so I did a clean install of Jaunty and downloaded the .deb from the openoffice website rather than using synaptic or Add/Remove and it's working well. I'm not saying that you'd need to do a clean install, but it's a suggestion. I hope you can get it sorted out.

You could try and install OpenOffice 3.1.0 from the site:

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: [B]sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb
[/B]
Once you've done that you'll find OpenOffice 3.1.0 in Office

---

### Post by rgsproductions on 2009-05-19
Your instructions worked except Openoffice base seems to have issues starting.  In 8.10. I was sucsessfull in installing OO3.1.0.  In Jaunty, I got errors even when using the PPA method.

***** Finally** solved my issues with OO3.1 installing.  I had to remove the .openoffice folder in the home directory and remove the office folder in the OPT directory.  Reinstalled OO3.1 and all programs work great.

---

### Post by grayn0de on 2009-07-17
Bug reported. If anyone has any additional info, please post a comment to the bug report, so that it can be confirmed.

[https://bugs.launchpad.net/ubuntustudio/+bug/400726](https://bugs.launchpad.net/ubuntustudio/+bug/400726)

((Sorry to bump an old thread, but this is still an issue that I am sure others might like fixed... :) ...))

---

