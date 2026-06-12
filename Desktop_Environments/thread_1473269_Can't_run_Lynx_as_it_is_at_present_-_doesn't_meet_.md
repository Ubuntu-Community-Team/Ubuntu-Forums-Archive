---
title: "Can't run Lynx as it is at present - doesn't meet my needs."
date: 2010-05-05
forum: Desktop Environments
---

### Post by tx836519 on 2010-05-05
I have been using Ubuntu 8.04 for about two years and like it very much.  I have followed the development notes for 10.04 and even downloaded the beta version for evaluation.  Based on my satisfaction with the operation of Ubuntu 8.04 (Hardy Heron), I was eagerly awaiting the release of Lucid Lynx.

I downloaded the Live-cd and did a clean install.  Everything looked pretty good at first.  I did notice that the sound was a bit rough and broken up.  Never had this problem with Hardy.  I proceeded to set up the new version to provide the same (or nearly the same) functionality that I had in Hardy.

The first problem I had was in changing the screen resolution.  I have old eyes and can't work very well with the default resolution, so I wanted to drop it to 1280 X 1024.  I had set up /home on a separate partition that was not connected during the install and I had to work a bit to find that the .config file did not copy over to the new /home.  Once this was done, the screen resolution changed with no other problem.

After installing software and doing major system configuration changes, I rebooted Lucid Lynx.  On this boot it did a file system check.  Ok, I want to know that all is OK before I go deeper.  The process progressed from 0 to 70% OK, from 70 to 75% slowly, from 75 to 90% very slowly and at 90% forward it was painfully slow!  It finished after about a half-hour and the system booted just fine.

Now that the software was installed and the system up and running, it was time to configure my applications.  One thing that I used in Hardy and to which I have become somewhat addicted is gkrellm system monitor.  I like the heads-up display of my machine's status.  It installed with no problem on Lynx and all looked good at first when I started the configuration, but when I was ready to set up the ISA port sensors, I could not get the driver to load.

----------------- from terminal session -----------------------
ken@ken-desktop:/etc/init.d$ sudo /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
module-init-tools stop/waiting
ken@ken-desktop:/etc/init.d$ start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.62" (uid=1000 pid=5325 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
ken@ken-desktop:/etc/init.d$ 
--------------------------- end ------------------------------

I am trying to start:
Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8705F Super IO Sensors'

When I ran sensors-detect, everything seemed to work fine with all of the sensors being detected.  Without the driver, I don't have power supply voltages or fan data.

I run wine and when I tried to load programs into the wine environment, Lynx started acting like windose!  It knew more about the software than I did and it decided that it was not safe to run since it did not come via Ubuntu/Debian repository!  This is the very reason I am trying to totally get rid of Windows and why I like Linux so much.  I thought that this was an environment where the user had control (depending on the level of control of the logon id).  Well, I worked around this problem and got my apps running.

Once I had the system set up somewhat like the Hardy configuration (with the exceptions above) I started cruising the default applications in the new distribution.  I am not into video like many, but do a little editing and DVD creation of my home videos.  Movie Player just gave a black screen.  If I clicked on one of the tool-bar option buttons, the screen worked as long as the drop-down menu was displayed but went back to black if I closed the command window.

I have worked in electronics all of my life and built my first computer in 1979.  I started out with 16 kilobytes of ram and 100 kilobytes of mass storage.  It's still running after thirty-one years with a full 64 kilobytes of memory, four times the cpu speed and with a 20 Megabyte HD, in fact!  I am active in the LTspice user group and download files from the group to help others or to just learn something new.  When I tried to download a file, everything seemed to work just like always until I closed the web browser to open the new file.  I couldn't find it!  I first searched /home.  Then I searched the entire system disk and it did not exist!  So, I must have done something wrong.  I logged back in and downloaded it again, and it said it was saving a second occurrence.  I again searched the entire disk and could not find the file!  Obviously it re-named it to something besides what I am searching for!

After a week of testing and evaluating, I am back to running on Hardy Heron.  If it appears that the new system gets some work and a new version is released, I'll download it and give it a second chance.  -- ken

---

### Post by dino99 on 2010-05-05
nice thread, thats remind me my first 20mhz Commodore big monster system ;)

Since Hardy, lot of things have changed in the background and with apps too.
When you cant find a downloaded files, use "locate" to dig all the system at once.

good luck

note: work as expected on my end ):P

---

