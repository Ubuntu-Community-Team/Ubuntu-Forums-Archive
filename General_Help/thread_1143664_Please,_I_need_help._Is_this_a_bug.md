---
title: "Please, I need help. Is this a bug?"
date: 2009-04-30
forum: General Help
---

### Post by Mad dog on 2009-04-30
I have installed nvidia-glx-173, the recommended driver for my system. I can't activate it! No matter what I try. I try ```
sudo nvidia-xconfig
``` and absolutely nothing happens (it doesn't even ask me for my password) Also, I've entered SYSTEM>ADMIN>HARDWARE DRIVERS and attempted to activate the installed driver that way, and still nothing happens. I've tried every possible Nvidia driver, I've used envyNG, I've purged and reinstalled many, many times, in every possible way I know how. I really, really need some help please.:confused:

---

### Post by 4Orbs on 2009-04-30
I don't know if this might apply in your case, but here is what I experienced (I'm using a different version, but this post is more about the installer and Jockey).

When I clicked the button to activate the driver (in the Hardware Drivers Mgr window). First the progress bar popped open, but stayed at zero for a few minutes. I was ready to kill the process because of no activity from the progress bar, when I noticed my computer's cpu light flashing as if it was doing some work. So I left things alone, and after a few more minutes the progress bar suddenly jumped to 80% and finished the installation.

On another installation I did only a few days ago, the same thing occurred, but then Jockey crashed and the progress bar disappeared. But I left the Hardware Drivers Mgr open until the cpu light stopped flashing and rebooted (although I was never prompted to reboot because Jockey crashed). The driver was successfully installed despite the foul feedback.

---

### Post by Mad dog on 2009-04-30
> **4Orbs said:**
> I don't know if this might apply in your case, but here is what I experienced (I'm using a different version, but this post is more about the installer and Jockey).

When I clicked the button to activate the driver (in the Hardware Drivers Mgr window). First the progress bar popped open, but stayed at zero for a few minutes. I was ready to kill the process because of no activity from the progress bar, when I noticed my computer's cpu light flashing as if it was doing some work. So I left things alone, and after a few more minutes the progress bar suddenly jumped to 80% and finished the installation.

On another installation I did only a few days ago, the same thing occurred, but then Jockey crashed and the progress bar disappeared. But I left the Hardware Drivers Mgr open until the cpu light stopped flashing and rebooted (although I was never prompted to reboot because Jockey crashed). The driver was successfully installed despite the foul feedback.

Unfortunately this doesn't seem to be the case for me. It just says 0% for about 1 sec., closes the dialog window automatically and nothing else happens. 

I copied the error message I get when I reboot after installing the driver:

[error message]
[B]Ubuntu is running in low graphics mode

[/B]The following error was encountered. You may
need to update your configuration to solve this.

(EE)NVIDIA(0): failed to load the nvidia kernel module!
(EE)NVIDIA(0): *** ABORTING ***
(EE) Screen(s) found, but none have a usable configuration.
[/error message]

Does this have something to do with my monitor maybe?

---

### Post by Mad dog on 2009-04-30
bebump

---

### Post by 4Orbs on 2009-04-30
Actually, that sounds almost exactly like what happened to me when Jockey crashed. I was reading another thread and the man said it happens because the servers are unusually busy now, and Jockey doesn't have the patience to wait for a timeout (or something like that).

I suggest giving the Hardware Drivers Mgr one more try to activate the driver. And when it crashes, don't mess with it, just wait. You can open the system monitor while waiting and see if there is any network activity showing or cpu activity. Regardless wait ten minutes or more before rebooting... but do reboot. The longer you are willing to wait, the more likely the installation will occur. I mean, don't wait more than a few days, but 15 or 20 minutes should assure that you finally bust through the server and connect to the download.

If you have previously installed the driver manually with the .run package from nvidia's website, you should run the uninstaller for it before trying to activate the driver from Hardware Drivers Mgr.

PS. If it crashes, you will never see the progress bar or any indication of activity and you will never receive notice of success or the prompt to restart. Just pretend all is well and reboot when you can't wait any longer.

---

### Post by Mad dog on 2009-04-30
Anyone? The problem is not that I can't download or install the driver, it's that I can't use it.

---

### Post by NFblaze on 2009-04-30
Are you sure its the right nvidia driver for it?
I'd double check that.

Also, I dont think anything is supposed to happen when you type:
sudo nvidia-xconfig

when i typed it on my system it just repeated the prompt. And then I was able to set my graphics to use the restricted drivers. Then it said I was not supposed to use the default screen manager...but Nvidia X Manager.

---

