---
title: "Ubuntu desktop freezing after open Chrome/Firefox - Seems to be NVIDIA  Related"
date: 2022-09-19
forum: Desktop Environments
---

### Post by gustavodartagnan on 2022-09-19
Hello,

I'm using Ubuntu desktop 22.04 in a Lenovo  Notebook model Ideapad Gaming 3i that has an NVIDIA® GeForce® GTX 1650 video card.
It was a little dificult to install, because ubuntu wasn't able to boot after install finishes, but I started in recovery mode and was able to install the NVIDIA latest official driver v515.65.01.
After the NVIDIA driver install everithing works great!
The problem is that after power off or reboot it freezes when opening Chrome or Firefox. 
Need to hard reset the notebook and start again in recovery mode and reinstall the diver to have it working again, until next reboot.

Need help to figure out what changes after rebook that broke the configuration.

Thanks in advance!

---

### Post by &amp;KyT$0P# on 2022-09-19
Does the issue occur if you start the browsers without hardware acceleration?

For Firefox you can try starting it in [Troubleshoot Mode]("https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode") as a test.  For Chrome try running it with [FONT=Courier New]--disable-gpu[/FONT] command-line option.

---

### Post by gustavodartagnan on 2022-09-19
I've tested without hardware acceleration and both started ok.

---

### Post by &amp;KyT$0P# on 2022-09-19
> **gustavodartagnan said:**
> I've tested without hardware acceleration and both started ok.

Then I would say that is the solution.  See [here for how to disable it in Firefox]("https://support.mozilla.org/en-US/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration"), [here for how in Chrome]("https://www.howtogeek.com/412738/how-to-turn-hardware-acceleration-on-and-off-in-chrome/").

---

### Post by gustavodartagnan on 2022-09-19
> **halogen2 said:**
> Then I would say that is the solution.  See [here for how to disable it in Firefox]("https://support.mozilla.org/en-US/kb/troubleshoot-extensions-themes-to-fix-problems#w_turn-off-hardware-acceleration"), [here for how in Chrome]("https://www.howtogeek.com/412738/how-to-turn-hardware-acceleration-on-and-off-in-chrome/").
Sorry I forgot to say that it's freezing opening others menus and applications too.
I think we need to fix the Nvidia hardware acceleration after the reboot, as I mentioned before. Everything works great just after I reinstall the Nvidia driver.

---

### Post by tea for one on 2022-09-19
Are you running a Wayland session or Xorg?
Ubuntu defaults to a Wayland unless you change to Xorg at login.
There are many internet articles about the Wayland/Nvidia performance.

---

### Post by gustavodartagnan on 2022-09-20
I's running Xorg.
I Followed an post that said to exclude all Nvidia packages, uninstall Nvidia driver and try to install the ubuntu nvidia driver again.
And it works!

Thanks!

---

