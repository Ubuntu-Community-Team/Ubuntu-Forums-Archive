---
title: "Firefox will not run"
date: 2009-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by herold on 2009-11-23
I had Firefox installed on Ubuntu 9.04 on a Dell Vostro 1500, and it worked without a problem until a week or so ago.  I had not used it for a couple of weeks, and when I tried to start Firefox last week, I got a message, "Could not launch application
Failed to execute child process "/media/MEDIADIRECT/Documents and Settings/Administrator/My Documents/My Videos/desktop.ini"  (No such file or directory)"

Windows XP is on my internal hard drive, and Ubuntu (and GRUB) are on a WD My Passport usb  hard drive.  I had expected to have GRUB on the internal hard drive, but since it was loaded onto the usb drive, I just plug in the usb drive before booting the laptop.

I searched for MEDIADIRECT on my computer, and concluded it was only on the Windows drive,  I have no idea why Firefox is looking for it.  (I also have Firefox on Windows XP, but I do not expect that to have anything to do with Firefox on Ubuntu, since I boot either into Windows or Ubuntu.  

I thought perhaps that I could get away from the problem by upgrading Ubuntu 9.04 to 9.10, so I did that yesterday.  While Ubuntu will not start Firefox, it will connect to the internet through ethernet, and I did the upgrade through the ethernet cable.  Since I did the upgrade to 9.10, the place on the upper bar that formerly had the Firefox icon now has a red circle with a slash across it.  If I click on the red circle, I get the same error message I got in 9.04, with the reference to MEDIADIRECT, no such file or directory.

I tried reinstalling Firefox via Synaptic, with no change in results.  (It is now Firefox 3.5.5)

I just finished searching for mediadirect on Ubuntu forums, and see that I could get into a lot of trouble by pushing the Mediadirect button, the one with a little house symbol on it, but I am sure that I have never touched that button, not even once.

What do I need to do to get Firefox to be usable again?

---

### Post by wilee-nilee on 2009-11-23
I think the easiest way to do it would be to add this ppa to your apt/sources .list then update and see if there is a firefox update.
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)
This I believe will install shiretoko which is FF 3.5.
The next thing is not remove Firefox completely and down load from Mozilla the regular package.

This is the daily build ppa as well.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by herold on 2009-12-02
Thanks for your response, Wilee-nilee.  I have been away for a few days, and just got back to this.  I looked up some more information on Shiretoko that you suggested, and concluded that it was an older version of Firefox than what I was using, so I decided not to try that right away.  Somewhere on the forums, I saw references to Launcher, and read the Man pages on that, and the GNOME Desktop User Guide.  I decided to find out whether Launcher was the problem.

I clicked on the red circle with the slash across it (where the Firefox icon used to be) and came up with a small Launcher window.  In it, where the command line had a reference to an obviously incorrect location on my hard drive that has Windows on it, I entered "firefox."  (Without the period or quotation marks.)  I closed that window, and clicked on the red circle with the slash again.  Firefox opened.  Success!  Again in the Launcher properties window, I clicked on the "icon" button.  A menu of icons came up, and I clicked on the one for Firefox.  Then I closed the windows.  My Firefox icon was back where it had been originally, and I could use it to launch Firefox.  Another success!

I do not know how I came to have a directory from Windows in the Command line, or how I got to have the red circle with the slash across it in place of the Firefox icon.  But if it happens again, I will have a better idea of how to fix it.  Maybe this information will help someone else, too.

---

