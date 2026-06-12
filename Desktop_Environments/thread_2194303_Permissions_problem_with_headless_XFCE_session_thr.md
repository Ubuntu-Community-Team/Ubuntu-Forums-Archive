---
title: "Permissions problem with headless XFCE session through vncserver"
date: 2013-12-17
forum: Desktop Environments
---

### Post by IAmWhatWasDavidBowman on 2013-12-17
First, I have searched for an answer to this problem repeatedly, and I have not come up with anything that looked similar. I haven't been successful in analyzing anything in my system logs either. I apologize if I still somehow missed something obvious. My problem is that I'm not sure how to articulate this issue in a concise way, so I have had issues even searching for a solution.

Particularly frustrating is that I did not make any change (of which I am aware) to cause this to stop working, and then just a week or so ago things started working again. I think there were some updates that were installed right before it started working again. I was very pleased and happy. Yeah, well, more updates were applied and now I'm back to things not working. So I'm finally breaking down and posting a request for help from all you gurus out there. Please and thank you in advance!

I'm using 12.04, and I run a headless, secondary XFCE session to use remotely with the vncserver wrapper script. It was working flawlessly until a little while ago when I suddenly could not get things like networkmanager to connect to a VPN or a harddrive to mount through a file manager. I can select the VPN from networkmanager, but it does nothing. No prompting for permissions, nada. I get a "Not Authorized" message from either Thunar or Nautilus when I try to mount a drive by clicking on the icon. I can't mount the drive in Disks either. I get a message of "Not authorized to perform operation (udisks-error-quark, 4)" after I enter my password (correctly!). A simple "sudo mount" from the terminal works fine though. 

I'm logged in as my usual user, and these actions work when I connect to my main GNOME session through a different port (this VNC server is setup with a script that runs at startup, and not through the vncserver script). If I mount a drive there or connect to a VPN server in GNOME, all is well in XFCE. But those actions cannot be initiated in XFCE. I try to avoid using the GNOME session as the resolution of my TV at home is much higher than the remote devices I'm using, so it's easier to have a lower-res, less-glitzy second X session running.

I get similar behavior with gparted. I can click on the icon under the Applications Menu and I get nothing. No prompting for my password, no error message. Nothing. But a simple "sudo gparted" works fine. If I switch back to GNOME, I can click on the icon, it prompts for permissions, and everything is normal.

I've tried updating XFCE. I'm currently running 4.10. No luck there. Same behavior as before the update.

So I'm just at a total loss. Does anyone know how to get things working normally under XFCE again? I don't know what logs or other information to post that might help, but please let me know if you can think of anything or need something additional.

Thank you again!

---

