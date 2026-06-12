---
title: "Google Earth Without Sudo"
date: 2009-01-05
forum: General Help
---

### Post by kaoskorruption on 2009-01-05
I've installed Google Earth recently but it doesn't work without doing SUDO googleearth. If I do it without sudo it never shows the globe, just stars. I've search around a bit, but everybody has had to use sudo. Does anybody know of any way to install it so that this is not necessary?

Thanks!

---

### Post by iaculallad on 2009-01-05
Drop on your terminal and issue the command below:

```
sudo chown -R your_username:your_username ~/.googleearth
```

---

### Post by fragos on 2009-01-05
If you add the medibuntu.org repository you'll be able to install Google Earth and use it like any other application.

---

### Post by donkyhotay on 2009-01-05
Medibuntu is the easiest way to install certain programs such as googleearth. The information on adding the repositories is located at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kaoskorruption on 2009-01-05
I did a complete removal of Google Earth from Synaptic, I added the Mediabuntu respiratory, and then I reinstalled it. That did not work. I then did what iaculallad suggested- no luck. I have no idea what the problem is. It works fine under sudo (though I have not run it under sudo since I reinstalled as to not mess up privileges). When I run it, I just go to the command line and type "googleearth." - is there some special way that I'm supposed to open it? When I don't see the globe, I click "Server Login" inside of Google Earth, but it doesn't fix anything.

---

### Post by fragos on 2009-01-05
Removing a package doesn't remove it's configuration files. Delete the .googleearth folder from your home folder and then reinstall.

---

