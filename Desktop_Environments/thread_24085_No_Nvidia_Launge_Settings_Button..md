---
title: "No Nvidia Launge Settings Button."
date: 2005-04-05
forum: Desktop Environments
---

### Post by LongTooth on 2005-04-05
From the Ubuntu 5.04 Starter Guide: 

Q: How to install Graphics Driver (NVIDIA)?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. Read How to install Menu Editor for GNOME?
   4.

      $ sudo apt-get install nvidia-glx nvidia-settings
      $ sudo nvidia-glx-config enable
   5. Applications -> System Tools -> Menu Editor
   6. Menu Editor

      File Menu -> New Entry

      Name: NVIDIA Settings
      Command: nvidia-settings
      Category: System Tools

      Save Button
   7. Applications -> System Tools -> NVIDIA Settings


All installs well. However when I follow step 7 and click on NVIDIA Settings I get an error message: 

Cannot launch Entry
Details: Failed to execute child process "System" (No such file or directiory)

How do I fix this? 
Thanks.

---

### Post by yage on 2005-04-05
Seems like you put System Tools under Command instead of Category?  :wink:

---

### Post by LongTooth on 2005-04-05
Hummm? I'm at work at the moment. I'll check it out when I get home. Isn't it alway the thing right under your nose you can't see. I'll get back and let you know. Thanks.

---

### Post by LongTooth on 2005-04-06
yage, have you ever dial a telephone number without thinking about it? You follow a pattern. If someone was to ask what you dialed you would have to stop and ponder. I didn't even think about what I was doing. You hit the nail right on the head. Next time, I'll look and think and then look again. Thanks, that did it. Jumped right in without looking.

Now to figure how to use it. Much to study.

---

