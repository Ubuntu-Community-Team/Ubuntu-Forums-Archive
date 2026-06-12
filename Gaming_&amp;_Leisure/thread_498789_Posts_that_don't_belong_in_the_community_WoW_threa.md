---
title: "Posts that don't belong in the community WoW thread."
date: 2007-07-08
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2007-07-08
Puppet:  have you installed the video drivers for your system?  What kind of video card do you have?

Also please post the output of:

```
glxinfo | grep rendering
```

---

### Post by puppetj on 2007-07-08
my card is an nvidia geforce fx go6500 my output is below, but your forgetting the other issue:
"1st off i have wine installed and for some reason i couldnt just double click on the installer.exe, when i was able to on another pc with unbuntu w/ wine installed and had to go by term/cmd install, how do i fix this, i have removed/uninstalled & reinstalled wine and still happens."

AND WHAT DO I DO TO GET THE DRIVERS INSTALLED, BECAUSE I GOT DRIVERS FROM NVIDIAS SITE, BUT TO INSTALL THEM IT SAYS I NEED TO EXIT X(GUI), HOW DO I DO THAT? AND THE DRIVERS I INSTALLED FROM AUTOMATIX, SAYS THERE ARE INCOMPATIBLE. 







Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by hikaricore on 2007-07-08
Don't use Automatix to install drivers.
If you must use a script I suggest [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

Also if you are using Feisty use the Restricted Driver Manager.

---

### Post by puppetj on 2007-07-08
UPDATE : I DID THE ENVY INSTALL NVIDIA DRIVER, BUT NOW I CANT GET BACK INTO X (GUI) I GET A BLUE SCREEN WITH FAILED TO START THE  X SERVER...BLAH BLAH
SO NOW WHAT???


what i'am i using Restricted Driver Manager. for??? also i have wine installed and for some reason i couldnt just double click on the installer.exe, when i was able to on another pc with unbuntu w/ wine installed and had to go by term/cmd install, how do i fix this, i have removed/uninstalled & reinstalled wine and still happens."

---

### Post by puppetj on 2007-07-08
but it didnt work like a charm for me?! remember? so what do i do?

as for the wine link you gave me, you miss understood my issue with wine problem i'am having it's not working:

i have wine installed and for some reason i couldnt just double click on the installer.exe, when i was able to on another pc with unbuntu w/ wine installed and had to go by term/cmd install, how do i fix this, i have removed/uninstalled & reinstalled wine and still happens."

---

### Post by puppetj on 2007-07-08
ok, but this iisue still needs fixing:

i have wine installed and for some reason i couldnt just double click on the installer.exe, when i was able to on another pc with unbuntu w/ wine installed and had to go by term/cmd install, how do i fix this, i have removed/uninstalled & reinstalled wine and still happens."


AND WHY WOULD UNINSTALLING & REINSTALLING HELP?   WHAT HAPPENS IF IT DOESNT?

---

### Post by puppetj on 2007-07-08
ok installing  didnt help, neither didnt reinstalling, even tried manual nothing working!!!

---

### Post by hikaricore on 2007-07-08
I think you need to calm the hell down.

I believe the entire reason the installer was crashing is due to your video card/drivers.
Getting the game installed while this is still an issue is pointless and not an option.

Also often in WINE "double clicking" on installers and apps doesn't work properly, many others have found this out before and it's most often suggested while you're setting up or running a new app to do it from a terminal.  A little searching for the reason why you're having issues instead of just reposting here over and over again might help, and be of more benefit to you.

And this thread really isn't the appropriate place for help installing video drivers.

Take it to the general help forum before I merge all your posts here into a thread and dump it there.

---

### Post by puppetj on 2007-07-08
i'am calm, but wine, works on the other pc this way, no reason why it should be the same on this pc, i didnt do anything different, i had to repost this b/c noone was seeing it, as two issues, now i tried this dpkg-reconfigure -phigh xserver-xorg , since i couldnt get back into x, it gives a list of things to cg=hoose, it was default on vesa, i choose that and my rez of 1152x768 restarted got gui login, logged in but now everything is gone from the m desktop, no menus, nothing

---

### Post by puppetj on 2007-07-09
please, what can i do to get these issues fixed, i cant even get back into x (gui) now

---

### Post by puppetj on 2007-07-10
> **Sammi said:**
> Did you try this in the CLI:```
sudo envy -t
```Then choose option number 6. "Clean the installation of any Nvidia driver".

Finish by choosing number 1. "Install the Nvidia driver".



And dude. This is not the tread or room for driver support.

Well, i was told to use Envy....by hikaricore if you see in past response , this has to with wine and a driver issue,and it has to do with the drivers installed right along with wine, people can tel use, this but went this go wrong they care to not help all that much, and that why i'am pissed.

Yes, i tried this, none of the cmd line/ text menu options help still can get drivers installed, and still cant get back inti x (gui)


so i'am i out of luck, do i need to reinstall, this becoming similar sounding to a windows response, heheheh

---

### Post by hikaricore on 2007-07-10
> **puppetj said:**
> Well, i was told to use Envy....by hikaricore if you see in past response , this has to with wine and a driver issue,and it has to do with the drivers installed right along with wine, people can tel use, this but went this go wrong they care to not help all that much, and that why i'am pissed.

Yes, i tried this, none of the cmd line/ text menu options help still can get drivers installed, and still cant get back inti x (gui)


so i'am i out of luck, do i need to reinstall, this becoming similar sounding to a windows response, heheheh


So you followed the instructions EXACTLY?  You first removed, then reinstalled the drivers with envy?

Looking back I'm starting to think that Automatix may have borked something with your video drivers.  I've rarely seen Envy fail.

Run envy again using only the remove option.  This will uninstall any nvidia drivers aside from the default nv driver, then do the following from command line:

```

sudo aptitude install build-essential linux-source linux-headers-$(uname -r)

wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run

chmod +x NVIDIA-Linux-x86-100.14.11-pkg1.run

sudo ./NVIDIA-Linux-x86-100.14.11-pkg1.run

```

Follow the onscreen prompts, noting any errors.
Please PM me or post questions in a different support thread until we can resolve your issue.

--Aaron

---

### Post by hikaricore on 2007-07-10
You should have read his posts.  That's not going to help him.

---

### Post by puppetj on 2007-07-11
for

sudo aptitude install build-essential linux-source linux-headers-$(uname -r)

"uname" do i put my login name there?

i tried either way

then the:

wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)


