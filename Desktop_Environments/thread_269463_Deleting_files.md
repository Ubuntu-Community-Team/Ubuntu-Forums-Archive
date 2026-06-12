---
title: "Deleting files"
date: 2006-10-01
forum: Desktop Environments
---

### Post by SishGupta on 2006-10-01
Hey,
 I have a problem where every time I try to delete a file in nautilus it takes about 30-60 seconds to move to the trash. Then when I empty the trash it takes another 30-60 seconds for that to happen. During the times when i am waiting for a file to move to the trash or to be deleted from the trash, nautilus is completely unresponsive. Sometimes other apps work, but usually they are frozen until the file is deleted.

This doesnt always happen, it works fine if i restart..after a while the problem starts again.

I would greatly appreciate any help or feedback regarding the situation. It is very annoying as I am a neatfreak and I am always deleting unessissary files in my home dir.

thanks
-Sish

---

### Post by Mr Frosti on 2006-10-01
It sounds like a corruption issue in either the file system, or in the application Nautilus itself. You can eliminate the latter by reinstalling Nautilus, replacing any possibly corrupted files. This can be done by running the command below:

```
sudo apt-get install nautilus --reinstall
```

---

### Post by SishGupta on 2006-10-02
Thanks ill try that.

By any chance is it possible that it is related to how i have fstab connect and mount a drive on a network server?

I am not sure but this problem may happen because of a loss of connection to this server (either my wifi drops or im on a different network).

---

### Post by SishGupta on 2006-10-03
The nautilus reinstall had no effect, but i have found the cause of my problem.

The problem does indeed occur because of the mounted network drive. It is fine when the network drive is available, but when I am on a different network this is when the slow downs occur. Unmounting fixes this immediately.

Is there a workaround other than unmounting everytime im not on the network?

---

### Post by taurus on 2006-10-03
Try removing it by hand from a terminal!!!

```
rm <filename>
```

---

