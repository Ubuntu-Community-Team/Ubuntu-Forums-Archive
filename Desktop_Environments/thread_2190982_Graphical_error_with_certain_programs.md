---
title: "Graphical error with certain programs"
date: 2013-11-30
forum: Desktop Environments
---

### Post by matk1995 on 2013-11-30
[ATTACH=CONFIG]248205[/ATTACH] 
So we upgraded our server from a single core cpu to a 6 core i7, we were using ubuntu 12.10 at the time I believe and was working fine. We then decided to just do a fresh install of ubuntu for the new server, and get 13.04, we did this but as you can see in that image certain things are not how they should be. We are using remote access via vnc and the client we were using is TightVNC. 

It only seems to be doing it to the odd application, and it isnt just a problem with the screen/information we are getting, its like its an intended thing.

Any help you could possibly give us would be amazing.

P.s, if anyone knows, I have created a few .sh scripts to backup files and they worked perfectly on 12.10 however on 13.04 even though I allowed them to be executed as a program when I double click it, it just defaults to a text editor, is there a new step I am unaware of?

---

### Post by matk1995 on 2013-12-02
Going to go ahead and bump this because we really would like some info if someone has it.

---

### Post by newb85 on 2013-12-03
Don't know about your graphics issue, but I think I can help with your script issue.  In Nautilus (the file browser) click Files>Preferences and go to the Behavior tab.  There's a section for how executable text files are handled, and I believe the system default has been changed to viewing in a text editor.

---

### Post by matk1995 on 2013-12-06
Thanks man, this actually wasnt the issue, but I do thank you for trying to help out. I had to download a program (forget which one) but then changed a setting, in 12.04 how you described it worked fine, make an sh file allow it to execute but 13.04 just didnt do give the little dialogue box when opening, just instantly opened in gedit.

---

### Post by deadflowr on 2013-12-06
newb85 is right.
You have change the settings in files>preferences>behavior, as executable files are defaulted to view.
This a new setting and isn't part of precise.

---

### Post by matk1995 on 2013-12-07
As I said to newb, this wasnt MY issue, though I am sure it is possibly the answer to others, I had already made it executable, but it defaulted to gedit, never gave the info box to ask if I want to view it or execute it. Though, as I also said to newb, I fixed that problem with a Natuilus editor.

Thanks for trying to help, but the main issue really is not being able to see the terminal, surely this isnt a unique error. Fresh install of 13.04, I fail to believe that no one else has come across this error + has a fix for it.

---

### Post by newb85 on 2013-12-09
If you don't change the settings as I said, then no, you won't see that dialog asking how to open the file.

---

### Post by matk1995 on 2013-12-19
Every version prior to 13 I have found that what you said worked well, worked fine, and is the method I used, I am not an idiot. But you carrying on telling me that it was an issue to do with something it wasnt, isnt going to help anyone. 12.10, 12.04, what you said worked and is the method im sure everyone used. 13.04 no. It doesnt. It works completely differently and if you dont think thats the case then you should not be answering questions because I know more than you do.

---

### Post by QIII on 2013-12-19
There are better ways to get help than to snap at those who are trying to help you.  I'd suggest a different approach.

***To be clear, since you really had two issues in the original post:***  What you are concerned about now is that xterm is fine, but terminal is not normal?

---

### Post by matk1995 on 2013-12-20
The issue is: VNC to the server is fine, no graphical issues at all, can see all of the screen in perfect quality, once the terminal window is on screen it appears to have lines through it, as you can see, without that terminal open, that section of the screen is perfectly clear. I have also seen this effect on the "system monitor" program, bad install possibly?

---

### Post by QIII on 2013-12-20
Can you tell me exactly how you are viewing this?

Something like the following?

Physical machine -> (OS unknown) server -> KVM or Xen -> QEMU -> Ubuntu VM -> TightVNC -> Remote machine -> OS unknown -> TightVNC Viewer

---

### Post by matk1995 on 2013-12-23
physical machine: Windows 8.1 tight vnc viewer
Server machine: Ubuntu 13.04 tight vnc

---

### Post by newb85 on 2013-12-23
> **matk1995 said:**
> Every version prior to 13 I have found that what you said worked well, worked fine, and is the method I used, I am not an idiot. But you carrying on telling me that it was an issue to do with something it wasnt, isnt going to help anyone. 12.10, 12.04, what you said worked and is the method im sure everyone used. 13.04 no. It doesnt. It works completely differently and if you dont think thats the case then you should not be answering questions because I know more than you do.

I don't think you read my initial post carefully. The instructions I have were unnecessary prior to 13.  

I do still consider myself a newb; however, I have been using shell scripts since Intrepid was the latest release.

---

