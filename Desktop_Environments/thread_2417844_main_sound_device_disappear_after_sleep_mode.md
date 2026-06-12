---
title: "main sound device disappear after sleep mode"
date: 2019-04-28
forum: Desktop Environments
---

### Post by frankoi on 2019-04-28
Problem solved :
edit the /etc/modprobe.d/alsa-base.conf add "options snd-hda-intel probe_mask=1" reboot  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1826868/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1826868/comments/3)
     


Hello !

I have a problem with my sound since I upgraded to 19.04.

When I close my laptop, it goes to sleep. When I wake it up, it switches to " headphones ".
Then, if I go to " sound device ", my main speaker does not show. There's only the headphones that are here. I can't get my speakers back...
I had to reboot the computer to get my device back.

So, I formatted my laptop an reinstalled a clean 18.10, but the problem was still there...
I discovered that this answer : "Same happens for me but only if the HDMI monitor is not "awake" when OS starts or resumes: the list of devices in **Settings > Sound** doesn't even show **HMDI/DisplayPort - Built-in Audio** any more. 
  The fix for me is to suspend the session, ensure HDMI monitor is on, resume the session. 

  Suspend in Ubuntu 18.04 LTS is somewhat insanely hidden behind the  PowerOff button in the drop down menu: hold mouse down on it, or press Alt to convert the PowerOff button into Suspend. Talk about hidden navigation! " in this post [https://askubuntu.com/questions/762816/ubuntu-16-04-changes-sound-device-after-suspend-how-to-fix](https://askubuntu.com/questions/762816/ubuntu-16-04-changes-sound-device-after-suspend-how-to-fix)

     
solved my problem.

So, I thought " OK, i'll do that with 19.04 " and I upgraded to 19.04.
But this solution does not work with the disco dingo release...

Any idea ?

Thanks for your upcoming help.

---

