---
title: "Change default session in autologin"
date: 2011-10-16
forum: Desktop Environments
---

### Post by prebbish on 2011-10-16
Hi!

I have just installed Ubuntu 11.10 on a brand new HTPC. I have also installed XBMC for the home theater part, which works very well.

But now I would like to change the login session to xbmc, I have installed XBMC stand-alone package and when I log out I can easily change session to xbmc. So far so good.

But since Unity i quite different from earlier versions I cant figure out how to make the XBMC-session default with autologin so I dont have to type my password every time.

Really hope someone is able to help, thanks in advance.

- Preben / Prebbish

---

### Post by spipe on 2011-10-17
Bump, and same problem here, except I'm trying to do it with fluxbox.

Auto-login refuses to go to the user's choice of desktop environment.  That might not be a big deal, but as things stand, the full-screen application that's supposed to run at login time gets polluted by the big button bar on the left edge of the screen.

This is not good for a kiosk setup.

---

### Post by prebbish on 2011-10-18
I have also learned that when logging into the XBMC session I cannot log out again, I have to reboot to change session.

---

### Post by mcduck on 2011-10-18
At the moment there is not graphical tool for setting the default login session when using automatic login.

However changing it by hand only requires editing a single line in a config file. Edit the */etc/lightdm/lightdm.conf* -file and change the "*user-session=ubuntu*" line to point to which ever session you want as default. (the name of the session is the same as what appears in the Sessions menu in the login screen, although in lower case.)

---

### Post by spipe on 2011-10-18
:-) mcduck saves the day!  Thank you.

---

### Post by prebbish on 2011-10-18
McDuck: Do you know anything about XBMC?

Because it would be kind of stupid to set the default session to be XBMC before I know how to log out again :D

---

### Post by mcduck on 2011-10-18
> **prebbish said:**
> McDuck: Do you know anything about XBMC?

Because it would be kind of stupid to set the default session to be XBMC before I know how to log out again :D

Something, although I haven't used it on Ubuntu. 

My XBMC setup does have an "Exit" option in the very same menu where the shutdown option is (Accessed from the bottom left corner, at least on the default "Confluence" skin). That should log you out.

You could also go to System->System->Power Saving, and change the "Shutdown function" to "quit"

...if all else fails, no need to worry about getting stuck in XBMC. The magic key combination SysRq+k will kill whatever is running on current virtual console. If you do that from desktop (or XBMC) it will restart X and get you back to login screen. And you can also always use Ctrl-Alt-F1 to log into a TTY and edit the lightdm config from there to switch the default session or disable automatic login.

(Be careful with the SysRq shortcut, it will not give any running programs a chance to save what they are doing.. So don't use if you have anything imporant open unless nothing else is responding...)

---

### Post by prebbish on 2011-10-18
The thing is just that the exit button shuts down xbmc, shows the wallpaper for a second or two and then starts xbmc again. I use the Transparency skin, but the log out button is simply missing. If I use the standard skin (forgot the name) the logout button is there, but doesn't work...

Edit: If you cant help me with xbmc I will try the xbmc forums instead. Thanks alot for the help with autologin though :D

---

### Post by sgtkwol on 2011-11-02
I just installed xbmc-live and it auto logged in for me. Make sure you have an xbmc user set up.

---

