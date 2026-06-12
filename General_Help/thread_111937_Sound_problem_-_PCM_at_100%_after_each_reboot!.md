---
title: "Sound problem - PCM at 100% after each reboot!"
date: 2006-01-03
forum: General Help
---

### Post by daller on 2006-01-03
Hi There,

You probably know that the sound sounds weird with PCM at 100%

Is there a way to set it to 75% permanently?

Should this be reported as a bug? (I mean - over a longer timespan this may kill the speakers!)

I have this problem on 3 different laptops!

Dell Inspiron 8600
Acer Travelmate 292 XCI
HP Pavilion ze4453ea

Any suggestions?

---

### Post by heimo on 2006-01-03
Not sure if this helps. Set the volume level and run:
sudo alsactl store

---

### Post by Kræn Knude on 2006-01-03
I had a similar problem, but with PCM at 0% instead. Try open kmix and uncheck "restore volumes on reboot" in the configuration panel. Then set the PCM at 70%. Dunno if it will work, but it's worth a try

---

