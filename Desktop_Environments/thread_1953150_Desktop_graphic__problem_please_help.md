---
title: "Desktop graphic  problem please help"
date: 2012-04-05
forum: Desktop Environments
---

### Post by Scholar-code on 2012-04-05
Hello everyone.

I have just tried ubuntu 11.10 and 12.04 on my new acer 5755G with intel core i3-2330M and nvidia optimus geforce gt540M cuda 1gb.

Live cd works wornderfully. But, when I install the os, graphic doesn't work, like when I minimize a black thick box moves towards launcher, and when I right click and select change desktop background, there no launcher icon size available, it is availabe in Live CD when testing the OS, please help me, I like ubuntu.

I am just confused why it doesn't work when I install the os, but, it works fine with live CD?

---

### Post by Curtis6767 on 2012-04-05
I'm assuming you're using 12.04 LTS Beta. If not, then ignore the following.

Open a Terminal with Ctrl + Alt + T

at the prompt enter this code:

```
sudo apt-get update
```Enter your password when asked for.

Allow update process to run all the way through to completion. You will know this when there is a tally of how many MB's were downloaded with the time it took and the average speed of the download.

Close the terminal. Restart your system.

Then click on the Gear Icon at the top right of your screen. 

In the drop down menu, select System Settings.

In the window that opens, select Appearance.

If the "Look" tab is not selected by default, select it.

Launcher icon size should be at the bottom. Mine is set to 48 by default.

Hope this helps

---

### Post by Scholar-code on 2012-04-06
No.
I have updated it twice, I strongly suspect, It has to do anything about my graphic driver, only thing bothers me is why does live CD works fine.

maximise minimize feels like sh**

and there no look tab?


Please somebody help.

---

### Post by Curtis6767 on 2012-04-06
Which version are you on? 

Have you gone into System Settings and then clicked on Additional Drivers

When you say that Maximise/Minimise doesn't feel right, just exactly what are you maximising and minimising and what is happening with this? 

When I minimise my browser, FireFox, it is sucked into the launcher, but not as a black box.

Try logging out and then back in, but before you type in your password, click on the Ubuntu icon on the small password window. What do you see there?

Have you downloaded the Restricted extras package?


```
sudo apt-get install ubuntu-restricted-extras
```Once you've done all this, then you'll have a better starting point from which your issue may be better diagnosed.

You can also try doing a search of the forums to see if others have had the same problem and their problem was resolved.

---

