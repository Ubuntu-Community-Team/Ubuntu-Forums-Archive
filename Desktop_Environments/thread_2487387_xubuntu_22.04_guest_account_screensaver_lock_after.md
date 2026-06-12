---
title: "xubuntu 22.04 guest account screensaver lock after 5 minutes"
date: 2023-06-02
forum: Desktop Environments
---

### Post by petehorm on 2023-06-02
Hi,
I work at a school and use the xubuntu minimal install and lightdm guest account for students.  On 18.04 it didn't timeout and lock the screen when the monitor shuts off.  On 22.04 it blanks the screen and locks the guest account after 5 minutes of inactivity.  It asks for a password and there is none which means you have to switch user and create a new guest session.  That seems to be a known issue.

I usually copy the .config and .local folders to /etc/skel of a stock user to make the guest account desktop look the way I want to.  I have tried:
1.  Various Power manager settings to not lock the screen.
2.  I have disabled screensaver and screensaver lock from starting up at boot.
3.  I have tried changing some cli gsettings  commands regarding idle times to false. 

It still blanks the screen and locks the guest account after 5 minutes.

The only thing that did work is when I set  my  stock user to presentation mode and I take the .config and .local folders and copy those to the /etc/skel folder.  That seems to stop the guest locking from happening, but it now keeps the screen on all the time.

Can someone please tell me what program is causing the guest account  to blank the screen and lock the guest account and
what I can do to disable locking?  I am at a loss as to what is causing this.

Thanks so much for any advice you might have!!

pete

---

### Post by TheFu on 2023-06-03
I don't user Xubuntu, but google found this answer:

To have the screen blank after an idle period, 
```
$ gsettings set org.gnome.desktop.session idle-delay X
```
where X is in seconds.
3600 would be 1 hour.  I'd use 10 minutes for screen blanking.

To have the screen lock after an idle period, 
```
$ gsettings set org.gnome.desktop.screensaver lock-delay X
```
where X is in seconds.

Might be smart to have the lock delay at least 10 seconds longer than the idle-delay, but maybe an hour or longer.  Depends on the opportunity for mischief by random people in the location.  There is some mention that the lock-delay begins once the idel-delay has been met, but IDK if that is true.

I don't know if this works.  No Gnome here.

---

### Post by petehorm on 2023-06-04
I think I had tried that, but I will check tomorrow at work and report back.

Thanks very much for the response!!

---

### Post by TheFu on 2023-06-04
> **petehorm said:**
> I think I had tried that, but I will check tomorrow at work and report back.

Thanks very much for the response!!

It was the only reasonable solution that I found, assuming it even works. 
I looked in the Xubuntu documentation and didn't see anything obviously related to the _screen lock_ time.

---

### Post by aljames2 on 2023-06-04
In the Screensaver Preferences, I had tried to up the time for the screensaver but it would always go back to 5 minutes.
Finally, I figured out you can't type the number in, instead you have to use the spinner (plus sign) to up the idle time.  I set mine to 30 minutes and restarted and haven't had a problem since.

I haven't tried disabling it, but if I were testing this, I would try:
Settings -> Setting Editor -> xfce4-power-manager -> lock-screen-suspend-hibernate = False (uncheck)
and restart.  I would expect this to disable those features.
This may not be good for security if the computer is left unattended.

---

### Post by TheFu on 2023-06-05
> **aljames2 said:**
>  
Finally, I figured out you can't type the number in, instead you have to use the spinner (plus sign) to up the idle time.  I set mine to 30 minutes and restarted and haven't had a problem since. 

Ah, GUI programmers.  One place I worked, the main GUI programmer only used the mouse, no keyboard, unless absolutely necessary, so all the accelerated keyboard shortcuts inside any program he touched never worked.  Anything that could accept typing events were never handled, unless it was a textenty field, specifically.  Nobody had said anything to him before I got there and started harassing him about it.  The only thing that got him to fix it was when I brought a blind person in and had the programmer watch him try to use the GUI.  The pity effort was the only effective method to get him to carefully test that aspect.  2 months later, the small company hired a QA manager and he was finding dialogs where only the mouse worked for 6+ months.

I have to say, it really wasn't the programmers fault that nobody in college or for the prior 2 yrs that he worked at the company had gotten after him to fix this.  A pretty GUI is what sells products, not 100% working programs.  At least in the specific industry their program was used.  Hooking up both the mouse and keyboard to the event notification for a widget isn't hard, but it has to be done.

Don't get me started about tab-order of fields.  Tabs should flow logically from entry widget to the next one. They usually are ordered by the order the widget was added to the window/frame.  Often, for small 1-2 item entry frames, it isn't a big deal, but when there are 5+ inputs on a single page, the order can be maddening.

---

### Post by petehorm on 2023-06-06
Hi,  The issue was related to the xfce4-screensaver.  I apt removed it, and added xscreensaver.  xscreensaver blanks the screen but doesn't lock you out in the guest account.   Hope this helps someone experiencing the same thing I did.  Still won't power down the monitor after the allotted time, despite the power settings in both xcreensaver and power manager telling it to turn off,  but one problem at a time.  :)  Thanks again for the input.

---

### Post by petehorm on 2023-06-06
Very true about security, but these are computers in a school lab that are basically serving as internet kiosks, thus the use of the guest account.  The kids are instructed to logout of the guest account at the end of class.   Thank you very much for your input!  It is greatly appreciated.

---

### Post by TheFu on 2023-06-06
> **petehorm said:**
> Hi,  The issue was related to the xfce4-screensaver.  I apt removed it, and added xscreensaver.  xscreensaver blanks the screen but doesn't lock you out in the guest account.   Hope this helps someone experiencing the same thing I did.  Still won't power down the monitor after the allotted time, despite the power settings in both xcreensaver and power manager telling it to turn off,  but one problem at a time.  :)  Thanks again for the input.

xscreensaver comes with a few different programs.  xscreensaver-command is a CLI tool for setting options.  xscreensaver-demo is a GUI for setting options, including lockout times and screen blanking.  I know the VESA drivers for AMD don't support turning off the display, but the AMD drivers do.
You can probably put a wrapper around it using
```
# Turn off blanking
xset s off &
xset -dpms &
/usr/bin/xscreensaver-command -exit

```

```
# Turn on blanking
# Enable the screensaver
/usr/bin/xscreensaver &

xset +dpms &
xset s on &
```

That's how I do it for some programs that I don't want the screen saver to interrupt.   There's another program, which I've never used and don't know if it runs on Linux, called "caffeine".  May be helpful. IDK.

---

