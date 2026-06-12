---
title: "ALT-TAB stopped working"
date: 2008-08-28
forum: Desktop Environments
---

### Post by kbrill on 2008-08-28
I cant seem to get it working again.  It works if I switch on Comp-Wiz but if I turn that off I get nothing.

Any Ideas?

---
Update:Sorry, of course I mean "ALT-TAB"

---

### Post by arch0njw on 2008-08-28
Have you checked your keyboard shortcuts under system preferences to make sure they are still activated?

Sorry if that is a silly question.

---

### Post by prshah on 2008-08-28
> **kbrill said:**
> It works if I switch on Comp-Wiz but if I turn that off I get nothing.

If you have assigned Alt+Tab to one of the fancy switchers (Ring, Shift) in Compiz Settings Manager, when you disable compiz, the Alt+Tab will not work. 

To clear this, start Compiz; then run the Compiz settings manager (System-Preferences-Advanced Desktop Effects Settings) and choose Window Management, then reset bindings to defaults in Ring Switcher, Shift Switcher and Application Switcher. Make sure all are enabled _before_ resetting to defaults, you can disable whatever you don't want after resetting to defaults.

Now, turn off compiz with System-Preferences-Appearance-Visual Effects-None, and check if your Alt+Tab binding is activated.

---

### Post by gren12345 on 2008-11-13
This thread helped me get Alt-Tab to switch between windows working again.  It was just disabled in System > Keyboard Shortcuts.  The action I had to change was:
Window Management > Move between windows with pop-up

---

### Post by aftabnaveed on 2010-03-12
I had the same problem and it worked it for me too :-) thanks

---

### Post by ogoforth on 2010-05-20
Compiz setting suggestion got me working.  Thank you!:guitar:

---

### Post by Cincinnatux on 2010-06-07
I had the same problem today with ALT-TAB and, indeed, going to the keyboard mapper proved an effective approach.  My question is:  how did this get 'broken'?  I ran the usual updates this morning and not only did it wreck the keymapping, but Compiz hard-locked on me once (I had to power off, because keyboard inputs were not responding at all) and failed in one subsequent rebooting, though I was able to use preferences to manually shut down Compiz that time.  It seems to be working okay now (yet another reboot), but now Ubuntu refuses to mount USB devices.  

What (other than the user, of course) could have so screwed up my system?  I'd take credit for being the problem here, but all I can say I did was allow Synaptic to update my software automatically.

FWIW, booting into the dark side of my hard drive (Windows Vista) did not indicate any hardware problems (e.g., mounting a USB drive worked normally, video card seemed to work fine, etc.).

---

### Post by harun3d on 2012-07-02
if you have disabled ring switcher, switch on application switcher to reenable alt tab

---

### Post by oldos2er on 2012-07-02
Old thread closed.

---

