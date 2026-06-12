---
title: "Kernal Automatic Updates Stopped Working"
date: 2016-05-25
forum: Desktop Environments
---

### Post by Wadcutter on 2016-05-25
I asked about this issue previously. The answer made sense at the time, but doesn't really address the issue now.  About a year ago my wife's computer crashed after the automatic system update installed Linux kernal 3.2.0.95. I rolled it back to 3.2.0.94 where it worked fine and has done so up to now.  While her computer is not exactly the same as mine, it is a 64 bit desktop box and we are both running Ubuntu 12.04 which we both installed about the same time 3.5 to 4 years ago. She and I regularly receive and install all the updates from the automatic Update Manager, however whereas I am now running Linux kernal 3.2.0.103.143, she has never received a further kernal update after the 3.2.0.95 fiasco. It seems that in the past 12 (or more) months, she should have received a few kernal updates because she was receiving them regularly in the past.

 

 I've compared all the Update Manager settings but can't find a difference between her settings and mine that would account for me being about 12 kernal versions ahead of her. I haven't really pursued the issue until now going on the, “if it ain't broke, don't fix it.” theory. But it does bother me and I'm not knowledgeable enough about kernals to try any fixes without some competent advice. I have looked into Synaptic Manager, but am reluctant to install the 3.2.0.103 package without knowing a little more. Would it work without all the previous kernal versions? Does a kernal stand on its own or, like incremental backups, does it require all the previous versions be installed first? I'd feel better if I could just get the automatic kernal updates to work for her.

Thank you.

---

### Post by mcduck on 2016-05-25
My guess would be that when rolling back to older kernel you also ended removing the kenrel metapackages, which are needed to get automatic kernel updates.

Make sure you have the *linux-generic* package installed. If it's not installed, simply installing it should get everything working again.

Basically, unlike most other packages in your system, kernels aren't updated simply by replacing an existing package with a new version of the same packages. Instead, each kernel update adds the new kernel, while the old version is left installed so that if you have any issues with the new kernel you can just select the previous one from Grub menu to get back to a working system. And this is done in a simple way, there's a package called *linux-generic*, which doesn't actually include any files at all, but always has the latest kernel version marked as it's dependency. So, when new kernel comes out, the metapackage is updated, and it brings in the new kernel package with it.

(And no, you don't need the intermediate kernel versions, just the latest one is fine, and reinstalling that metapackage should sort that out ofr you.)

---

### Post by Wadcutter on 2016-05-26
Thank you, mcduck. That seems to have worked---with one problem. I'm now back to where I was when I reverted to ver 94 (3.2.0.94 generic) a year ago. The reason I did that was because the ver 95 kernal update messed up her display and this update to ver 103 has done the same thing. It now thinks her widescreen flat panel monitor (22 or 23 inches) is a laptop and the maximum resolution offered is 1024 X768 which makes all the icons gigantic. Correct resolution should be something closer to 1920 x 1080 but I don't seem to be able to change the display to that (from the System Settings menu).  This is the original problem I should have addressed a year ago instead of reverting to a previous kernal version.  I probably should now post this as a separate thread to look for some suggestions on it. I do thank you, however, for your help on getting the kernal up to speed.

Update: I downloaded and installed a different (I think) Nvidia driver from the Additional Drivers menu and that has, at least, given me a choice of many resolutions including the aforementioned 1920 x 1080. The desktop looks respectable. I hope the next kernal update doesn't trash the display again. If it does, I will then look for the cause of that and a solution.  I think everything is, at least, usable now. Surely don't want my wife angry at me. Thanks again for you help.

---

### Post by mcduck on 2016-05-27
As long as you use drivers from Ubuntu's repositories, updates shouldn't break them. Maybe that was the problem in the first place? If you install drivers by downloading them manually from nVidia, for example, their installer creates a kernel module which is specific for the kernel version you have at the exact moment when you install the driver, so kernel updates would require you to reinstall the graphics driver manually. Using the drivers from Ubuntu's repositories that's not an problem and everything really should just work...

Anyway, great that you got things working correctly again!

---

