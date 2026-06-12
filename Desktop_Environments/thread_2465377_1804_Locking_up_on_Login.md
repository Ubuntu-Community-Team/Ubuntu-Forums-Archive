---
title: "18:04 Locking up on Login"
date: 2021-07-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-07-31
Toshiba Satellite laptop running Win10 and Ubuntu 18:04 from a 1TB disk

Folks, this has been running fine for ages, Windows seldom used, really just boot up to update.  Recently, to fix a Windoz issue I reinstalled Win10 then using gparted did a bit of disk geometry tidying reducing Windows partition size and moving Ubuntu and increasing its capacity.

Now e2fsck says disk is clean, a windows utility (crystaldiskinfo) says disk in good condition but, I've had a quite a few total lock ups booting Ubuntu after the login screen appears, enter my user password, momentary movement then total freeze.  Ctrl-Alt-F1 (mine needs the FN key too) does not bring up an alternative login.  I have to power off.

I've had this happen quite a few times, any suggestions as to what to investigate would be appreciated.

I am considering installing 20:04 to that partition, maybe that is the easiest option.

Geoff

---

### Post by Geoff_Lane on 2021-07-31
This **may **have been resolved following advice in following link;


[https://stackoverflow.com/questions/52659103/ubuntu-18-04-freezes-after-login](https://stackoverflow.com/questions/52659103/ubuntu-18-04-freezes-after-login)

Shall report back if any recurrences of issue.

Geoff

---

### Post by TheFu on 2021-07-31
Did MS-Windows update the boot loader?
Were new GPU drivers installed under Ubuntu?
What do the log files say?  For linux issues, always, always, always check the log files.

---

### Post by Geoff_Lane on 2021-07-31
> **TheFu said:**
> Did MS-Windows update the boot loader?
Where new GPU drivers installed under Ubuntu?
What do the log files say?  For linux issues, always, always, always check the log files.

Boot menu looks fine.
Not aware of any GPU drivers being installed.
Log files,  had a look at syslog but really didn't know what to look for, I know how to pipe to grep but not knowing the cause of the lockup baffled what to search for.

As mentioned in previous post though it may have been resolved.  Awkward to know with a spasmodic problem but as it happened twice consecutively and again soon after my moving everything and having not been an issue before I thought it may have been related to the move, especially as on one occasion I got a busybox command line.  Suggested I ran fsck, which I did, required a few errors to be corrected then reboot and all fine.

Geoff

---

### Post by monkeybrain20122 on 2021-08-01
I remember old forum posts saying that you should never change Windows file system with Linux tools such as gparted.  Things may be different now, I don't know. Haven't done any dualboot since 2011 When I wiped Windows and installed Ubuntu 11.04.

---

### Post by Geoff_Lane on 2021-08-05
Had a couple more lockups, one was just changing wifi access point connection.

syslog shows this at time of lockup;

```
Aug  5 10:45:26 satellite dbus-daemon[2155]: [session uid=1000 pid=2155] Successfully activated service 'com.canonical.Unity.Scope.LocalFiles'^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^



```

Me thinks an install of 20:04 LTS is looking the best option now.

Strange thing is, if it boots up with no issue then system runs all day without any problems.

Geoff

---

### Post by Geoff_Lane on 2021-08-05
> **monkeybrain20122 said:**
> I remember old forum posts saying that you should never change Windows file system with Linux tools such as gparted.  Things may be different now, I don't know. Haven't done any dualboot since 2011 When I wiped Windows and installed Ubuntu 11.04.

It may have been an issue a few years back but gparted seems very good.  Twice I've resized Windows NTFS partitions with no effect on the MS Operating system but I rarely use Windoz and in all honesty, is kept merely because it came with the machine.

As for your mention about dual boot, on an external disk I have a choice between Ubuntu Mate, Debian, Raspberry Pi for PC and Arch.  All work fine though occasionally updates seem to write all over my laptop GRUB menu, a problem I have learned to live with as it seems GRUB defaults to internal drive even if running from an external.

Geoff

---

### Post by TheFu on 2021-08-05
Resizing and checking files systems that are "owned" by Windows using Linux tools is dangerous in that Windows knows the correct file system internals and the Linux tools are all reverse engineers and cannot know NTFS in the same way.  It is dangerous. Data loss and partition issues CAN happen.  Be prepared to boot from whatever Windows uses as an emergency boot disk/flash drive to restore access should something go badly.

This is always be the situation until MSFT provides native NTFS drivers to Linux.  NTFS has added much more complex setups in the last few years that weren't available previously.  If those get used, bad things DO happen.

After you've been burned like many people here have, you'll understand better.

Never expect Linux drivers to replace the native either scandisk or chkdsk from Windows/MS-DOS.

---

### Post by Geoff_Lane on 2021-08-08
> **TheFu said:**
> Resizing and checking files systems that are "owned" by Windows using Linux tools is dangerous in that Windows knows the correct file system internals and the Linux tools are all reverse engineers and cannot know NTFS in the same way.  It is dangerous. Data loss and partition issues CAN happen.  Be prepared to boot from whatever Windows uses as an emergency boot disk/flash drive to restore access should something go badly.

This is always be the situation until MSFT provides native NTFS drivers to Linux.  NTFS has added much more complex setups in the last few years that weren't available previously.  If those get used, bad things DO happen.

After you've been burned like many people here have, you'll understand better.

Never expect Linux drivers to replace the native either scandisk or chkdsk from Windows/MS-DOS.

I can only go by my experience, I certainly don't resize windows NTFS often, probably twice to make room for Ubuntu.  Plus Windows is rarely used but yes, agree that resizing any not native file system could be potentially dangerous.

Geoff

---

