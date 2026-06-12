---
title: "no progress bar on file copy"
date: 2012-08-28
forum: Desktop Environments
---

### Post by andycivil on 2012-08-28
I'm doing a drag and drop operation from one USB drive to another, but it behaves weirdly. After complaining about a couple of special files and links (expected) it seemed to finish immediately, even though there was around 15 GB of data. As I suspected, when I tried to eject the destination drive, I got an error that there was a pending operation.

Clearly, the actual copying is going on in the background, but I have no progress bar to tell me how the job is going, which is pretty unfriendly. How could I have done the copy in such a way as to get a proper progress bar? I don't know if it's gong to take five minutes, or five days!

---

### Post by papibe on 2012-08-28
Hi andycivil.

While the copy process is being done, a new window is created that shows you the progress. It is called 'File Operations'

Try switching between windows to find it (using alt tab). Alternatively, you could use super+1 to bring up all nautilus windows (file manager).

Let us know how it goes.
Regards.

---

### Post by andycivil on 2012-08-28
Hi papibe, I apologise, I found the file operations dialog a few seconds ago. This is the problem with not having a task bar - it was created underneath everything else, and there was absolutely NO indication on the screen that it was there. I'll know for next time. (Although I'm not sure that progress popups generate taskbar entries anyway, can't remember.)

Meanwhile, I accidentally clicked on "cancel" instead of "skip" on one of my uncopyable files, which aborted the copy, so I'm giving up for now and I'll try it again in the morning.

Thanks for the answer.

---

### Post by andycivil on 2012-08-28
I played around with Alt-Tab and I found it very tricky to pull the progress bar to the front. If you just do Alt-Tab, you see the desktop and the nautilus icons to choose from. If you keep holding Alt and wait on the nautilus icon, it expands to show all the windows including the file operations one. I discovered by trial and error that only the Right-cursor key would let you choose one of these. Up/Down did nothing, and Left took you back to the desktop again. Eventually I managed to get the file operations to come to the front long enough for me to drag it out from underneath the main nautilus windows. It doesn't seem very intuitive: I don't see your average joe finding that.

---

### Post by jeanjean84 on 2012-08-31
Same problem for me in Unity-2d in Ubuntu Precise 12.04.1 and Nautilus 3.4.2 ...

I found a workaround to recover the progress window (when minimized it is just impossible to find again...): wmctrl

wmctrl -l List the windows being managed by the window manager.
wmctrl -a <WIN> Switch to the desktop containing the window <WIN>, raise the window, and give it focus.

See wmctrl(1) - Linux man page [http://linux.die.net/man/1/wmctrl](http://linux.die.net/man/1/wmctrl)

It does the trick! But it is just a workaround!

There are 2 related bugs (at least...):  [https://bugs.launchpad.net/unity-2d/+bug/891169](https://bugs.launchpad.net/unity-2d/+bug/891169)  &  [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/849733](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/849733)

I miss Lucid on that one.... :-(

ctrl-alt-tab does not work at all for me (nor does alt-tab...)...

---

