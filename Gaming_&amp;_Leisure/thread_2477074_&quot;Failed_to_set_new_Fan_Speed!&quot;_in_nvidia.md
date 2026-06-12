---
title: "&quot;Failed to set new Fan Speed!&quot; in nvidia-settings"
date: 2022-07-13
forum: Gaming &amp; Leisure
---

### Post by 2000mater on 2022-07-13
Not quite solved, but the issue is no longer present as I installed Arch-linux instead and had no issues this time. If you have a similar issue even with gwe consider tracing back or starting over ig. GL!

[SIZE=5]After reinstalling my system I'm curious how I managed to custom control my fan speed the first time.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290719&stc=1[/IMG]
I tried nfancurve with this installation before trying nvidia-settings but I got an error at line 147 of temp.sh. I double-checked cool-bits are set to 28 in /etc/X11/xorg.conf. Finally I tried to set manually in nvidia-settings, and I got that error in the left corner (previous image), fans also did not spun up of course.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290723&stc=1[/IMG]

I also updated the nvidia drivers so that nvidia-driver-515 shows up as selected instead of x.org, hoping that was the issue.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290722&stc=1[/IMG]
I have some worries because other than the xorg.conf file I have some things that appear they might affect these settings such as an empty "xorg.conf.nvidia-xconfig-original" file, an empty xorg.conf.d directory, and many more things I'm fairly unknowldged in :,)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290720&stc=1[/IMG]
I'm getting fairly annoyed because the standard setup tends to get a bit toasty, and these hoops are needlessly complicated.

Thanks everyone who tries to help.
[/SIZE]

---

