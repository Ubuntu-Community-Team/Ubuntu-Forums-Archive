---
title: "Update-Manager won't display to desktop"
date: 2006-07-13
forum: Desktop Environments
---

### Post by StayPuft on 2006-07-13
When I get my update-manager notification, and I click on the icon, it asks me for my password and then it shows the status of the update-manager checking the repositories and downloading the information. But then the update-manager itself never shows up on my desktop. The icon stays grayed out for about 3-4 minutes and a mouse rollover says "A Package manager is working". But after the 4 minutes or so the icon comes back to normal and I go through the same process again. This is a brand new installation of Ubuntu on an i386, and the update-manager worked for the first 3 days before it stopped. However, if I type 'sudo update-manager' in a terminal window it will come right up on the display....any ideas?

Thanks in advance for any help.

---

### Post by bojzi on 2006-07-13
Try to right-click on the Update Manager icon when it shows up and selecting the first option.
I had the same problem because I right clicked on the icon once and made it just upgrade (without looking at the packages) and the Update Manager remembered that as the default when I double-click the update icon.

---

### Post by PriceChild on 2006-07-13
update-manager should only work with super user privelages....

Also, please run it with "gksudo" instead of "sudo" (gk being a graphical sudo) So that you don't run into errors later down the line.

---

