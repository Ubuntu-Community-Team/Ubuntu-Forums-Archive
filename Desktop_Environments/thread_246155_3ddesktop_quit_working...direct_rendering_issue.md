---
title: "3ddesktop quit working...direct rendering issue"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mssever on 2006-08-28
I use 3ddesktop under Xorg/Metacity. After logging out and back in, 3ddeskd won't start. Here's the message I get:
```
~:$ 3ddeskd --mirror
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
``` Despite the somewhat confusing last line, the daemon exits immediately.

After searching Google, I think that this has something to do with my Xorg setup. But all the sites I found dealt with mis-configured settings--mostly video card settings. And I haven't changed anything, although I have installed all the updates that come up--including Compiz.

Does someone understand X better than I do? I have no idea how to configure hardware acceleration...especially since it worked until today!

---

### Post by SishGupta on 2006-08-28
at a terminal type "glxinfo" scroll up and tell us what it says under "Direct Rendering"

"No" means that you dont have proper drivers installed for your card or they are not set up properly.

Regardless if glxinfo gives you a yes or no for people to help you we will need to know what gfx card you are using.

---

### Post by mssever on 2006-08-28
> **SishGupta said:**
> at a terminal type "glxinfo" scroll up and tell us what it says under "Direct Rendering"

"No" means that you dont have proper drivers installed for your card or they are not set up properly.

Regardless if glxinfo gives you a yes or no for people to help you we will need to know what gfx card you are using.
glxinfo says there is no direct rendering. 
```
~:$ lshw -class display
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: Radeon IGP 330M/340M/350M
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@01:05.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:d8000000-dfffffff ioport:9000-90ff iomemory:d0300000-d030ffff irq:10
``` 
What's confusing me is that I never updated my drivers or anything, and direct rendering evidently worked before today.

---

### Post by mssever on 2006-08-28
I have no idea what the problem was, but logging out and back in fixed it.

---

### Post by _savior_ on 2006-09-11
Hello,

my comment from another thread:

> I get the same error. I think I have found out when this happens. I use XFCE (but I have also confirmed this in Gnome), and I added "3ddeskd --acquire=100" to "Autostarted Applications", so that it starts each time I log in to XFCE.

So when I first log in, it works fine. Then I press Ctrl+Alt+Backspace (or log out), and log in again. NOW I get the error above. I do not know why, but maybe it has something to do with 3ddeskd. It remains there after a logout, and possibly this causes problems with -- yeah, with what? I do not know exactly what happens if I press Ctrl+Alt+Backspace. Does the x server restart, or what? I tried to trace what happens (meddling with init scripts, including x11-common), but it does not seem to restart... Anyway, if I kill 3ddeskd before I log out (or execute 3ddesk --stop), it works on the next login, too!

So now I am looking for a way to kill the daemon process if I log out from XFCE or Gnome. Is there a way to do this?


Unfortunately, I haven't found a solution... I have added an icon to my Xfce desktop which executes "3ddesk --stop", and I use it if I want to log out Xfce and use another session, but there must be a better way...

Savior

---

### Post by mssever on 2006-09-11
3ddeskd should be killed when you log out, because logging out kills everything that you own. When you killl X via Ctrl+Alt+Backspace, I don't think that anything other than X gets killed, unless some other process notices that X is dead and starts killing stuff.

My problem that I have is that every once in a while, something (X, I think) starts incorrectly and I lose direct rendering, which 3ddesk needs. Loging out and back in usually fixes it. But I have no idea what causes direct rendering (or X) to malfunction.

You might try SishGupta's suggestion above to see if your issue is with direct rendering like mine was.

---

