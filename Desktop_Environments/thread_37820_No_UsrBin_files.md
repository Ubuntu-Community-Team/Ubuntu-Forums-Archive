---
title: "No /Usr/Bin files"
date: 2005-05-28
forum: Desktop Environments
---

### Post by QuestionsBoyee on 2005-05-28
Some how i delete the /usr/bin files i was trying to install firefox that I downloaded. Not from apt-get. So now I have no gui nor do i have files in the /usr/bin so Is there a way to re-install without formatting the boot partition I have files I want.  I not a linux noob(I used RH FC) but I am a ubuntu noob. Thanks for your help.

---

### Post by Alexander Kirillov on 2005-05-28
[QUOTE=QuestionsBoyee]Some how i delete the /usr/bin files i was trying to install firefox that I downloaded. Not from apt-get. So now I have no gui nor do i have files in the /usr/bin so Is there a way to re-install without formatting the boot partition I have files I want.  I not a linux noob(I used RH FC) but I am a ubuntu noob. Thanks for your help.[/QUOTE]
 Have you removed *all* /usr/bin files? Then I think reinstalling Ubuntu is the only way. If you just removed some of them, you can reinstall the appropriate application.

---

### Post by tread on 2005-05-28
Maybe boot from the live cd and then mount the harddrive and copy some of the essential executables? like apt etc and then reinstalling a lot of the major packages?

---

### Post by QuestionsBoyee on 2005-05-29
im not sure even how I did it i pointed the firefox install to the  /usr/bin folder

but my question is how do you reinstall without losing files on the HD?

thanks for your help in advance.

---

### Post by tread on 2005-05-29
I'm a little confused here really .. are you posting this from your linux setup? What happens when you try to boot into linux?

---

### Post by JonahRowley on 2005-05-29
If you've deleted all the files in /usr/bin, you've deleted apt and dpkg, as well as any hope you have of fixing this without reinstalling.  Unless reinstalling is not feasible (for some reason..), it'll be your easiest way to fix this.  Be careful what commands you use with sudo ;)

---

### Post by dbloom on 2005-06-01
well, you're not the only dunce -- i just did the same thing last night.  i've been running a debian system for 2 years and i still made that mistake!

anyway, i happened to have a few live cd's laying around.  i used kanotix to mount the drive and burn a cd with many of my important files.  then i re-installed ubuntu. 

kanotix was pretty good for that.  i think knoppix and mepis may also work well (in that they also automatically mount all connected drives).

---

