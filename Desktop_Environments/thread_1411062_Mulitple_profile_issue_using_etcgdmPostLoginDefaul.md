---
title: "Mulitple profile issue using /etc/gdm/PostLogin/Default."
date: 2010-02-19
forum: Desktop Environments
---

### Post by tgoatley on 2010-02-19
Problem: The problem is running the /etc/gdm/PostLogin/Default script in Ubuntu 9.10. When I log in as a user it will not give me the base profile that I setup for it to use. Please read the following.

We are under development at our Washoe County Library to start implementing Ubuntu both staff and Public. For our Public Internet I need to offer some security to our Patrons so I:

The following is an example of how this functions in Ubuntu 9.04.

1. Create multiple user profiles. I setup 1 profile as needed that will serve as the base profile for all other profiles with pattern lnxlib*. At /home I create the "base" profile that will be used ( cp -r somealreadycreatedprofile base) .
2. From /etc/gdm/PostLogin/Default.sample I recreate the Default file as per file instructions. Then, add the scripting and as root run the script from the prompt $./Default

Here is the file contents and script that was added:

#!/bin/bash (this line in Default.sample comes #!/bin/sh so I changed it)
#
# Note: this is a sample and will not be run as is. Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run. This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that. $HOME, $LOGIN and such will all be
# set appropriately and this script is run as root

#Script for resetting home directory
if [[ "$LOGNAME" == lnxlib* ]] ; then
rm -rf $HOME
cp -a /home/base $HOME
chown -R $LOGNAME:$LOGNAME $HOME
exit 0

else
exit 0
fi

3. I then setup timekpr according to the profile names (in the script example it is lnxlib*) then, restart the machine and viola`. The same desktop appears (as I set it up from the profile I created and renaming is base) for each patron that signs in.
4. I point it to the squid proxy and let the filtering take place.

I think you get the gist.

This is seemless with 9.04 and works great but 9.10 can't get past the ./Default phase . I could really use someones help. We would like to upgrade and keep this project moving.

Thank you
Todd Goatley

---

### Post by Jonnox on 2011-02-23
Not sure if this is the same bug, but if you are using autologin, there is a bug (at least in 10.04) that /etc/gdm/PostLogin/Default is not run. If you remove autologin and force the user to login (even if the user has no password) it is then run.

---

