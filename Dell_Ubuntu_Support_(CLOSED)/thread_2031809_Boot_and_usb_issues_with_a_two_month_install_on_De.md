---
title: "Boot and usb issues with a two month install on Dell insp."
date: 2012-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oobuntuck on 2012-07-22
Hello all! I am a newbie here.

I have Ubuntu LTS 12.04 on a six year old Dell Dim E521. Love it. A little less than my Mint Julia, but don't be hatin me for that. It just could be that I have used such little of Ubuntu.

Came over from the dark side about 3.5 years ago and there is no way I am going back to Win Hell - everytime I use GNU products, I realize how viscerally I hate MSft's paid ones. I used to work for them for a while and have friends who can give me free products, if I ever wanted them  so I am not cribbing for the money. 

Sorry about the rant, needed to get that off.

I need help with my two-month old install. Everything was sailing smooth like a song, but one week of absence and a reboot and everything has gone dead wrong.

1. The boot is now random. I hear the machine churning for a while when it does but the peripherals only come on randomly. Especially the monitor, it says 'no signal' and goes into sleep mode. My monitor is a brand new ViewSonic and works beautifully when it does make the connection to the pc.

2. A lot of my peripherals are usb connected: wireless keyboard, w/l mouse, and w/l modem. They too work randomly. After a boot, sometimes an active keyboard freezes and the mouse does the same. I have tried wired connections with the same behaviour.

3. My machine has crashed a few times too but I gather its far too may times for Ubuntu in a span of two months.

4. All updates are up-to-date

Help. Please.

Thank you.

---

### Post by oobuntuck on 2012-07-22
my machine has two harddrives, one with a dead vista on it. It has been sitting there for the past two years and I do randomly use it for file access via Nautilus but that is it.

One of the symptoms of the virus that finally got me off the Win coolaid was that my vista was not booting - the machine kept whirring after startup. Could it be that my boot order was changed by the deadling?

---

### Post by oobuntuck on 2012-07-22
:help:

---

### Post by atenz on 2012-07-24
have you tried booting from Single hard drive , containing Ubuntu by removing the Vista Drive

---

### Post by oobuntuck on 2012-07-25
Thank you for your response. Do you mean by physically removing the other hard drive? Do you think the solution should be as drastic that I should open the box and do that? I can try but I'd doubt that would work for a lot of people. I use the other drive as a repository for media. Other than that I don't. Do you suspect the virus that affected my boot sector is interfering with the process? I can understand that but why are my peripherals getting unhinged randomly?

Thanks again!

---

### Post by oldfred on 2012-07-25
It could be a hard drive or any device that is failing or has a driver not working quite right.

BIOS, grub & System (Ubuntu or Windows) scan all devices to know what drivers to load. So if a device does not report correctly due to impending failure or driver does not see it correctly you may have intermittent failures. Very difficult to find.

With hard drive, go into Disk Utility and click on drive. If Smart Status is green then drive should be ok or else it may report impending failure. All I really know is green is good, but it had many technical details.

---

### Post by oobuntuck on 2012-07-26
> **oldfred said:**
> With hard drive, go into Disk Utility and click on drive. If Smart Status is green then drive should be ok or else it may report impending failure. All I really know is green is good, but it had many technical details.

Thanks OldFred, did the disk check and the status shows as green. What else can I do to get diagnostics of a previous session?

---

### Post by oldfred on 2012-07-26
You can check log files with Log File Viewer and look for any error messages. On booting it is dmesg but there are many log files. In dmesg I look for errors, long times between some task, or a task that keeps repeating and then fails.

Log files are in this if you have to open more than what the default shows:

/var/log

---

