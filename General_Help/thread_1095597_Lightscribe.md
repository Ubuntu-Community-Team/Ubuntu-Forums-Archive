---
title: "Lightscribe"
date: 2009-03-13
forum: General Help
---

### Post by AndyP79 on 2009-03-13
Hi All,
 I downloaded from the Lighscribe website the packages need to make my burner work. They seem to be in the opt file that they needed to go to, but...now what? I don't see a program in my Menu, and can't seem to find much on google. I am going to keep looking, but maybe one of you can beat me to it, and then others can see also what to do.

Thanks

---

### Post by AndyP79 on 2009-03-13
Okay, i found this, but can anyone decipher this into plain English for me please? I have no clue what this is saying, though it seems like it would be something positive?


[http://vitalbodies.wordpress.com/2008/07/14/getting-lightscribe-to-work-in-ubuntu-hardy-heron/]("http://vitalbodies.wordpress.com/2008/07/14/getting-lightscribe-to-work-in-ubuntu-hardy-heron/")

---

### Post by banana jama on 2009-03-13
if you can't see an program icon in your menu this might mean that you have to create one (thats what i had to do). here look at my screen shot. go to system---> preferences---->main menu and accessories on the right click new items and fill the following information.:

Type: Applications
Name: LightScribe (Simple)
Command: "/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler"  (without the "")
comment:Simple CD/DVD Labeler

to get the picture place click on the launchpad (board with spring on bottom) and place```
/opt/lightscribeApplications/SimpleLabeler/content/images/LabelWizardIcon.png  
``` in the browse bar.

after that everything should be set you'll now see light scribe in applications---> accessories

---

### Post by AndyP79 on 2009-03-13
I tried this, but nothing happend, no application in the menu

---

### Post by banana jama on 2009-03-13
maybe instead of putting what i put in Command you should put your file directory to the opt file. what's the name of the program you downloaded for lightscribe. if i can remember to get mine to work i had to download to separate things first the lightscribe system software to get functionality for lightscribe on your computer then 2) the simple labeler. did you download both? the instructions i gave you  are only for the simple labeler the system software doesn't need an icon.

---

