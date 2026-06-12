---
title: "LIVE USB boot customization"
date: 2009-01-03
forum: General Help
---

### Post by Blutrille on 2009-01-03
All using 8.10
I have used unetbootin to create the original drive. this drive does not retain the changes so i used this drive to access the ubuntu live usb boot thumb option that come with 8.10. I have had great success with most of the edits besides the boot process. 

I would like to boot to the login screen not auto boot into an account that seems to be invisible to the users and groups. the account is called ubuntu in the home folder. 

how can i make edits to the boot process and retain the live usb instead of having to make a full install.

I have been directed to [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I have ran into a snag early on.

while trying to create the chroot environment using 

     sudo debootstrap --arch i386 gusty chroot

I am then prompted to enter the root password... this seems to work successfully although it is followed by 

E: No such script: /usr/share/debootstrap/scripts/gusty

What might cause this error? Also just after this step the directions instruct that I should install MySQL after generic linux is installed. Is the reference to install server or client or both?

---

