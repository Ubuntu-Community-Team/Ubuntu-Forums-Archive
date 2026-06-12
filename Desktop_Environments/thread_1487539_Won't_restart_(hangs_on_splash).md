---
title: "Won't restart (hangs on splash)"
date: 2010-05-19
forum: Desktop Environments
---

### Post by thync on 2010-05-19
Dear all

I'm hoping someone can assist me with my problem:

When I restart the system (Lucid) using the power icon in the top right of the screen, it begins the shut down process but almost immediately hangs on the splash screen with the Ubuntu icon, normally with 2 of the 5 dots filled.

When I restart from terminal (alt+ctrl+F2) it begins shutdown (including terminating daemon processes) but hangs after the last process stating [Waiting to restart] or something similar.

I then noticed that there were several lines of text not relating to the shutdown of daemon processes, which read as follows:

> Your CPU appears to be lacking expected security protections. Please check your BIOS settings, or, for more information, run:
/usr/bin/checkbios-nx --verbose

I ran this command with the following text resulting:

> This CPU is family 15, model 4, and has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capability.  Please enable this in your BIOS.  For more details, see:
[https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)

I might be wrong but I'm fairly certain that my CPU is not model 4, more like model 2 (Intel P4 2.66GHz), which does not have NX capabilities. I have checked my BIOS and do not find any reference to NX. Nevertheless, I don't think that this is the problem, as further results of the shutdown dialogue indicate:

> NM-dispatcher.action: Could not get the system bus. Make sure the message bus daemon is running! Message: Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory

I'm still fairly new to Ubuntu so I can't make any sense out of all this. Also, I don't know if it has any relevance, but when I restart or even boot/shutdown from the GUI, the Ubuntu splash screen seems abnormally large - much larger than it used to be, as if it was magnified several times. I can't remember if there was any particular program or process that I installed/updated just prior to noticing this.

I should mention that I upgraded to Lucid from Karmic about a week ago, but that I also could not restart in Karmic (also hung on splash), although I can't remember any of the error messages from terminal restart.

Thanks in advance

---

