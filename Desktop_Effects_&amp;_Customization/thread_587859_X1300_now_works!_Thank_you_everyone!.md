---
title: "X1300 now works! Thank you everyone!"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by DrQuincy on 2007-10-23
After hours and hours of faffing around thanks to the good folk at this forum Compiz Fusion is now running on Gutsy on my X1300 Pro.

This is what worked for me - I'm not saying it's perfect but it worked.

If you find the RDM and the Screens and Resolutions option does nothing for you download the ati-driver-installer-8.41.7-x86.x86_64.run file from ATI's site.

Run:
sudo chmod +x ati-driver-installer-8.41.7-x86.x86_64.run

Run:
sudo ./ati-driver-installer-8.41.7-x86.x86_64.run

And follow the installer using the recommended settings.

Run:
aticonfig --initial

Then restart.

Then run: 
sudo apt-get install xserver-xgl

Then run:

sudo apt-get install compizconfig-settings-manager

Then restart X

Then login again and run:

compiz

Then go to System > Preferences > Advanced Desktop Effect Settings

I hope that helps someone else out; I've had a real hard time trying to get my card to work.

Once again, thanks to everyone who helped me.

One final thing, it is a little slow even on Fast rendering.  Any suggestions to boost performance?

---