i ran and got:
failed..... Name or service not known   (and yes i checked the spelling and used the upper case when need

so i didnt go any farther..... but as for "Automatix may have borked something with your video drivers."
not sure, but i did follow the unstall/restore to uninstall that process.

---

### Post by hikaricore on 2007-07-11
(i asked you to stop posting in this thread)

> sudo aptitude install build-essential linux-source linux-headers-$(uname -r)
^ this is exact and does not need changed.  if you ran it this way and let it install everything you should be fine.

On to the nvidia drivers.

Download it from here:

http: //www.nvidia.com/object/linux_display_ia32_100.14.11%20.html


If you need to do this from command line use lynx:

```

sudo apt-get install lynx
lynx http://www.nvidia.com/object/linux_display_ia32_100.14.11%20.html
```

Use your arrow keys to navigate down the page to this link **NVIDIA-Linux-x86-100.14.11-pkg1.run** hit **d** to download.  Then save it when it completes, you will be prompted to save after it downloads.

Then follow the instructions from that point.

---

### Post by puppetj on 2007-07-11
if i can't post in this thread, then how and going get this issue fixed, which is how i got in this sitauion in the 1st place? Sorry but really need your help, i'am not try to be an ***, just everything is gone to hell....well i tried what you asked, but the reason why both links aren't downloading is b/c i'am not getting any internet connection?!  Well i did had to run a bash script to install my wifi drivers, because they didnt work by default.
So unless there is a better fix , should i just reinstall???

---

### Post by hikaricore on 2007-07-11
> **puppetj said:**
> if i can't post in this thread, then how and going get this issue fixed, which is how i got in this sitauion in the 1st place? Sorry but really need your help, i'am not try to be an ***, just everything is gone to hell....well i tried what you asked, but the reason why both links aren't downloading is b/c i'am not getting any internet connection?!  Well i did had to run a bash script to install my wifi drivers, because they didnt work by default.
So unless there is a better fix , should i just reinstall???

I'm done with this.  Up until this point you haven't really been asking, you've been arrogantly demanding, and ignoring all of us telling you to take it elsewhere.  The world where you came from that taught you to act rash and annoyed about your computer problems to get support is not here, we are not paid to assist you we do this with only our spare time, perhaps you don't understand the purpose of this community. I offered to let you PM me for personal assistance, I directed you towards the help forum, and time after time you ignored it. You blindly try anything that will take 2 steps out of a process, I suggested Envy (i said exactly: *If you must use a script* which means it's one possible option) and you dove in head first without even researching how to use it.   Nevermind the fact that there are hundreds of threads around the forums about installing Nvidia drivers.  You couldn't be bothered to read them, or sanity forbid MAKE ONE asking for help in an appropriate place.  Now we find out you have no internet connection...  You know bash scripts work from command line too right?  But at this point I suggest maybe you have messed up your system bad enough to where it would make sense to reinstall.  Mind you I could walk you through getting back to the GUI with the "nv" or "vesa" driver, but what's the point?  You would get back and be right back here asking for more help with your video drivers.  So yea, I give up, someone else can help you, I'm sorry but I'm not dealing with it.

**DO NOT** post _in this thread_ again with your video and network connection issues.

---

### Post by puppetj on 2007-07-11
> **hikaricore said:**
> I'm done with this.  Up until this point you haven't really been asking, you've been arrogantly demanding, and ignoring all of us telling you to take it elsewhere.  The world where you came from that taught you to act rash and annoyed about your computer problems to get support is not here, we are not paid to assist you we do this with only our spare time, perhaps you don't understand the purpose of this community. I offered to let you PM me for personal assistance, I directed you towards the help forum, and time after time you ignored it. You blindly try anything that will take 2 steps out of a process, I suggested Envy (i said exactly: *If you must use a script* which means it's one possible option) and you dove in head first without even researching how to use it.   Nevermind the fact that there are hundreds of threads around the forums about installing Nvidia drivers.  You couldn't be bothered to read them, or sanity forbid MAKE ONE asking for help in an appropriate place.  Now we find out you have no internet connection...  You know bash scripts work from command line too right?  But at this point I suggest maybe you have messed up your system bad enough to where it would make sense to reinstall.  Mind you I could walk you through getting back to the GUI with the "nv" or "vesa" driver, but what's the point?  You would get back and be right back here asking for more help with your video drivers.  So yea, I give up, someone else can help you, I'm sorry but I'm not dealing with it.

**DO NOT** post _in this thread_ again with your video and network connection issues.


FINE IF YOU DON'T GIVE A ****, AND CAN'T FIX MY ISSUE, THEN I'LL GO BACK TO WINDOWS
AND FORGET LINUX ALL TOGETHER, I GUESS LINUX IS JUST A HYPED UP BS, THANK YOU FOR BEING A ******* AND NOT HELPING ME, YOU PROBABLY DON'T CARE ME 1% LITTLE ME LEAVING AND NEVER COMING BACK, BUT THIS IS THE THIRD TIME I WAS TOLD TO GOTO HELL, WELL I'AM ANTI-UUBUNTU  NOW THANKS TO YOU!

---

### Post by hikaricore on 2007-07-11
Removed from the community wow thread and merged here.  I'm sorry for this everyone.

---

### Post by FNDII on 2007-07-11
intel 3.0 hyperthread
2gb ram
Asus extreme x800


I would assume i have the latest version of wine, I installed it yesterday.

I thought I had the Restricted drivers but i just reset the xorg file and re applied the ATI x800 fix. Now i dont see the restricted drivers.

---

### Post by puppetj on 2007-07-12
> **hikaricore said:**
> Removed mine and puppets posts and put them in another thread.

I appologize for my response but I didn't feel he was trying to be helped.


I'am wasn't trying to be helped?, lol your the one that told me to piss off and go somewhere else, your the reason why people stay away from linux!

---

