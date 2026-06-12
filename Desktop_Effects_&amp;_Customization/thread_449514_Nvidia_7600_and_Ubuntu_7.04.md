---
title: "Nvidia 7600 and Ubuntu 7.04"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by fossiili on 2007-05-20
In my sons and sonsons computer I had Suse 10.2 installed and it worked well. Then the boys wanted to have WindowsXP also for the sake of games and they had spared money for a new hard disk and I installed WindowsXP in their (actually my...) computer.

Unfortunately Suse 10.2 disappeared in that process so I installed the brand new Ubuntu 7.04 and in the beginning it seemed to work well. An unpleasent surprice was that it ones frozed completely (Ctrl+Alt+F7 did not help), but that event has not been repeted.

My displaycard is PALIT Nvidia GeForce 7600 and in Suse 3D acceleration and the modern desktop effects worked well after installing Nvidia proprietary driver.

As a pleasant surprice I found from Ubuntu 7.04 an easy to use tool to get Nvidia's driver in work. Everything seemed go well and I started Ubuntu again. But now the X-server could not work, no graphical desktop at all:(

After some efforts and other hash the graphical desktop started and I could even get the Beryl-effects to work! But again, when shutting the computer and starting it again X did not start for the sake of some errors:evil:

The 3D acceleration is a must, becouse without it the childrens can not play the nice Ppracer-game they like verry much. Also my sonson hopes he can present the fine Beryl effects he has in "his Linux" to his frends.

Is there anything I could try to get 7.04 to work?
Is there any hope that this error would be solved by system uppdates later?

---------------------
Later: Nothing seems to help. Also [http://ubuntuforums.org/showthread.php?t=449254&highlight=Will+now+halt](http://ubuntuforums.org/showthread.php?t=449254&highlight=Will+now+halt)

---

### Post by vikramsharma on 2007-05-21
> **fossiili said:**
> In my sons and sonsons computer I had Suse 10.2 installed and it worked well. Then the boys wanted to have WindowsXP also for the sake of games and they had spared money for a new hard disk and I installed WindowsXP in their (actually my...) computer.

Unfortunately Suse 10.2 disappeared in that process so I installed the brand new Ubuntu 7.04 and in the beginning it seemed to work well. An unpleasent surprice was that it ones frozed completely (Ctrl+Alt+F7 did not help), but that event has not been repeted.

My displaycard is PALIT Nvidia GeForce 7600 and in Suse 3D acceleration and the modern desktop effects worked well after installing Nvidia proprietary driver.

As a pleasant surprice I found from Ubuntu 7.04 an easy to use tool to get Nvidia's driver in work. Everything seemed go well and I started Ubuntu again. But now the X-server could not work, no graphical desktop at all:(

After some efforts and other hash the graphical desktop started and I could even get the Beryl-effects to work! But again, when shutting the computer and starting it again X did not start for the sake of some errors:evil:

The 3D acceleration is a must, becouse without it the childrens can not play the nice Ppracer-game they like verry much. Also my sonson hopes he can present the fine Beryl effects he has in "his Linux" to his frends.

Is there anything I could try to get 7.04 to work?
Is there any hope that this error would be solved by system uppdates later?

---------------------
Later: Nothing seems to help. Also [http://ubuntuforums.org/showthread.php?t=449254&highlight=Will+now+halt](http://ubuntuforums.org/showthread.php?t=449254&highlight=Will+now+halt)

First you would have to install drivers for Nvidia on your Ubuntu install, have you installed the Nvidia Drivers on Ubuntu.  In case you haven't use "Restricted Drivers Manager", the path to go there is by System->Administration->Restricted Drivers Manager.  And once the drivers are installed, goto the "Desktop Effects" via  System->Preferences->Desktop Effects.   Click on "Windows Wobble when Moved" and also mark "Workspace on a Cube"thing.  In case I confused you , you can also have a look [here]("http://blog.mypapit.net/2007/04/how-to-enable-3d-desktop-effects-on-ubuntu-feisty-fawn-704.html") . Hope this helps you.

---

