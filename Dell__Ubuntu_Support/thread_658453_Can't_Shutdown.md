---
title: "Can't Shutdown"
date: 2008-01-04
forum: Dell  Ubuntu Support
---

### Post by crazyfish666 on 2008-01-04
I can't seem to shutdown. After [this]("http://ubuntuforums.org/showthread.php?t=653379") was fixed I found when I tried to shutdown that the clicking the poweroff fellow in the top right gives me only five options, Log Out, Lock Screen, Switch User, Suspend and Hibernate. No Shutdown or Reboot. I also still arrive at a a black terminal-like screen when I power up and have to log on there and start the visual interface by typing "startx". I don't particularly mind this but I figure it might be related. Any ideas on how to be able to shutdown??

---

### Post by N8K99 on 2008-01-04
1) you can just press the power button until the computer shuts down.
2) You can open a terminal and 'sudo shutdown -h now' (look at the man shutdown and see that this option halts the system after it has been brought down)
3) Hillbilly method: just pull the plug out the wall. :-)

---

### Post by crazyfish666 on 2008-01-04
> **N8K99 said:**
> 1) you can just press the power button until the computer shuts down.
2) You can open a terminal and 'sudo shutdown -h now' (look at the man shutdown and see that this option halts the system after it has been brought down)
3) Hillbilly method: just pull the plug out the wall. :-)

I was always under the impression that 1 and 3 were bad for your computer. I really don't know about 2, does it take the time to shut everything down properly??

---

### Post by johnw2007 on 2008-01-04
The last time I had to shut down using the power button after the system had hung it went into fsck when it restarted and went through repairing what seemed like hundreds of bad nodes on the disk. Luckily everything still seems OK but it was scary accepting all those repair prompts!

---

### Post by NGSG on 2008-01-04
a fast solution, is simply:
                CTRL+ALT F5
 to get into text mode, and then loggin and issue:
            /sbin/shutdown -h now
hope that helps.

---

### Post by freddyp on 2008-01-04
Some reported a similar problem in Feisty Fawn 7.04.  If I remember correctly, the fix was to:

   1. Go to the top menu bar and choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Name Chooser below it is checked as well

The Shutdown and Restart options should will magically reappear!  Not sure if this fix also works in Gutsy 7.10.  See if this helps!

---

### Post by crazyfish666 on 2008-01-05
> **freddyp said:**
> Some reported a similar problem in Feisty Fawn 7.04.  If I remember correctly, the fix was to:

   1. Go to the top menu bar and choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Name Chooser below it is checked as well

The Shutdown and Restart options should will magically reappear!  Not sure if this fix also works in Gutsy 7.10.  See if this helps!

Yes, I have seen this solution, but when I go into System -> Administration I don't have a 'Login Window' option in the menu so I can't even try that one. I imagine there is something different for Gutsy, but I can't find it.

---

### Post by freddyp on 2008-01-05
Let's check and make sure the 'Login Window' is properly selected as an option for the System>Administration menu.

Try --

1.  Right click on Applications>Edit Menus
2.  Scroll down to System>Administration and make sure the Login on Windows is selected in the Items right pane.

If it's not you won't have the option under System>Administration.

---

### Post by gbrainin on 2008-01-05
To answer your question, yes, the shutdown command (assuming it runs successfully) does shut the system down properly.

---

### Post by NHmomma on 2008-01-05
Hi,

I am having this problem as well!

I am on Gutsy also.  I tried the right click on apps button, but when I went to the administration tab, there was no login to windows even in the menu to choose from!

Still having problems... anyone?

Having my computer boot up to a black screen with text prompts to start up is not an option...  I need to fix this.

Thanks!

Carrie

---

### Post by freddyp on 2008-01-06
Not sure why the Login Window option is not available using the Applications right click edit menu process, but let's try opening a terminal window and typing in --

sudo gksu /usr/sbin/gdmsetup

I think the standard launcher for the Login Window simply runs this command.  This should launch the Login Windows Preference panel and from there you can select the Local tab, Check the box next to Show Actions Menu, and make sure Include Host Name Chooser below it is checked as well.

NOTE:  These changes on the Login Windows Preferences panel are simply to try and fix the original problem asked about in this thread -- missing Shutdown or Reboot buttons in menu -- not a fix for the lack of ability to add the Login Window option using the right click edit menu process.

Hope this helps!

---

### Post by millermobile on 2008-01-10
"**System**"
 '-> "**Administration**"
  '-> "**Login Window**"

Go to the "**Local**" tab, and make **BOTH** options under "**Menu Bar**" are checked (set to true).

You don't have to restart, just check the boxes and your shutdown menu will instantly regain both "shutdown" and "restart".

This works on both **Feisty** and **Gusty**.

---

### Post by raquo on 2008-01-12
> **freddyp said:**
> Some reported a similar problem in Feisty Fawn 7.04.  If I remember correctly, the fix was to:

   1. Go to the top menu bar and choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Name Chooser below it is checked as well

The Shutdown and Restart options should will magically reappear!  Not sure if this fix also works in Gutsy 7.10.  See if this helps!

I've just experienced same problem with disappearing buttons and, to make it worse, although i could press "hybernate", hybernation would always fail, and shutting down using terminal command would bring errors. But now it all wokrs great. Thank you! (I'm using GG **7.10**) :popcorn:

---

### Post by crazyfish666 on 2008-01-12
> **freddyp said:**
>  login

I don't see the option there to select.

---

### Post by crazyfish666 on 2008-01-12
> **freddyp said:**
> 
sudo gksu /usr/sbin/gdmsetup


Didn't do anything. No error, nothing.

---

### Post by craigmac on 2008-04-14
Thanks freddyp, your fix worked perfectly for me. After having just regressed to Gutsy after a couple of weeks of Hardy hiccups - the experience was sub-optimal so I decided to reinstall Gutsy - I had no shutdown options. 

Thanks again.

---

