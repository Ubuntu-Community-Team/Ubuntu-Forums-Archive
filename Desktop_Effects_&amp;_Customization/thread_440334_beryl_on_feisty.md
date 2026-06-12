---
title: "beryl on feisty"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by iiyama on 2007-05-11
HI

I am new to Linux systems so i apologize in advance if i don't fully understand.
Yesterday a carried out a dual boot install of Ubuntu 7.04 (feisty). 

Today i attempted to install beryl using the following guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) 

installation seemed to progress without any obvious errors. 

however beryl- manager does not seem to start,
when i try to start it manually using alt +f2: i receive an error that their is know such directory (or something very similar)

i am able to stare emerald and beryl-setting program fune but not beryl manager. 
I have also noticed after carrying out the installation my shutdown buttons have diapeared?

How can i get beryl-manager to work?
Any way og getting shutdown buttons back?

i would apriciate any help or insights. 
my graphics card is radeon express 1150 (in a dell inspiron 1501 laptop)

thanks for reading

---

### Post by lynxus on 2007-05-11
Try installing beryl from the Add/Remove menu in ubuntu , then choosing it from the menu once installed.

IE: Search Add/remove on all repos for " beryl "

Not sure what that tutorial told you to do to install, But i suppose installing it from the install app program shoudl setup everything correcty.

---

### Post by Ozeuss on 2007-05-11
i don't have an ATI card, so i really don't no the specifics for that card. but i first suggest that you install the regular version from the repos initially. did you cross check that tutorial with another tutorial/thread?

---

### Post by iiyama on 2007-05-11
hi 

Thanks for quick replys. 

Lynxus-
I have installed beryl manager from install/uninstall area. I can now see the program running in the system panel( red diamond). 

However there has been no change to my themes in any way. i have tried opening emerald theme manager to select a theme but nothing happens 
I have also tried to change in the login session to XGL  mode at the login screen. I have also selected beryl as window manager.

Ozeuss- I did not cross check thread. It work for others so i assumed it was ok. Wish i had now:( 


Any help will be great 
Thanks

---

### Post by sowelie on 2007-05-11
Try starting beryl-manager from the terminal and check the output when switching to beryl window manager.  What kind of video drivers do you have installed.  Are you using AIGLX or XGL?

---

### Post by strumluff on 2007-05-12
iiyama, I'm pretty sure that in order to get that card to work you will need to use the ATI proprietary drivers.
Make sure they are installed from System -> Adminstration -> Restricted Drivers Manager.

Next thing you need to do is install XGL and create a session for it as Beryl will not run under AIGLX at the moment unless you use the open-source drivers, which I believe are not supporting your card.

After you need to install Beryl, but only the 0.2.0 version I believe as the version in the universe repo does not work yet, I'm not sure if the status of this has changed yet.

The reason why beryl-manager may not be starting is because you haven't actually installed it, if you aptitude install beryl, it won't install beryl-manager, so you have to do it yourself:
```
sudo aptitude install beryl-manager
```
You can get your shutdown buttons back by including a couple of lines of code in your startxgl.sh script, I recommend you start over though and follow this guide as it caters for everything:

Here's a good guide to follow: [Linky]("http://ubuntuforums.org/showpost.php?p=2564461&postcount=13")

Any other problems, just report back.

---

### Post by iiyama on 2007-05-12
Hi 

thanks for all ur suggestions . Sadly I could not get beryl to work.
i think the codes are messed up because of previous attempts.
I am now going to try and reinstall system and try from scratch. 

will update how i get on

take care

---

### Post by AZcat on 2007-05-12
It was pointed out in various threads within this forum that the version of Beryl in the universe repositiory does not work with ATI graphic cards.  You need to install the Beryl directly from the Beryl Project website.  The answer (#13) given in the following thread gives very clear direction on how to install xgl-Beryl:

[http://ubuntuforums.org/showthread.php?t=427947&page=2&highlight=XComposite+extension](http://ubuntuforums.org/showthread.php?t=427947&page=2&highlight=XComposite+extension)


And you can find instructions on how to install the fglrx driver in the following link:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Best of luck.
AZcat

My setup: duo boot XPpro+Feisty + ATI Radeon 9700 pro running xgl-beryl.

---

