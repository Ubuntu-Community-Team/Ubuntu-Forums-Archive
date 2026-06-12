---
title: "Just installed Ubuntu - Fan is LOUD"
date: 2009-03-23
forum: General Help
---

### Post by Deathray on 2009-03-23
I just installed Ubuntu on my desktop as well now but have found out that the fan is waaay to loud! In windows I used a piece of software that came with my ASUS motherboard that automatically adjusted the fan speed according to the CPU temperature. Is there anything equivalent in Ubuntu or at least another way to manually control the fan?

---

### Post by mozetti on 2009-03-23
This is the thread I've always used: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by Deathray on 2009-03-23
Thanks I'll gather some courage and go ahead and try :P
Also found this if the other one doesent work: [http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors")

---

### Post by Deathray on 2009-03-23
Okay I found an alternative by going into the BIOS and setting the fan speed to ultra silent. I couldnt get lm-sensors to work with my P5Q Pro, command "sensors" only shows the CPU temperature.

Does anyone have any idea of what I can do to stress test my CPU to make sure it doesent get too hot? Some benchmark or something ...

---

### Post by Chemical Imbalance on 2009-03-23
Try installing gkrellm if you want to monitor your temps/fans/cpu usage

> sudo apt-get install gkrellm

---

