---
title: "We fixed problem #1 but created problem #2."
date: 2013-06-15
forum: Desktop Environments
---

### Post by jfbooth on 2013-06-15
Running Xubuntu 12.04 with XFCE 4.8.

Problem #_2_:
On boot or 'restart', I get the XFCE login screen. I provide p/w, ... then get the same screen again. Log in again and am at desktop where everything works OK.

During that restart, I notice that all those messages that scroll along as you restart ... before the log in screen, are severely scrunched vertically. Before, they scrolled up in normal size 'terminal' text.

I THINK I must be running two XFCE 'sessions' ... or sumptin(?).  Also .. system overall seems noticeably sluggish.

Problem #2 MOST LIKELY has to do with problem #1 which is another thread.  After a lot of help from a Moderator, we thought we had it fixed ... at least that is how it looked .... until I did a restart and observed problem #2.  I tried to reopen/append to the other thread, but another moderator told me to open a new thread.

If you want to know about problem #**1**, I will summarize it now ( the entire thread is here [http://ubuntuforums.org/showthread.php?t=2153840](http://ubuntuforums.org/showthread.php?t=2153840) )  _summarized and slightly edited_ :

I said:
> On startup, I get the following after logging into XFCE:

No running instance of XFCE4 - PANEL was found. Do you want to start the panel ......
and the options to cancel or execute. Clicking execute gives:

Modifying the panel is not allowed. Because the panel is running in kiosk mode, you are not allowed to make changes to the panel as a regular user.

and a close button. Clicking on Close gets me to the desktop. Please advise on correcting this condition and achieve normal operation.
Thank you in advance.

moderator said:
> Hey.
looking about and this is the suggested solution from several forums:
log out of xfce
ctl+alt+f1 to get a console
in terminal enter:

```
sudo rm -rf $HOME/.cache/sessions
```

ctl+alt+f7 (GUI) and log back in.

All now should be back to defaults, so have to reset all.

I said:
> Did entire list of instructions. NO startup errors .. all original problems appear fixed.

=================
There is likely one more element to this .. it is yet ANOTHER thread ... but I won't summarize it here as it is too lengthy.  Here is the thread, though:

[http://ubuntuforums.org/showthread.php?t=2154115](http://ubuntuforums.org/showthread.php?t=2154115)

So, ... I hope I have made it clear enough .. and someone can help me get it straightened out.  Thank you in advance.

EDIT: ... So, while waiting ... did a full shutdown and then powered up and the problem did not repeat.  Gone and done fixed herself.  Thanks anyway. :redface:

---

