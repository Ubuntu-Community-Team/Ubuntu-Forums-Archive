---
title: "vsync not syncing after a while"
date: 2019-02-26
forum: Gaming &amp; Leisure
---

### Post by BatteryKing on 2019-02-26
I have tried various tricks to get vsync to work correctly on my system with a high end Nvidia card while playing Steam games, but the best I can get is it works at first, but after awhile (as in I come back the next day or get a chance to play a week or two later) it will not sync correctly.  I have tried things like:
1. In /etc/modprobe.d, add file zz-nvidia-modeset.conf, and put "options nvidia_drm modeset=1" in the file and restart the system.
2. In the NVidia control panel, set "Force Composition Pipeline" and also "Force Full Composition Pipeline".  This either has no effect on the game (there is not tearing and no stuttering to begin with), just fixes screen tearing on desktop applications, or if there is screen tearing during game play, this causes screen jutter as in one frame gets drawn twice and then the next is skipped.

An interesting thing is when there is screen tearing, it very consistently tears near the top of the screen at about the same spot.  Only in some challenging scenes do I ever see the tear line shift.  As this is at 60 fps on a 60Hz display and 60 Hz is slow enough to where I can see the individual frames, I can confirm at least when compositing is turned off that there are no dropped frames.  Also when compositing is turning on I can see that one frame is drawn twice and then right after a frame is skipped.  At this this tends to happen multiple times per second, so makes me nauseous real fast.  I have also tried turning off vsync and just using the composition pipeline to get the double buffering effect and what happens is the frame rate tends to jump to around 200 fps, not really look all that smooth as I can see each individual frame at 60 Hz and can see it is just picking one of these few frames drawn at slightly different points in game time every time seemingly at random, and power draw goes up by over 200W with this system.

As for relevant hardware I am running:
1. CPU - Intel Xeon E5 1650v4 (6 core, 3.6 GHz base, 4.0 GHz turbo, Broadwell) liquid cooled via a full board monoblock.
2. GPU - MSI 2080 Ti Seahawk EK X
3. Radiator - 560mm wide, 86mm thick with a single row of high static pressure Noctua 140mm industrial fans (tending to run around 1,000 RPM while gaming).
4. RAM - 64 GBs of ECC RAM across the 4 memory channels of the CPU.
5. Displays - Two fairly ancient 1920x1200 24" monitors.
6. OS - Ubuntu 18.04 Mate edition.

As for other things going on with this system:
This system is a central hub of sorts for my home computer setup.  It has multiple real time processing tasks happening concurrently, however these tasks leave ample room across the 6 cores for games to have the CPU time they need.  There are also regular multi-threaded jobs running on the system, but I have the priority level set low so they seem to play well with gaming.  There are multiple users using this system.  I have noticed problems crop up after other users log into the attached console, however I get a chance to check if game play is affected days to weeks after usually due to lots of things going on in life now, so hard to say if this is causing the problem.  There are multiple VMs (virtual machines) running on this computer via VMware Workstation 15, but so far don't have all of the VMs fired up right away, so later on when all of the regular VMs are fired up do I notice the problem, so also not sure of if the problem lies here.  I did at least turn off 3D acceleration in the Windows VM as 3D mode does not play well with multiple users using the console at different times.  As this is a central hub system, it is hard to justify restarting every time there is an issue with vsync in games to try to nail this down better.  This system also has a number of servers running on it, but most of these are always running, so I doubt this would be the problem as then I don't think vsync would be working after a fresh reboot , however it is.

---

