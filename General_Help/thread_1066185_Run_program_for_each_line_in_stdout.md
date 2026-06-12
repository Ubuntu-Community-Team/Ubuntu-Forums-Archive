---
title: "Run program for each line in stdout"
date: 2009-02-10
forum: General Help
---

### Post by LinuxPS2 on 2009-02-10
I have s script that will display the alerts from kismet server but the problem is that it displys something like this
```
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
*ALERT: XX:XX:XX:XX:XX:XX
```

Is there a way to make a program run for each "*ALERT: XX:XX:XX:XX:XX:XX"?
that way each time a new ALERT line appeared it would say, take a picture with its name being whatever XX:XX:XX:XX:XX:XX is?

and as an added bonus is there a way to check and make sure the MAC address is not 00:00:00:00:00:00?... thanks

---

### Post by lavinog on 2009-02-10
what type of script is it?
Would you be able to post the script you have, or at least a modified version?
Would you want to add the features to that?

What do you mean by a picture?...do you want to make a screenshot?

---

### Post by LinuxPS2 on 2009-02-10
currently the script is
```
#!/bin/bash
echo -e '!0 REMOVE TIME\n!1 ENABLE ALERT bssid' | nc localhost 2501 | xargs -n1 ~/print.sh
exit 0
```
where print.sh is just a test script that makes a txt with the name of the arg and contains the arg, this will eventually be a script that takes a picture with the name of the argument, and by picture i mean i will be using something like gphoto2 to control my digital camera to take a picture - I accidentally left my digital camera at home (at college right now) so as soon as I head back to get it this weekend I will see how that goes, not sure if my old sony (really old) will be able to do it, i'm afraid the shutter speed is too horrible since I will be moving at a fairly decent speed (wardriving)
after that I want to either make a script that parses the kismet gps data and accesspoints with the picture with the corresponding bssid as its name or modify/borrow one of the converters already out there to include picture support (this will be done in python) and hopefully if all that works I will make a nice little PyQt4 frontend for it all (just three buttons, start/stop kismet, start/stop camera, and parse data to googleearth file) if anyone wants to collaborate thats would be cool

now what would be the best way of deleting files that do not match the pattern ```
??:??:??:??:??:??.*
``` just an if loop?

---

### Post by lavinog on 2009-02-10
I think having files with colons in the name can be problematic

a for loop would work i think.
I thought using find would work, but I don't know how to find files that don't match the pattern...unless you use regex (which i am pretty limited with)

---

