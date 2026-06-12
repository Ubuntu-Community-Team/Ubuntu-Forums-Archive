---
title: "Oh no something has gone wrong. A problem has occurred and the system can't recover"
date: 2021-02-27
forum: Desktop Environments
---

### Post by t825143 on 2021-02-27
Hello
I upgraded from 20.04 to 20.10 and yes I interrupted the upgrade when base-files took over an hour to install
not sure if it was stuck or just was taking it's time... 
never the less I was able to login but my dock was not loading
I had to reboot
and ... the dam luck while I am continuing to upgrade the system, it froze with colors all screwed. my video  card bonked, (it is not the driver) because even on the BIOS screen the  letters start flashing all over the place
and that is the 2nd upgrade interruption...
I had an almost identical nvidia card so I replaced the video card and the display works fine now

rebooted and now I get "Oh no something has gone wrong. A problem has occurred and the system can't recover"
what I did
I booted in recovery mode, fixed all the packages no more broken packages, my system is updated ... but same error as above

reinstalled many times , gdm3, ubuntu-desktop, gnome, base-files 
dpkg-reconfigure -a .... nothing worked
it has been a week. I almost tried everything I found on the internet related to this error

when I have gdm3 configured my TTY do not work, I do not get the login screen it display the above error after boot
when I have lightdm I get the login screen but it fails to log me in giving the error as above but it display the button to logout, TTY works fine and I can get to my /home 
not sure if important but lighdm login screen still display 20.04 LTS

but everywhere else it display 20.10


OS is Ubuntu
Gnome DE 
nVidia 8500 gt


any help is appreciated

---

### Post by tea for one on 2021-02-27
> I upgraded from 20.04 to 20.10 and yes I interrupted the upgrade when base-files took over an hour to install
Interruption of an upgrade has undoubtedly caused your problem.
> **t825143 said:**
> it has been a week. I almost tried everything I found on the internet related to this error
After a week without success, surely a fresh install and restore your backup is the solution.

---

### Post by Autodave on 2021-02-27
+1 with *tea for one: *time for a clean install.  And, unless oyu have bleeding edge technology that has to have 20.10, I would stay with 20.04 until 22.04 is released in a little over a year from now.

---

### Post by t825143 on 2021-02-27
I agree to stick with 20.04......no cutting edge nothing, just a basic user but I have raids , encrypted volumes , just don't wanna screw it up and end up loosing some data...
the upgrade was just a spur of the moment.

but now I just want to salvage what I have without reinstalling
too many settings...if you believe it this is the first upgrade that I could not solve since warty on same machine.

---

### Post by tea for one on 2021-02-28
> just don't wanna screw it up and end up loosing some data

I just want to salvage what I have without reinstalling

Reading between the lines, I get the impression that you don't have a recent backup?

---

