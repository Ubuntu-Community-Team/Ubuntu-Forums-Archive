---
title: "Wine configuration crashes"
date: 2006-05-15
forum: Desktop Environments
---

### Post by pillu on 2006-05-15
Hello all
I am running Xubuntu on my Dell P2 laptop. I tried to install Wine by following the directions in the Official Wiki. However when I try to configure wine using the winecfg command the whole system crashes. I have to do a hard reset to get it up and running again. What might be the problem? Should I try installing earlier versions of wine instead of the latest one? If so, how do I do that. 

Thanks

---

### Post by Chris03 on 2006-05-15
Not sure about config files, but I did the following:

sudo gedit /etc/apt/sources.list

Enter the below repository, as referenced here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main

Save and close.

sudo apt-get update
sudo apt-get install wine

Then on an .exe file, right click on it and select "Open with other application", then click on the arrow near "Use custom command", and then type **wine** in the box.

Then, to browse the pseudo Windows environment that Wine sets up, go to the Home folder in Nautilus, and then to the .wine folder. It might be hidden, in that case press Ctrl + H.

Some .exe files can work, others are buggy. Wine isn't perfect but it's awesome progress given Microsoft never published the specifications to the Win32 API.

---

