---
title: "Ubuntu desktop login loop after installing Nvidia/CUDA due to LD_LIBRARY_PATH??"
date: 2016-03-19
forum: Desktop Environments
---

### Post by xuancong84 on 2016-03-19
There are many people who encounter this problem: after they installed Nvidia/CUDA library, after reboot, they got a login loop, cannot login to desktop.

I also encounter the same problem today. So I switched to TTY (Ctrl+Alt+F1) and created a new user and found out that I can login using the new user. Then I realize that if I use the new user's $HOME/.profile, I can login too. Finally, the problem lies in the $HOME/.profile, the problematic line is surprisingly: LD_LIBRARY_PATH=*/cuda*:*/nvidia*:$LD_LIBRARY_PATH

It turns out that if your current graphics card is not compatible with the Nvidia driver or CUDA library, or if there is some conflict in Nvidia/CUDA, or in my case, I blacklisted Nvidia device in [COLOR=#333333][FONT=Helvetica Neue]/etc/initramfs-tools/modules [/FONT][/COLOR]for a GPU passthrough, then desktop login will crash the X session despite the fact that X session can still reach the login screen. It is a bug that deals with the fail-safeness of the ubuntu-desktop.

LD_LIBRARY_PATH is used to specify dynamic library path when linking programs, no matter how incorrectly set, it should not cause desktop login to crash.

Thus, I hope the developers can make desktop login more fail-safe, and DON'T do funny stuffs like dynamic GPU module compilation during login, which if fails, causes a infinite login loop.

---

