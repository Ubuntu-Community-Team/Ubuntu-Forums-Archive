---
title: "Messed up Xorg install"
date: 2006-10-13
forum: Desktop Environments
---

### Post by jnicita on 2006-10-13
I'm hopoing someone can help me out. I messed up my XOrg 7.0 install somehow and am not sure how to repair it.

I have 2 monitors hookoed up to a ATI X200 (radeon) card and succsessfully got it setup and had everything running great.

I was reading somewhere about changing the boot splash screen and downloaded the gnome-desktop-manager thinking that it was going to help me change the "boot-up" graphics (the screens where ubuntu is loading, and listing all the inits and scans of the drives, usbs, etc, etc). I ran the gnome thing without much thought at picked a cool graphic that I had saved as a background. When I rebooted, my monitors went white, (I saw the hour glass for 1 second) and then they flickered and when white, black, white, black, white. I know I messed it up. But I ssh'd to my box from another machine and copied my xorg.conf file to a saved, and moved my xorg.conf.original.0 back to my xorg.conf. It didnt work as a fix, but it stopped my monitors from freaking out by puting the config to one monitor and ignoring the other, and at this time I got to read the error that my gnome desktop manager (gdm) was crashing and that it is going to drop back to the default manager (I can hit okay, and then a gnome desktop logon screen apears where I can choose the other managers to log onto and such. 

Can someone tell me how to re-install the gdm package or whatever I need to do to repair what I messed up. I wish to restore it the way it came when first installed (the gdm and logon procedure). I did run the logon manager from the preferences area and pointed it back to the default logon theme, but it still has the crashing gnome manager.

Any help would be apperciated, at least I can actually log onto the system with the old config, (I saved the dual head one so that I can copy it back, but until I get the gdm fixed I cant use it because the two screens are so diffrent that they conflict and the frequency or something isnt correct).

Thanks

JN

---

### Post by jnicita on 2006-10-15
bump?

---

### Post by taurus on 2006-10-15
Maybe

```
sudo aptitude update
sudo aptitude remove gdm
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by jnicita on 2006-10-15
taurus thanks, but that didnt do it.

Maybe I should try to explain what I think is happening so someone might be able to help me.

Like a idiot, I used the gnome-desktop-manager or whatever its called to modify the login theme. I actually thought I was modifying the page graphic that is shown during the inital booting of the system (i.e. the screen with all the dmesg's on it).

Anyways, now I get a message on my login saying that the "greater applicaiton is crashing". I am prompted to hit okay to try another program, and what loads looks like a older version of GDM, it has all the normal login functions, in that I can choose to login to gnome, or a terminal failsafe, etc, etc. However, logging in with this doesnt send the correct xorg.conf configuration as my xinerama config with my dual screen display is all jacked with a mirrored screen 0 on screen 1, and resolution is messed up as well. 

I logged into the machine and forced my logon to the non x logon, logged onto the machine with start x and it seemed like that worked correctly (I guess at this point its not using the "greater" applicaiton. I assume that this greater application is the GDM portion, but I am not sure. The graphical user log on and authenticaiton routines are messed up. I have used the apt-get remove of gdm ubuntu-desktop followed with a apt-get install gdm ubuntu-desktop. Didnt help, I also used the apptitude remove gdm - apptitude install gdm as mentioned. Still the same xwindows ugly drawn box saying "greater application is crashing" hit okay to continue or load a diffrent applicaiton or whatever it says. IS GDM the greater application? (I guess I better understand that first), I think it is, so I am sure its possible that uninstalling and then re-installing the gdm isnt working because of configuration files that remain after the un-install. Anyways, Im sure this is real simular to the issues that happen with one tries to load the kde stuff into a gnome installed version. Again, any help? I believe that the synaptic package manager allows me to do a COMPLETE uninstall (it says including all configuration files). Im going to give that a try on the GDM package now. Since I have used startx from the command line and logged out and not seen the GDM issue, I am going to assume that I can uninstall and reinstall the GDM package from within XWindows as it is a applicaiton that runs with X rather than X itself.

Again, any help would be greatly apperciated, as the machine I jacked up is my primary work desktop. (I know, what a idiot). At least I got a desktop to work with while I try to figure it out..

Thanks again...

JN

---

