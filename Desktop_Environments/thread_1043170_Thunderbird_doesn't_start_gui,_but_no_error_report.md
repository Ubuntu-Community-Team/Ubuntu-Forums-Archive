---
title: "Thunderbird doesn't start gui, but no error reported"
date: 2009-01-18
forum: Desktop Environments
---

### Post by Antonio Tavares on 2009-01-18
I have a laptop running Windows on one partition and Ubuntu 8.10 on the other. Since one year ago, I'm using Ubuntu 99% of the time. I have Thunderbird 2.0.0.19 installed and I was sharing the profile on both operating systems with no problem.
Unfortunately a month ago a problem with Thunderbird in Ubuntu started appearing. Sometimes I pressed the icon to start Thunderbird and nothing appeared. 2 processes were running (thunderbird and thunderbird-bin). After rebooting in Windows and back to Ubuntu it was running again. But since one week ago I can't start the email interface even going to terminal and typing thunderbird -safe-mode. The process doesn't appear doing ALT-TAB, but it always shows in the process list like follows:
```
tota@portota:~$ ps -edaf | grep thunderbird
tota     13235  9842  0 15:04 pts/0    00:00:00 /bin/sh /usr/bin/thunderbird -safe-mode
tota     13248 13235  0 15:04 pts/0    00:00:00 /bin/sh /usr/lib/thunderbird/run-mozilla.sh /usr/lib/thunderbird/thunderbird-bin -safe-mode
tota     13252 13248 22 15:04 pts/0    00:00:01 /usr/lib/thunderbird/thunderbird-bin -safe-mode
tota     13266 13166  0 15:04 pts/1    00:00:00 grep thunderbird

```

I've googled this as much as I could and gone through the "[_Standard Diagnostic_]("http://kb.mozillazine.org/Standard_diagnostic_-_Thunderbird")" with no results. Reinstall doesn't work. If I delete the profile, Thunderbird allows me to reconfigure a new one and then the window dies. I see nothing on system logs, and no errors on the terminal.
Thunderbird still works on Windows, but I want to avoid using it since the time Ubuntu 8.10 brought real support for 3G network connections. It's very annoying having to reboot several times a day.

Can anyone help me avoid reinstalling Ubuntu Intrepid?
Thunderbird is essential to me and I can't trust any other email client (Evolution for example doesn't install on Windows).

---

### Post by adamlau on 2009-01-19
Open a terminal and run thunderbird from there. Any error messages printed to stdout?

---

### Post by albinootje on 2009-01-19
> **Antonio Tavares said:**
>  Reinstall doesn't work. If I delete the profile, Thunderbird allows me to reconfigure a new one and then the window dies.

Is there anything else wrong or not working on your Ubuntu installation ?

Can you do a forced file system check ?
```

sudo touch /forcefsck

```
and reboot.
Remove the /forcefsck after the file system check.

By the way, if you're really desperate, and nothing seems to work with Thunderbird, then you can also run Thunderbird with Wine in Ubuntu, not ideal, but it should work.

---

### Post by Antonio Tavares on 2009-01-19
> **adamlau said:**
> Open a terminal and run thunderbird from there. Any error messages printed to stdout?
No message at all. The terminal just stays hanged waiting for the program completion (as normal on graphical programs like Thunderbird).

---

### Post by Antonio Tavares on 2009-01-19
> **albinootje said:**
> Is there anything else wrong or not working on your Ubuntu installation ? 

I tried the file system check on Windows (it is a FAT32 partition) but it didn't make any difference.

In fact I noticed something strange. When I moved down the mouse, the pointer seemed to disappear under the screen. This is a problem I was having recently. I investigated the screen configurations. I have the ATI Catalist drivers installed, and I use an external screen positioned up of my laptop. For some reason, the configuration was like it was a big screen including the 2 screens. I removed the second screen and rebooted the X server. After that Thunderbird was working properly! :)

Thank you albinootje, it seems you made me find the problem! I'm still note absolutely shore that this was the real issue, but for now it's certainly working. I just wonder why ALT-TAB selector window wasn't showing Thunderbird? It should, even if the window was out of the present screen. I suspect that this is a bug of XORG, or the ATI driver.

Anyway, this problem is solved. Now I have to find a way of using 2 screens in Ubuntu, but better just one than none!

---

### Post by Antonio Tavares on 2009-01-19
You said:
> **adamlau said:**
> Ubuntu 8.10 Minimal + XFCE 4.6 = :popcorn:

I'm using Gnome, but maybe I should give XFCE a try to have 1 or 2 screens according to fixed or roaming use of my laptop in a more organized way (no programs disappearing and no desktop items disappearance)? :confused:

---

### Post by adamlau on 2009-01-19
Definitely give Xfce a try. Works best with a minimal install as even fewer GNOME libraries are depended upon that way.

---

