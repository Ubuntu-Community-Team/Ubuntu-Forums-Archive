---
title: "X configured for 1280x800 but KDE only 1024x768?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Geshtar on 2005-10-16
I am first time kubuntu user and I am installed it on a Dell 700m laptop which has a native resolution of 1280x800 which was correctly detected by the X configurator and is the only resolution listed in xorg.conf.  However in KDE the resolution according to the KDE control panel is only 1024x768.  Based on how it looks, I am inclined to believe KDE.

Anyone have an idea on how to tell what is really is going on and how to fix it?

Thanks in advance,

-Geshtar

EDIT: I just got a 1024x768 wallpaper and put it as my background centered; it took up the whole screen, so KDE is definetly running at 1024x768 even though it should be 1280x800.

---

### Post by CAE on 2005-10-16
You might need to make sure that the refresh rates listed in your xorg.conf (/etc/X11/xorg.conf) are appropriate for your monitor. For that, check the laptop manual as they should be listed there.

---

### Post by mekgp on 2005-10-16
I'm encountering the same issue as Geshtar... When using fglrx, it really doesnt seem to matter what /etc/X11/xorg.conf states. The resolution is stuck on 1024x768 EVEN when the .conf file has ONLY 1280x800 listed with the proper refresh rates. When I go into <System Settings><Display>, choices are the 1024x768 and "lower/smaller" only... I didnt have this issue in Hoary on this laptop. :confused::confused:

---

### Post by MechR on 2005-10-16
Go to System -> Package Manager (Adept).

Go to Adept -> Manage Repositories, and enable the Universe repositories (right click -> enable on the two relevant lines, which you'll be able to find by reading through the file). Save and then Fetch Updates.

Find 855resolution in the list of packages. Read the program description, and install it. Then go and read the file specified by the description, and it'll tell you how to configure 855resolution for the res you want, and how to have it autorun on startup.

Btw, you may need root-level permissions to edit the relevant files. For that, go to the KDE menu -> Run Command, click Options, check "run as a different user," and choose to run as root with your regular password. Then type "kate" (without quotes) in the Command field and click Run. That opens a text editor window that'll be able to save the changes you make to system files.

Good luck!

---

### Post by xristos on 2005-10-16
I had the exact same problem with you guys .
I own an Acer 1524WLMi and in my manual it doesn't say what the monitor's specifications are :(
So I was stuck with 1280x768 until I found a webpage from a guy that had the same laptop with me that stated the correct refresh rates and other options for the xorg.conf file .
So I guess you have to find the correct refresh rates from somewhere , either laptop manual or web !

---

### Post by mekgp on 2005-10-16
Thank you MechR...unfortunately, the program wouldn't even recognize information from this particular laptop.  If I understand correctly, this machine is chipset is an 828 based system??!!??  :confused::confused::confused:

---

### Post by Geshtar on 2005-10-16
Thanks, mechR, looks like that is on t he right path anyways.  I am having some trouble with it though.  I went through the steps you suggested and it says when I run 

/etc/init.d/855resolution start

that It was succesful for the mode I selected and put in
/etc/default/855resolution, but the resolution does not change immediately.  I killed the X server with Ctrl-Alt-Backspace and when X/KDE restarted, it was still at 1024x768.  I tried rebooting too, but it also just came back to 1024x768.  On gentoo, I am used to using rc-update to have things run at boot, I do not know the equivalent in kubuntu either.....

Any further ideas?

Thanks,
Geshtar

---

### Post by Geshtar on 2005-10-17
bump!

---

### Post by MechR on 2005-10-20
Sorry for not replying, I haven't been around in a while ^_^'  Unfortunately, that's about all I know anyway :(

---

