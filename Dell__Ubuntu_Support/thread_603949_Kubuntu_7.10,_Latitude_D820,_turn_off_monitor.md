---
title: "Kubuntu 7.10, Latitude D820, turn off monitor"
date: 2007-11-05
forum: Dell  Ubuntu Support
---

### Post by kevin79 on 2007-11-05
I'm using a Dell Latitude D820 with Kubuntu 7.10. I have an Nvidia card with the proprietary drivers installed. Is there any way to manually turn off the lcd screen so that it isn't on when I walk away for an extended period of time? My boss used to be able to do it with a Latitude D600 using Ubuntu 7.04 with and ATI card but he isn't sure how, other than using fn + f8. He's not sure if it was a driver install, something specific to the ATI card or what. Is there a way for me to do it?

---

### Post by dacap06 on 2007-11-07
> **kevin79 said:**
> I'm using a Dell Latitude D820 with Kubuntu 7.10. I have an Nvidia card with the proprietary drivers installed. Is there any way to manually turn off the lcd screen so that it isn't on when I walk away for an extended period of time? My boss used to be able to do it with a Latitude D600 using Ubuntu 7.04 with and ATI card but he isn't sure how, other than using fn + f8. He's not sure if it was a driver install, something specific to the ATI card or what. Is there a way for me to do it?

Well, I can get you close.  Read through this entire message before you take action.

First, open your system settings, click on the Monitor and Display icon, then click on the power saving tab.  Ensure Power Saving is enabled.  Change the delay from the default 20 minute setting to whatever you like.  Save your settings with the apply button.  You may now dismiss the System Settings window.

Second, right-click on your task bar panel and select the Add Applet to Panel menu entry.  Scroll down about a third of the way and select the Lock/Logout buttons applet.  Now add the selection to your panel.  You may now dismiss the Add Applet window.  Position the lock and logout button applet wherever you like on the task panel - I like it right next to the K Menu button.

Finally, right click on your desktop and select the Configure Desktop menu entry.  Select the screen saver icon.  Select the Blank Screen screen saver and then press the apply button.  You may now dismiss the Configure Kdesktop window.

Now that you have set everything up, a single button press of the "lock" button on your task panel will engage the screen saver immediately and the back light will turn off after the time delay you chose.  It also adds a modicum of security because you must type your password to disengage the screen saver.

Another alternative is to use the back light controls on your keyboard, if you have them, although it will take repeated presses to reduce the backlight setting to 0%.  My Dell 5100 has a blue function button I can press in combination with the up arrow or down arrow to increase or decrease the brightness of the backlight.  On Dell Latitude and Inspiron laptops, those buttons are driven using the i8kutils package.  All you have to do is install it.

Best of all, you can use both solutions at the same time!

DaCAP

---

