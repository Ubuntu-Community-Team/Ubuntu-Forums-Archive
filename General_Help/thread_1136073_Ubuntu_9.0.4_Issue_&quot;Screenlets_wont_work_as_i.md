---
title: "Ubuntu 9.0.4 Issue &quot;Screenlets wont work as it should&quot;"
date: 2009-04-24
forum: General Help
---

### Post by prodisin on 2009-04-24
Hey guys! first off i would like to say hi to all on Ubuntu Forums as I am new here lol! and second of all I am having a slight issue with "Screenlets" after updating to 9.0.4.

Basically since updating I can not display any of my Screenlet widgets any more as of before I had no problem, if anyone knows a way I could fix this I would be very grateful for your help?

---

### Post by codeseer on 2009-04-24
Are you sure the Screenlets daemon is running? Check in the system tray.

I just installed Screenlets from the repositories on my 9.04 64-bit setup in VirtualBox and everything seems to be fine.

Everything continued to work fine when I restarted as well.

---

### Post by prodisin on 2009-04-24
> **codeseer said:**
> Are you sure the Screenlets daemon is running? Check in the system tray.

I just installed Screenlets from the repositories on my 9.04 64-bit setup in VirtualBox and everything seems to be fine.

Will just check now, sorry kinda new to Ubuntu but hell so glad I have converted to it loL!

---

### Post by prodisin on 2009-04-24
yep it's open, I go into the Screenlets manager click start and all the widgets I originally used don't even pop up on the screen any more no matter how many times I tick start on/off, and the weirdest thing is some of the widgets work but none of my other widgets used before the update work at all

---

### Post by codeseer on 2009-04-24
Have you tried a complete removal of Screenlets then?

I'd do a 'complete removal' using Synaptic. Then send the ~/.config/Screenlets directory to the trash. Then reinstall the Screenlets package.

---

### Post by prodisin on 2009-04-24
yep have uninstalled it and then re-installed again from the software repositories and still I have the same issue

---

### Post by codeseer on 2009-04-24
I'd try it with sending the configs to the trash, between the uninstall and the reinstall.

---

### Post by prodisin on 2009-04-24
> **codeseer said:**
> I'd try it with sending the configs to the trash, between the uninstall and the reinstall.


How do I do that? sorry not much of a wiz kid with Ubuntu lOL!

---

### Post by codeseer on 2009-04-24
To do a 'complete removal' open Synaptic from the System->Administration->Synaptic Package Manager menu. Then click the 'Search' button and type 'screenlets' in the box and click the 'Search' button. It should show Screenlets in the listing then, click on it, right-click it and choose 'Mark for Complete Removal' from the menu. Then click the 'Apply' button.

For cleaning up the old configuration in the GUI, you can click Places and then click Home Folder. Click the View menu and click Show Hidden Files. Then double-click on .config and single-click on Screenlets and hit the Delete key. Wouldn't hurt to get the .screenlets directory in the your home folder while you're at it.

To reinstall it after sending the old configuration to the trash, do the same with Synaptic as you did before, except when you right-click on Screenlets in the list, choose 'Mark for Installation'.

---

### Post by prodisin on 2009-04-24
> **codeseer said:**
> To do a 'complete removal' open Synaptic from the System->Administration->Synaptic Package Manager menu. Then click the 'Search' button and type 'screenlets' in the box and click the 'Search' button. It should show Screenlets in the listing then, click on it, right-click it and choose 'Mark for Complete Removal' from the menu. Then click the 'Apply' button.

For cleaning up the old configuration in the GUI, you can click Places and then click Home Folder. Click the View menu and click Show Hidden Files. Then double-click on .config and single-click on Screenlets and hit the Delete key. Wouldn't hurt to get the .screenlets directory in the your home folder while you're at it.

To reinstall it after sending the old configuration to the trash, do the same with Synaptic as you did before, except when you right-click on Screenlets in the list, choose 'Mark for Installation'.

ok mate will try that now, thank  u for the advice will let u know if it has worked

---

### Post by prodisin on 2009-04-24
ok its worked but I have a widget installed called "Perfect Clocks" and everytime I tick start on the widget so that it turns the widget off everytime I highlight it again it keeps on showin me the widget is still on but not visable uninstalled the widget n reinstalled it n still get the same thing even when I delete the .config files for the widget it still duz the same thing

---

### Post by codeseer on 2009-04-24
It has a blue background and 6 clocks on the icon?

Try opening the Screenlets Manager, clicking on PerfectClocks and clicking the Reset Screenlet Configuration.

---

### Post by prodisin on 2009-04-24
yeah thats the one its the imac style clocks which I got from gnome-look.org...have managed to get it workin now though had to turn the auto start off n then click the icon a good few times n then it finally popped up on my desktop n when it did I put an autostart tick on so the same disklets loadup on startup, restarted it to see if it works well n it duz now loL! thank u for helping me out mate appreciate it alot wouldn't of solved the problem without ur help :-)

---

