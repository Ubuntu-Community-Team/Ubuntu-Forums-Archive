---
title: "How to list Ubuntu 20.04 files from Windows 10 on dual boot notepad"
date: 2020-06-07
forum: Desktop Environments
---

### Post by Raj_Cherukuri on 2020-06-07
I have a dual boot laptop configured to run Ubuntu 20.04 and Windows 10 on the same machine. I can list windows files from ubuntu without any issues.
However, I am not able to display Ubuntu files from Windows 10. The problem is that I have a small size partition on C:\ where I have installed windows 10 and a much larger partition of 250GB wherein I have installed Ubuntu 20.04. On logging into ubuntu, the windows partitions are automatically mounted and listed. But, in windows 10 file explorer, I am unable to display ubuntu files. I have configured samba configuration file (smb.conf) to share two folders on ubuntu side. However, the share is not being enabled when I login to windows.

Any useful information is appreciated and if this forum is not suitable, kindly suggest the right forum to post this issue.

Thanking you in advance, Sincerely, Dr. C. Rajabhushanam

---

### Post by CelticWarrior on 2020-06-08
Welcome.

What you describe is perfectly normal and expected. Ubuntu supports all file systems Windows does but Windows only supports Windows file systems. Windows natively can't "see" Ubuntu partitions. It may with a third-party software that shouldn't be used because it is known for corrupting those partitions.

Samba is for network sharing, it doesn't and couldn't work in the same machine unless, in your case, Ubuntu was running as well.

So, unfortunately there's no good solution for you other than having a separated data partition NTFS formatted and with Windows Fast Startup feature disabled. Do NOT write to Windows system partition (C:\) from outside Windows. The risk of Windows becoming unbootable is very high, especially with Fast Startup enabled.

---

### Post by Raj_Cherukuri on 2020-06-09
Ok. Thanks. Shall use a pen drive to transfer files. Bye.

---

