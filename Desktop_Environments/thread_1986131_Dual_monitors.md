---
title: "Dual monitors"
date: 2012-05-24
forum: Desktop Environments
---

### Post by Ron McIlvaine on 2012-05-24
Hello,

I am knew to Ubuntu and Linux but not to the computer world.  I've been been working with them since DOS 3.0.

A few weeks ago, I loaded Ubuntu 12.04 on to my ACER Aspire 5534.  It's not the fastest or most powerful computer on the block, but it was all I could afford at the time.  i was hoping that Ubuntu would breath new life into it.  I like Ubuntu and have been setting it up, making it usable, mostly for learning purposes right now.

When trying to get my external ACER monitor to work, all I can do is get it to mirror the notebook screen.  When I un-check the Mirror box, it will show two screens but when I select it I get a message about being out of range, or something to that effect.

I read a post about installing the proper driver so I installed the driver from the driver folder.  it is a proprietary driver and not supported by Ubuntu with no better effect.

What am i doing wrong?

---

### Post by arubislander on 2012-05-24
You aren't necessarily doing anything wrong. But I do have a few questions that your answering could help us help you better:

[LIST=1]
[*]What is the exact message you get?
[*]What is the chosen resolution of your external monitor?
[*]Have you tried dragging the monitors on screen to sit under each other instead of next to eachother?
[/LIST]

---

### Post by Ron McIlvaine on 2012-05-24
This is the first message I get:

A selected configuration for displays could not be applied
requested position/size for CRTC 148 is outside the allowed limit: position=(1366, 0), size=(1366, 768), maximum=(1600, 1600)

Then I get:

Failed to apply configuration: %s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 148 is outside the allowed limit: position=(1366, 0), size=(1366, 768), maximum=(1600, 1600)

It automatically comes up with the external monitor on the right of the laptop monitor.  I have tried moving it and saving it but with the same or similar results.

The resolution for both is 1366x768.

Thanks for your response.

Ron

---

### Post by Ron McIlvaine on 2012-05-25
Can anyone help here?

---

### Post by arubislander on 2012-05-26
Two 1366x768 monitors side by side would give a virtual resolution of 2732x768 for the extended desktop, while the maximum virtual resolution supported in your situation is 1600x1600.
I would have expected that if you moved the monitors on screen to be the one on top of the other you'd then get a virtual resolution of 1366x1536 which should be all right.

---

### Post by Ron McIlvaine on 2012-06-01
Thanks. The external monitor was on the right side and it worked. However, when I moved it to the left side, all I now get is a screwed up screen. I have to force close the computer and restart the computer with the monitor disconnected. Any ideas on how to reset this? Thanks.

---

### Post by 1clue on 2012-06-01
Regarding getting your frozen X screen back, try <ctrl><alt><f1> to get to a virtual terminal, log in as your user and then type **sudo killall X** to kill off the session.  It should come back to the login screen on your normal  X terminal (mine is <ctrl><alt><f7> but I usually mess with that sort of thing)

If that doesn't work you can also **sudo reboot**.

Remember to log out of your f1 terminal when you're done.  It can be a security hole.

---

### Post by arubislander on 2012-06-08
> **Ron McIlvaine said:**
> ... The external monitor was on the right side and it worked. However, when I moved it to the left side, ...

You shouldn't move the external monitor to the left. That would not solve the virtual resolution issue, you should move it below or above your laptop screen.

---

