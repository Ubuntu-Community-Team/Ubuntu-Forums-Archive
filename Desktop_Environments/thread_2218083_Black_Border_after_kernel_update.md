---
title: "Black Border after kernel update"
date: 2014-04-19
forum: Desktop Environments
---

### Post by john195 on 2014-04-19
I experienced this problem, a black border around both the splash screen, login screen, and desktop, with a 3.8 kernel, but a subsequent kernel update corrected it.  I am on Xubuntu 13.10, using the 3.11 kernels.  3.11.0-17 did not have the border, so I continue to boot with that kernel.  The problem occurs with 3.11.0-18.  I was hopeful when 3.11.0-19 was released but the problem still exists with that version.  I have seen other threads with a similar problem but they all appear to relate to a specific desktop theme or video driver.  I have not changed any of that on my system.  I apply the updates regularly, and this problem only occurs with specific kernel versions, so I'm inclined to believe that one of the changes to the kernel causes the problem.  Is there something I need to change with these updated kernels?

---

### Post by mörgæs on 2014-04-20
Hi, welcome to the fora.
How does it look in a live boot of 14.04?

---

### Post by john195 on 2014-04-21
Hi and thank you.

I will give that a try and post back.

---

### Post by john195 on 2014-05-01
Not sure why this corrected the problem: I was cleaning up the kernel versions I had installed (3.11.0-12, 3.11.0-15, etc.) using aptitude.  While searching for each related entry, I noticed that 3.11.0-17, the one that DOES NOT have the problem, had the kernel headers installed.  But 3.11.0-18, 19, & 20 did not, and the problem occurs with each one.

So I installed the headers for 3.11.0-20.  Upon restart, the border was gone on both the splash screen and the desktop.  By the way, I don't think I mentioned I am using XFCE for my desktop.

The headers being installed resolved the issue.

---

