---
title: "FIX: VSYNC crashes Suspend/Hibernate"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by El Chupacabras on 2007-12-09
This problem has been bothering me forever now. A bug in the nvidia drivers breaks suspend/hibernate, but only when vsync is on.  I love my vsync and I hate having to enable it and disable it every time I use MPlayer. 

I remembered there being a fix for Beryl in which BerylManager was used to switch to Metacity when suspending and then back to Beryl when the system was resumed. SO, I chose to apply the same principle with the Vsync option.

 I will include the code below, but I gzipped a small package with the two scripts and an explanation. The code is pretty well commented, though.
Just use sudo gvim or sudo gedit <*file*> and paste the code into their respective files. (ex: sudo gvim /etc/acpi/suspend.d/05-comp-vsync-stop.sh) (to paste to gvim press these keys in this order: "+gp)


/etc/acpi/suspend.d/05-comp-vsync-stop.sh
```
#!/usr/bin/env bash

# This script is meant to work only in the version of Compiz Fusion 
# Distributed with Ubuntu Gutsy. It may work on other versions of Ubuntu
# and on Other distros, or it may not. You also need ACPI power-management
# installed on your system. It might work on APM, but I have no way of 
# testing such an adaptation.

# Based on Darwin Award Winner's fix, found here:
# http://ubuntuforums.org/showthread.php?p=2568654

# This script shall run when your computer goes down for Suspend or Hibernate
# It merely checks if Vsync is on in Compiz, and turns it off if it is.

# Get a list of users. This part is scary. It is necesary so we can turn off
# Vsync in each user's gconf. Again. It's scary. Newbies won't understand it.
USERS=`cat /etc/passwd | 
grep -E -e '/home/' | grep -Ev -e '/bin/false' | 
sed "s/^\([a-z]*\):.*$/\1/"`

# For every user on the system,
for USR in $USERS; do
    # Check if Vsync is on
    CURRNTVAL=`sudo -H -u $USR gconftool -g \
			/apps/compiz/general/screen0/options/sync_to_vblank`

    # If Vsync is on, Turn off Vsync in Compiz Settings with gconftool
    if [ "$CURRNTVAL" = "true" ]; then
    sudo -H -b -u $USR gconftool \
		-s /apps/compiz/general/screen0/options/sync_to_vblank \
		-t bool false
    
    # Create an temporary file to remind the resume script to turn vsync back
    # on
    sudo -H -b -u $USR touch /tmp/vsync-was-on
fi
done

# That's it! <sarcasm> That was simple wasn't it? </sarcasm>

```

/etc/acpi/resume.d/97-comp-vsync-start.sh
```
#!/usr/bin/env bash

# This script is meant to work only in the version of Compiz Fusion 
# Distributed with Ubuntu Gutsy. It may work on other versions of Ubuntu
# and on Other distros, but it may not. You also need ACPI power-management
# installed on your computer. It work on APM, but I have no way of testing
# such an adaptation.
# Adapted from Darwin Award Winner's fix, found here:
# http://ubuntuforums.org/showthread.php?p=2568654




# Get a list of users. This part is scary. It is necesary so we can turn on
# Vsync in each user's gconf. Again, It's scary. Newbies won't understand it.
USERS=`cat /etc/passwd | 
grep -E -e '/home/' | grep -Ev -e '/bin/false' | 
sed "s/^\([a-z]*\):.*$/\1/"`

# If 06-comp-vsync-stop.sh created a temporary file, log in as each user,
# and turn Vsync on
if [ -f /tmp/vsync-was-on ]; then
    
    # For every user on the system,
    for USR in $USERS; do
	# Start Vsyncin... Vsynching, Synching to Vblank
	sudo -H -b -u $USR gconftool \
	-s /apps/compiz/general/screen0/options/sync_to_vblank \
	-t bool "true"
    done
fi

# remove the temporary file
rm /tmp/vsync-was-on

# MOO
#
#         (__) 
#         (oo) 
#   /------\/ 
#  / |    ||   
# *  /\---/\ 
#     ~~   ~~   

```

You can also download the attached .tar.gz below. If anyone has any suggestions or can see how this could break some systems, please point it out to me.

PS. I hope this goes without saying, but as far as licensing, this is all Open Domain.

---

