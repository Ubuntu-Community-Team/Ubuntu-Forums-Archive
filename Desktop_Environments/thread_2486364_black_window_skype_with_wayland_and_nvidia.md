---
title: "black window skype with wayland and nvidia"
date: 2023-04-27
forum: Desktop Environments
---

### Post by pigmy31 on 2023-04-27
Hi,
I have just installed Ubuntu 23.04 and I still have the following problem (which I already had with version 22.10).
With Wayland, when I launch Skype, a black window appears. When I launch it with Xorg, it works correctly.
The NVIDIA driver (525 with 23.04, GeForce GTX 1060 card) is installed. Apart from this problem, everything else works fine. Despite my research, I have not found any solution.
Has anyone experienced this problem before? And, if so, has anyone found a solution?
Michel

---

### Post by TheFu on 2023-04-27
nvidia drivers and wayland aren't friends.  Has that changed?
Did you happen to read the release notes for 23.04?  [https://discourse.ubuntu.com/t/lunar-lobster-release-notes/31910](https://discourse.ubuntu.com/t/lunar-lobster-release-notes/31910)  There are a few nvidia related issues spelled out, but not related to wayland that I've seen. There is a Firefox snap issue with a blank screen spelled out, however.

---

### Post by pigmy31 on 2023-04-27
Hi TheFu,
I know that Wayland and NVIDIA do not mix well in general but I did not encounter the problem described in 22.04 LTS.
There is nothing in [https://discourse.ubuntu.com/t/lunar...se-notes/31910](https://discourse.ubuntu.com/t/lunar...se-notes/31910) that would allow me to get a lead.
Thanks for your comments and I don't despair that there will be a fix at some point...
Regards,
Michel

---

### Post by idmbe on 2023-04-28
Type this and see what results there and share it with us:
```
sudo dmesg -el err
```

---

### Post by pigmy31 on 2023-04-28
Hi idmbe,
The result of the command: [FONT=courier new]sudo dmesg -el err[/FONT] is:
[FONT=courier new]...
[april28 18:33] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership[/FONT]
This message was already present before I launched Skype (after opening a session with Wayland).
Considering the number of times it came up by [FONT=courier new]dmesg[/FONT], I think it is recorded whether I opened a Wayland session or an Xorg session.
Do you want more commands feedback?
Regards,
Michel

---

### Post by idmbe on 2023-04-28
I had like this issue before, and it's solved
Follow this link i hope it's helpful:
[https://answers.launchpad.net/ubuntu/+question/706349](https://answers.launchpad.net/ubuntu/+question/706349)

---

### Post by pigmy31 on 2023-05-03
Hi idmbe, sorry for my late reply.
After following the link (and the corollary links) step by step, nothing made the error message displayed by [FONT=courier new]dmesg[/FONT] disappear.
Too bad...
I continue my investigations.
Regards,
Michel

---

### Post by idmbe on 2023-05-04
Hello Michel,

I hope your investigations will reach a conclusion, and you will share it with us
Good luck

---

### Post by TheFu on 2023-05-04
The fix I chose was to pull the nvidia cards from my systems and use AMD GPUs going forward.  

For people who need the highest-end GPUs, say a 4090, then I can see where an nvidia GPU would be necessary.  For us mid-range and low-range buyers planning to run Linux, it just isn't worth the hassle that comes with nvidia and had for the last decade (if not longer).

That isn't to say that AMD GPUs are perfect.  I've had one in a system since last fall that doesn't have any driver support at all. That's my choice.  Newer (2020) kernels, 5.10+, have the support.  I simply haven't moved off 18.04 on that system yet.  Perhaps this weekend, but I've been saying that for the last 3 months. ;)

I've had nvidia GPUs lose driver support.  Was running fine at 1920x1200 then I did a fresh install to a new LTS release and the nvidia driver support stopped, so it ran at 1024x768. No higher.  The exact same hardware. No nvidia drivers for the newer kernel.  To be far, in 2012-ish (I don't really remember), I had a $50 AMD APU with a Radeon 45xx GPU built-in that also lost support.  But I think AMD released the driver code and the F/LOSS community ported it to all newer kernels after a year or so.

I'm not holding my breath for Nvidia to do the same.

---

### Post by pigmy31 on 2023-05-27
Hi,
I've just installed the NVIDIA 530 driver and my problem seems to have been solved.
We'll have to see now...
Regards,
Michel

---

### Post by TheFu on 2023-05-27
Please use the "**Thread Tools**" button to mark the thread solved. This puts a flag in the forum DB, so others can easily search.  Just changing the title isn't sufficient, but thanks for the attempt.

---

