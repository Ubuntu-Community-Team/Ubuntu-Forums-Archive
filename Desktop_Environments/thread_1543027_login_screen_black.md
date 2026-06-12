---
title: "login screen black"
date: 2010-07-31
forum: Desktop Environments
---

### Post by swdinesh on 2010-07-31
I installed ubuntu Lucid on my tx2000 laptop.
When the system is ready to log ask for the login the screen is blank.
If I start to press some <ctrl>+<alt|>+f1 (I see the classic shell login) then I press <ctrl>+<alt|>+f7 I can see the regular graphic login and I can start to use my ubuntu.

Can anyone help me to fix the initial graphic screen as it must be?

thank you 
Alex

---

### Post by derrickman on 2010-08-01
I have the same problem with the login screen except for when I use CTRL + ALT + F7 it is still black and I can't do anything.  This problem is most likely my fault because I attempted to change the default login screen.  I typed "gdmsetup" in the terminal and the startup screen has been black ever since.  Is there any way to return the startup screens to default from the CLI, I can get there.

By the way this is my first venture into Linux and I love it.  Just wish I did more good than harm to myself.:(

Thanks for any help with this issue.

Edit:  I was able to login by watching the screens when I swapped from the terminal and the black login screen, the login screen would flash for only a second.  My screen is still black with me logged in to the system.  Is there any way to revert my settings to default?

---

### Post by swdinesh on 2010-08-01
Hi derrickman, 

if you [ress <control>+<alt>+Fn you can access as some different terminals.
F1 to F6 are CLI terminal (the shell) F7 is the graphic interface and F8 is the error console where you can find the error messages to stderr.

so if you press <control>+<alt>+F7 you have to use the graphic interface. 
If you don´t probably you disable the X server and you have to switch back to runlevel 5 (but this is another kind of problem) ... I´d try to reconfigure X as described here [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/) 

cheers

---

### Post by derrickman on 2010-08-08
Thanks

I will give it a try and see what happens.

By the way the monitor is a LCD TV and I loaded Ubuntu up on her computer using my monitor originally.  When I moved the computer back to her room and powered up I got the black screen of death.

Edit:  Tried the steps listed in the link and still the black screen.  Does it have something to do with the LCD TV monitor because it shows fine on my monitor.  After entering the command "sudo dpkg-reconfigure xserver-xorg" and putting in the password nothing happened, just moved down one line.  Any more suggestions would be greatly appreciated.

Thanks for all your time with this.

---

### Post by derrickman on 2010-08-09
This is strange.  My guess is that my daughter's LCD TV is not supported.  It is a Sansui.  I moved the computer back to my monitor which is an Acer and it booted fine.  Oh well, any other ideas than the ones listed here in this thread will be appreciated but it looks as though I will have to buy here another monitor.

Thank you for all your time.  I love Ubuntu.  It just has a steep learning curve.:KS

---

### Post by mogadon on 2010-08-12
I am a new user and am having a similar problem. The trigger appears to be one of the user accounts actually logging out (as opposed to "switch user"). After this the system goes to a black screen and no amount of ctl+alt+fn does anything. Eventually I am forced to reboot the machine by pressing the off button.
I am dual booting with XP and I used the wubi installer. The machine is a Dell Dimension desktop with 1Gb of ram and an 80Gb harddrive.
I am not very techy so I have not done any complicated personalization or anything like that. I did install an Nvidia graphics driver, but the problem occurred before and after that install, so that's neither the cause nor the cure.
Thanks for any suggestions.

---

