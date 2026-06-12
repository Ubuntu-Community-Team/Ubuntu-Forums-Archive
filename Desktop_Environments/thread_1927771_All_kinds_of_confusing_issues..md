---
title: "All kinds of confusing issues."
date: 2012-02-18
forum: Desktop Environments
---

### Post by exzou on 2012-02-18
I am using an acer aspire 5516 1.76 gb of usuable ram and an AMD athlon tf - 20 dual booting vista basic and xubuntu (all my issues i am experiencing happened in ubuntu as well). as i am typing this i cant right click to use spell check, im unable to close the web browser because the entire upper bar (where the minamize and maxamize buttons are) when i try to save a document it wont save anything i have done in the past 2 hours. (i email them and redownload them to get it to work) the system feels like it hangs.

i am fairly new to linux but i am very comfortable in windows and as much as i cant stand windows anymore, i am tempted to go back. i am a student and cannot afford to constantly be losing information from my term papers or re install the os every time i have a problem. this instalation of xubuntu has been on my laptop for maybe 4 days and just started doing this again. any help would be greatly appreciated. if there is more info you need just let me know.

---

### Post by 3Miro on 2012-02-18
My guess is that the issues that you have come from your video card Radeon X1200. For many years ATI had no support for Linux and while AMD has made huge efforts to improve ATI support, the older graphics cards do not work very well. IIRK AMD recently dropped support for X1200 completely and many people with those cards are experiencing problems. Unfortunately this has nothing to do with Linux or Ubuntu.

There is very little that you can do. You can try installing Ubuntu 10.04 LTS, but it will have support for only about a year. Debian 6 will have longer support, but Debian is not as friendly to install.

Note that I may be wrong and your issues may be elsewhere. If you explain your problems carefully someone may be able to help.

---

### Post by exzou on 2012-02-18
I started using Ubuntu in an old custom build desktop (radeon video card) and to this day have had no problems. about six months ago i started using linux on my laptop. All was good for a long time. about a month ago i started having issues with the laptop.

 when i would be in libre office sometimes the upper bar that contains the "x" button would disappear completely preventing me from closing libre. when this happened anything i tried to save in libre would not save and i had to use other methods to export it and modify the document later. this only happened when i used libre. never with anything else. however, if i used libre and had this issue this issue would occur with ALL other programs. 

i got tired and eventually boot n nuked my hdd, filled it with zeros, and proceeded to reinstall windows and linux. i had played around with other distros and decided i like the xubuntu distro a little bit more than the new unity option. i have only had this distro installed for about 4 days. ive only installed a few after market programs. the problem is now occuring again but it doesnt matter what program i start using it still occurs. in the past i restarted my pc and everything worked (i noticed when using ubuntu it almost seemed as though the problem occured when A. i was using libre. and B. when i ran multiple programs.) now when im using xubuntu it does not matter if restart the problem remains. at the moment i am actually logged into windows and no problems. ( i dont know if that matters at all.)

---

### Post by exzou on 2012-02-18
i just realized i waited about 3 days to do the updates and now im having problems after the updates. is there a way to remove updates and see if the problem is solved?

---

### Post by 3Miro on 2012-02-18
- while desktops are pretty standard, laptops often times come with unique hardware and/or BIOS. Windows that comes with the laptop has also been tweaked, but generally speaking, Linux works worse on Laptops.

- the issues with the ATI drivers cover old cards only, the new ATI cards 4xxx and later work pretty well for regular use.

- you say you have trouble with Libre office, but Libre often times has trouble with saving non-native formats. Can you save documents in a format native to Libre like .odt as opposed to .doc

- Ubuntu and Xubuntu use the exact same Libre office, however, the Windows Manager is different (compiz as opposed to xfwm4). Trouble with Libre would be the same on both systems, however, the disappearing X buttons shouldn't happen on both.

- I don't know of a way to undo updates.

---

