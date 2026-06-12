---
title: "Compiz installed but cannot open"
date: 2008-03-21
forum: Desktop Effects &amp; Customization
---

### Post by Thalakos on 2008-03-21
Hello,

I've been using ubuntu for a week now.

 I was very happy with my new OS but today after login in i noticed that instead of 4 workspaces i had only 2 and even after going to "Preferences" and changing it back to 4 columns the things didn't change.

Then i tried to go for the cube animation and it failed. I tried to go to "Visual Effects" under "Desktop Background" after right clicking the workspace, and Custom was there and I can even check it, but if I click "Preferences" it does nothing. After closing and going back, "Custom" isn't selected anymore.

If i do "compiz" in the terminal if fails in glx and if i close, all my windows header with "Minimize, Maximize and Close" vanish.

Can someone help me to have my effects back? 

Thanks in advance!

---

### Post by bronx on 2008-03-21
mate are you sure that your graphics card is properly installed?? Maybe you should take a look at **envy** which will install the right drivers for you. I hope this will help.

---

### Post by sayakb on 2008-03-21
Open a terminal and type:
```
compiz --replace &
```

Now, you might need ccsm (if you dont already have it)
```
sudo apt-get install compizconfig-settings-manager
```

After the command completes, goto System->Preferences->Advanced desktop effects settings. Then goto general options->desktop size tab. There increase the horizontal virtual size to 4. You might also enable Desktop cube, Rotate cube and Cube caps from ccsm.

---

### Post by Thalakos on 2008-03-21
Nothing changes. I installed envy and it says my OS is not supported when i choose 1 to install nvidia drivers.

I've also tried what Innovation said but there is no System->Preferences->Advanced desktop effects settings

The System->Preferences->CompizConfig Settings Manager is there but when i click it nothing happens.

Thanks for the help, hope anyone has the solution, otherwise i have to format :(

---

