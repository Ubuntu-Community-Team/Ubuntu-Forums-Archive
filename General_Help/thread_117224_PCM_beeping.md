---
title: "PCM beeping"
date: 2006-01-14
forum: General Help
---

### Post by chevy on 2006-01-14
When PCM option is enabled the laptop beeps at me non-stop.  I have a Dell 9300 running Breezy.  The sound card I am using is a SIGMATEL STAC 975X AC97.  Any suggestions on how to shut this thing up and still be able to listen to music?

---

### Post by Ifrgtmyname on 2008-03-29
Same problem here please help! its sooo annoying! It started after I clicked the mix button under Kmix

---

### Post by mali2297 on 2008-03-29
Describe the problem further.

Are you just annoyed by the normal system beeps? 
...or do you hear a defect sound that shouldn't be?

---

### Post by strabes on 2008-03-29
You can disable the system beep by following the instructions located here and rebooting: [http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/](http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/)

Instead of rebooting you could just run:```
sudo rmmod pcspkr
```This will disable the system beep until you reboot. If you edit /etc/modprobe.d/blacklist like that blog post says, the system beep will be permanantely disabled.

---

