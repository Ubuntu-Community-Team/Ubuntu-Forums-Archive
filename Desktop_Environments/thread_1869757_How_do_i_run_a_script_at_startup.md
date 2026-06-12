---
title: "How do i run a script at startup?"
date: 2011-10-26
forum: Desktop Environments
---

### Post by thomo2710 on 2011-10-26
Hi,

I need to run a chmod command at startup to set permissions on a particular file that seems to get stripped out every time the machine reboots.

I have created the following file and called it test.sh, made it executable and added it to the startup applications but i need to get around having to input the sudo password for it to run!

#!/bin/bash

chmod 777 /the/location/of/the/file.cmd

I login as a user called ASTAdmin - i have added this user to the admin, root and sudo groups but im still prompted for sudo password.

I know this necessarily isnt the correct way to go around things but security for this problem is not a massive issue as its just me that will use the machine and its on a local network with no internet access anyway.

Cheers in advance

---

### Post by typhoon_tip on 2011-10-26
Open a terminal window then:

```
sudo gedit /etc/rc.local
```

Place your script in that folder. Make sure that the path of the file to change is complete and absolute. Don't overwrite the exit 0 ! Write your code before it.

E.g.,


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

*[place a call to your script here !]*

exit 0
```

---

### Post by thomo2710 on 2011-10-26
Works an absolute treat.

Thankyou so much typhoon_tip

---

