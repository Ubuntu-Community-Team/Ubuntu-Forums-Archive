---
title: "My experiences after upgrading Intrepid 8.10 -&gt; Jaunty 9.04 RC"
date: 2009-04-17
forum: Desktop Environments
---

### Post by motin on 2009-04-17
I don't know about you, but I have now evaluated the benefits of my upgrade from Intrepid 8.10 to Jaunty 9.04 RC, and I must say, while it is nice to know that I am having updated software, it didn't come with many benefits for me...

Here are the showcased features for the Jaunty upgrade, and my comment on how it affected me:

**GNOME 2.26**
[INDENT]	**Brasero - the now default disc burning utility in Nautilus**
[INDENT]		Comment: The Video disc feature would have been interesting if not all files that I tried to add (mov, avi, mts) were met by "You can only add video content"...
[/INDENT]	**Improved handling of multiple monitors with an updated gnome-display-properties**
[INDENT]		Comment: I am forced to use nvidia display properties so cannot really say that this benefits me. However I did like the way it notifies about and starts up the nvidia app when accessing display properties
[/INDENT][/INDENT]**X.Org server 1.6**
[INDENT]	Comment: Together with the last release of nvidia drivers, I have re-enabled Compiz for some days of testing. Up until today I have _never_ had any stable encounter with desktop effects. Maybe finally this is possible?
[/INDENT]**Wacom tablet hotplugging**
[INDENT]	Comment: Good to know that I can buy one of these now, but wasn't planning to...
[/INDENT]**Boot performance**
[INDENT]	Comment: I did extensive testing with bootchart before and after the upgrade. Time to GDM Greeter was totally unchanged (still ~105s), and time to desktop after login was extended from around 130s to 150s... 
[/INDENT]**Ext4 filesystem support**
[INDENT]	Comment: Interesting. I will enable ext4 features in some time after making sure that my hardware works with the Jaunty kernel. UPDATE: Seems that migration to ext4 on / alone cut boot times with 10% for me. Not bad!
[/INDENT]**Cloud computing**
[INDENT]	Comment: When would I want to use this?
[/INDENT]**Turn-key mail servers**
[INDENT]	Comment: This is a laptop...[/INDENT]

**Not showcased enhancements:**
		** - Touchpad settings support in mouse properties**
[INDENT]			Comment: I found this useful. Not a large impact, but nice to have.
[/INDENT]
		** - New GDM greeter design**
[INDENT]			Comment: This is awesome! Finally a good looking login screen in Ubuntu!
[/INDENT]

I have yet to evaluate the persistance of the long-standing bugs that I have experienced over the years (and are still not fixed). An update will follow, together with boot performance after disabling vfat fsck checks (around 43s during every boot...) and enabling ext4 features.

EDIT: Here's the update: (17-apr-2009 19:08)

**Regarding the persistance of the long-standing bugs that I have experienced over the years**
I have never been able to create an Ad Hoc network with my mac-based wireless network card. Still can't...
[https://bugs.launchpad.net/debian/+source/network-manager/+bug/183303](https://bugs.launchpad.net/debian/+source/network-manager/+bug/183303)

Regarding the never ever experienced stable compiz: it seems to be running smoother, but two hours ago the screen got messed up again and required disabling/enabling of the desktop effects again.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747)

I have 2-3 others as well which I haven't checked if the exist. Reason is I have well-working workarounds (scripts and keyboard shortcuts) for those issues, and currently I am happy continuing using the workarounds. Another day of computing, maybe...

**Boot performance after disabling vfat fsck checks (around 43s during every boot...)**
This directly cut around 43s from the boot-time... 
I also ran some profiling (which extended boot time but shortened the login to desktop time) and uninstalled privoxy (which gave -2s). Ended up with:

Time to GDM Greeter: 71s
Time to desktop after login: 105s

**Boot performance after enabling ext4 features**
Now here is the interesting part. After enabling ext4 on my root partition (having separate /boot and /home leaving as ext3), I got the following boot/login-times:

Time to GDM Greeter: 65s
Time to desktop after login: 94s

It seems that ext4 shortened the boot+login times with around -10% just like that. Not bad!

---

### Post by wanchai on 2009-04-17
I've been testing 9.04 since Alpha-5 on and off (swapping disks in and out) to see how it works with my hardware (HP 6930p), and I do see some small advantages: the brightness controls now work no matter whether I boot on AC or on battery.

My feeling is that it boots faster, but then again, my 8.10 "production system" uses LVM with encryption, the 9.04 test disk doesn't. I need to do some bootcharting as well...

My first impression of the new gnome-display-properties isn't that good. It seems to work better in 8.10. For example, I couldn't get the screens to mirror. Need to do more testing here.

A big problem is a bug in VMWare Workstation that shows up only in 9.04. When you go full screen in a virtual machine and change view ports in Compiz, VMWare will automatically move itself to the current screen. The workaround is to re-compile Compiz with a patch ([http://forum.compiz-fusion.org/showthread.php?t=10642](http://forum.compiz-fusion.org/showthread.php?t=10642)). I know from the VMWare forums, that they do have a fix for this, but it didn't make it into the latest release of VMWare Workstation ([http://communities.vmware.com/thread/199313](http://communities.vmware.com/thread/199313)). So, if you are a VMWare user, please start bombarding VMWare with requests to fix this.

Mail Server on a laptop? Why not? I've been running Dovecot as a single user on my laptop because I want to use Thunderbird and keep my emails in MailDir.

GDM screen: yessss, this one does look good. Very good, actually. However, I'll probably keep my personal one with a background image related to the hostname. I'm glad that there is no jackalope on the wallpaper. I do like the animals, but we should put an animal themed wallpaper on hold until the koala comes around.

---

### Post by leonardo_neo on 2009-04-17
> Boot performance

    Comment: I did extensive testing with bootchart before and after the upgrade. Time to GDM Greeter was totally unchanged (still ~105s), and time to desktop after login was extended from around 130s to 150s...

Ext4 filesystem support

    Comment: Interesting. I will enable ext4 features in some time after making sure that my hardware works with the Jaunty kernel. 

I enabled ext4, and I notice significant improvement in boot performance.

---

### Post by motin on 2009-04-17
@wanchai: Thanks for sharing your experiences

> **leonardo_neo said:**
> I enabled ext4, and I notice significant improvement in boot performance.

I just summarized my experience in the update above. Seems like ext4 cut -10% on the boot+login time. Not bad...

---

