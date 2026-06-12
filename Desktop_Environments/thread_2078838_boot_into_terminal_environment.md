---
title: "boot into terminal environment"
date: 2012-10-31
forum: Desktop Environments
---

### Post by McGertz on 2012-10-31
Im new to linux and i am currently taking a linux class.

I took an old laptop and installed ubuntu 12.04 on it.

It looks very nice, but i would like for it to boot straight into a terminal environment with minimal resources. 

We have used CentOS in our class a little bit and we boot straight into a terminal environment and when we want to bring up the GUI we just have to use the startx command and it starts up.

Is there any way to do the same thing with ubuntu?

Thanks

---

### Post by markbl on 2012-10-31
Edit /etc/default/grub and change GRUB_CMDLINE_LINUX_DEFAULT=”text”, then
sudo update-grub, and reboot.

---

### Post by McGertz on 2012-10-31
thanks. i will try this.

---

### Post by markbl on 2012-10-31
You may already know this tip but it is **very** handy to use "screen" or "tmux" (preferred) when working in a straight console environment to get multiple terminals, split screens, etc.

---

### Post by McGertz on 2012-10-31
It worked! thank you!

I've heard about tmux before and played with just the basic shortcuts. Is screen any better or worse?

What about window managers, i heard about wmii, i think thats what its called. 

I also saw someone in the class using something like tmux, probably was tmux, and he opened up a web browser in one of the windows.

Thanks again.

---

### Post by markbl on 2012-10-31
You said you want to boot to a plain console, no X, no wm, no web browser etc. I was just suggesting that tmux is a great way to get multiple terminal windows within such a simple console terminal. Screen is the original program we have used for many years, tmux is the "new kid on the block" but is slightly better (e.g. has vertical window split) and so is recommended for new adopters.

"apt-get install tmux" and then read "man tmux" and/or ask uncle google about tmux.

---

### Post by McGertz on 2012-10-31
Got tmux, thanks a bunch for the help. so what i changed into the grub file makes ubuntu load only the necessary processes to run the basic console/terminal?

---

### Post by markbl on 2012-10-31
> **McGertz said:**
> Got tmux, thanks a bunch for the help. so what i changed into the grub file makes ubuntu load only the necessary processes to run the basic console/terminal?
Ubuntu (well any linux) boots to at least a console prompt always. What you changed stops it doing the normal next step which is to start X11 + the login/window manager/environment which uses a lot more machine resources. As you asked for, you can start that second phase manually anyhow using the startx command. If you are on an old slow low memory machine, and you only want a terminal window, it makes sense to want to boot to just a console (but use tmux to make the environment much easier).

FYI, you can also still see the console prompt from the X environment using <ctrl>+<alt>+<f1>. Press <ctrl>+<alt>+<f7> to go back to X.

---

### Post by McGertz on 2012-10-31
Alright, well i think im set for my linux journey. Thank you very much!

---

