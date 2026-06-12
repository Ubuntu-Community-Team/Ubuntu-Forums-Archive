---
title: "Help with Kubuntu 6.10 desktop, please..."
date: 2007-02-03
forum: Desktop Environments
---

### Post by dbneeley on 2007-02-03
I'm running Kubuntu 6.10 on an HP laptop...or at least I was for a week or so.

After downloading many add-on and upgrade packages, the graphical installer seems to have removed the KDE base desktop.

While I was connected via wireless network at one point in the graphical GUI, I'm afraid I cannot figure out how to do the same thing via command line (obviously a relative newbie!).

Now, I get the login window, then the system goes to a plain blue background...no icons or such at all!

I do have the install CD (ISO)...and, on the Windows XP side, I have installed LTOOLS so I can see, copy and paste in the Linux EXT3 partition. With the Windows up, I also have wireless connectivity--but not, of course, a clue as to how to get the right packages from the repository to replace any that have been removed.

I am about to give up and reinstall completely--but that would make a mess of all the additional apps I have installed. I suspect I can use the LTOOLS to copy the various things onto CD or DVD through Windows, then put them back once the new install is up and running--but, obviously, I'd like to avoid that if possible.

Can any of y'all think of a method of recovering everything without going through the total reinstall?

I would *definitely* appreciate any suggestions!

I am working toward being able to get rid of the Windows partition entirely once I have a bit more day-to-day experience with Linux. This problem, though, isn't necessarily the experience I would have selected!

Thanks in advance for any advice.

David Neeley

---

### Post by floke on 2007-02-03
from the command line, try: sudo apt-get install kubuntu-desktop
and this might reinstall it along with any bits and pieces for you
...hopfeully??

---

### Post by bailout on 2007-02-03
You may have uninstalled packages somehow or it may be something broken. I don't know whether this will work if you have updated packages since install but it is what I would try first. Unless you have changed your apt sources list to remove it the install cd should still be listed as a repository. After booting to the command line put the cd in and try to install kubuntu-desktop. If you have somehow delated core packages this may reinstall them from the cd.

btw I don't know whether this is the case with you but there seems to be several instances of people doing major damage to there installs by inadvertately uninstalling packages with adept while installing something else. I have difficulty understanding this as I always look at the display in the bottom left corner which tells you what it is going to do but it is always a good idea to click on the preview changes button before clicking commit. If it shows that it is going to uninstall 200 packages when you only wanted to install one new app - STOP ;)

---

