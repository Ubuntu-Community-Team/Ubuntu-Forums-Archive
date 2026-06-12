---
title: "GDM hangs on boot in Feisty"
date: 2007-04-23
forum: Desktop Environments
---

### Post by jjakspaw6 on 2007-04-23
Hi All, 


I hope some one can help me out here.... I am still quite new to this and have know Idea what I've done. When I start my laptop It gets to a point where it's about to load the log in screen and the machine hangs. the last thing that I had done is turn on file sharing and enable remote login . (I was having issues with beryl earlier this morning but I had solved that.) 

I can boot my laptop to the recover mode and I can start X when I look at the console I see errors regarding my Radeon card and then every 5 minutes or so I get this 

firmware_helper[4654]: main: errorloading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:00:09.0' with driver '(unknown)'
[  877.220000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw not available or load failed

If some one could help me out I don't know where else to look for errors, in recover mode GUI I cant open any of the applets that I opened earlier ( like the file shareing and login screen) I don't know where the error logs are located at for this either.. 

Thanks inadvance...

Jason

---

### Post by jjakspaw6 on 2007-04-24
after much tinkering I gave up and reinstalled....... I figured that the GDM was so ar corrupt that it was pointless to continue trying to fix it (reinstall of GDM didn't work either). I am however I still see this error


firmware_helper[4654]: main: errorloading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:00:09.0' with driver '(unknown)'
[ 877.220000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw not available or load failed


anyone have a clue on this???????:confused:

---

