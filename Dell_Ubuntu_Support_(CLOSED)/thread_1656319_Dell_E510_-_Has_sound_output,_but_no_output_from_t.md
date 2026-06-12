---
title: "Dell E510 - Has sound output, but no output from the input device"
date: 2010-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rabiv88 on 2010-12-30
Hello,

   My computers sound is working fine when i use Rhythmbox or Youtube.  I recently connected my Xbox to the Audio input in the back and there is no sound output from my speakers.  When I open up my Sound Prefrences the input level recognizes that there is indeed sound being inputed into the computer.  My input volume is set at 100 percent.  I am new to Ubuntu and I am not sure how to fix this. 

  I have searched multiple forums and cant find any information.  Please let me know how to fix this or direct me to a thread to help me with this problem.

Thank You

---

### Post by lidex on 2011-01-05
Can you supply some info please? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

