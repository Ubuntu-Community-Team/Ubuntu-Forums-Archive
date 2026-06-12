---
title: "Conky Startup Script"
date: 2009-06-07
forum: Desktop Environments
---

### Post by BlazeXI on 2009-06-07
Hello...

i have manage to complete my conky configuration to my complete satisfaction (looks & stuff ) and also created a script with a 20 sec delay .... when i run the script from terminal (as user)  "sh script.sh" i get not error but just displayed info saying " not all process could be show : not root "....but when i run it as root sudo sh script.sh " no problems..

ok... i would like to run this script at startup (boot).... and i think i can do this by system/preferences/startup applications ..... add new application .... but how do i make it run as root ???

please help ;(

---

### Post by j0hn00 on 2009-06-07
make sure it's accessible and executable by all

sudo chmod a+x script.sh

then add the following to startup applications

sh /location/script.sh

make sure you replace location with the path of the file

---

### Post by BlazeXI on 2009-06-08
Thankz JohnOo ...

much appreciated ;)

---

### Post by Hund on 2009-06-08
How does that script look like if it requires root access?

Make a script like this instead:

```
#!/bin/bash
sleep 10
conky
```

Then you will be able to run it as a normal user.

---

