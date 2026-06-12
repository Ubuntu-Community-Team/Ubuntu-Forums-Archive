---
title: "Truecrypt mount / unmount script"
date: 2007-03-09
forum: Desktop Environments
---

### Post by rob_jewkes on 2007-03-09
For anyone interested i have written a small script to mount and unmount truecrypt volumes. On mount it will ask for your password in a password requester box. Once mounted it will add a Notification icon to the top panel, to unmount your truecrypt volume simply click this icon.



```


#!/bin/bash

# -------- Set the following variables to your own config ----------------

# location of truecrypt binary
TRUECRYPT=/usr/bin/truecrypt

# file containing an encrypted volume
ENCRYPTEDFILE=/home/tcvol.tc

# where to mount the volume
MOUNTPOINT=/media/tcmnt
# ------------------------------------------------------------------------

function update_volismounted {
VOLISMOUNTED=`$TRUECRYPT -l|grep $ENCRYPTEDFILE`
}


function unmount_volume {
zenity --notification --text "TrueCrypt dismount"
zenity --question --title "TrueCrypt" --text "Dismount your TrueCrypt volume?"
if [ $? == 0 ] ; then
$TRUECRYPT -d $ENCRYPTEDFILE
else
unmount_volume
fi
}

update_volismounted
if [ "$VOLISMOUNTED" ]; then
  # Message Output
    zenity --error --title "TrueCrypt" --text="TrueCrypt volume already mounted!"
else
  # mount the volume
  gksu -p --message "Please enter your TrueCrypt password for $ENCRYPTEDFILE" | $TRUECRYPT -u $ENCRYPTEDFILE $MOUNTPOINT

  update_volismounted
  if [ "$VOLISMOUNTED" ]; then

unmount_volume

  else
    zenity --error --text="Mounting of TrueCrypt volume failed."
  fi
fi

```

Hope its of use to someone :? 

Rob

---

### Post by chewearn on 2007-03-10
Hey, thanks man, really handy script!  :popcorn:

Oh, and sorry for asking, but if I unmount while some apps is accessing the content (e.g. natillus is show the directory), the unmount fails, but the script just ended/exited.  How do I detect if the unmount fails, so the script can give a message and loop back to mounted condition?  Thanks in advance.

---

### Post by chewearn on 2007-03-10
Ok, never mind.  I modify your code (copy pasting) to add a check for failed unmount.  Thanks again!

```

#!/bin/bash

# -------- Set the following variables to your own config ----------------

# location of truecrypt binary
TRUECRYPT=/usr/bin/truecrypt

# file containing an encrypted volume
ENCRYPTEDFILE=/home/tcvol.tc

# where to mount the volume
MOUNTPOINT=/media/tcmnt
# ------------------------------------------------------------------------

function update_volismounted {
  VOLISMOUNTED=`$TRUECRYPT -l|grep $ENCRYPTEDFILE`
}


function unmount_volume {
  zenity --notification --text "TrueCrypt dismount $ENCRYPTEDFILE"
  zenity --question --title "TrueCrypt" --text "Dismount your TrueCrypt volume $ENCRYPTEDFILE?"
  if [ $? == 0 ] ; then
    $TRUECRYPT -d $ENCRYPTEDFILE

    update_volismounted
    if [ "$VOLISMOUNTED" ]; then
      zenity --error --title "TrueCrypt" --text="TrueCrypt volume cannot unmount!"
      unmount_volume
    fi
  else
    unmount_volume
  fi
}

update_volismounted
if [ "$VOLISMOUNTED" ]; then
  # Message Output
  zenity --error --title "TrueCrypt" --text="TrueCrypt volume already mounted!"
else
  # mount the volume
  gksu -p --message "Please enter your TrueCrypt password for $ENCRYPTEDFILE" | $TRUECRYPT -u $ENCRYPTEDFILE $MOUNTPOINT

  update_volismounted
  if [ "$VOLISMOUNTED" ]; then
    unmount_volume
  else
    zenity --error --text="Mounting of TrueCrypt volume failed."
  fi
fi

```

---

### Post by rob_jewkes on 2007-03-17
Pleased you found it useful :)

---

### Post by orb9220 on 2007-03-17
Also there is now the gui and truecrypt can be installed from Automatix2

Just installed and now have a GUI front-end for truecrypt

---

### Post by chewearn on 2007-03-24
> **orb9220 said:**
> Also there is now the gui and truecrypt can be installed from Automatix2

Just installed and now have a GUI front-end for truecrypt

Nice.  Thanks for the tip, but how do I install the GUI front-end without using Automatix?  I tried going to the automatix website, it's unaccessible at the moment.  Also, my system was badly screwed in the past by Automatix, so I am wary of installing it again.

---

### Post by jackrobinson on 2007-03-24
> **AstalaVista said:**
> Nice.  Thanks for the tip, but how do I install the GUI front-end without using Automatix?  I tried going to the automatix website, it's unaccessible at the moment.  Also, my system was badly screwed in the past by Automatix, so I am wary of installing it again.
you sure it was automatix which screwed your system and not some fancy third party repo you added? The truecrypt GUI packages are maintained by the automatix team. you need their repository enabled.

---

### Post by chewearn on 2007-03-24
> **jackrobinson said:**
> you sure it was automatix which screwed your system and not some fancy third party repo you added? The truecrypt GUI packages are maintained by the automatix team. you need their repository enabled.

Ok, checked automatix website again and got in.  Been spending a few hours reading about various thread in this forum and in the automatix forum.  Looks like automatix has improved a lot and getting glowing endorsement from many.

Just to clarify, I last tried using it about a year ago.  Any "fancy third party repo", as you put it, was added by automatix then; but I understand that it doesn't do this anymore.

Thanks for the feedback, I will consider installing it.

---

### Post by banditti on 2007-03-29
Thanks for the heads up on this!  It helps.

---

### Post by hades_6_6_6 on 2007-04-02
Thanks for the script. It is very useful.
However I'd love to get for it an entry to the context menu.
That's the scenario:
- Select a .tc file in nautilus
- right click on it
- select the "TrueCrypt mount" entry
- the script prompt for tc-passwd.

Unfortunately, I'm a new be and have no idea how to realize it. Could you help?

---

### Post by alohre on 2007-04-20
another iteration of this script :)

1. put this file in /home/username/.gnome2/nautilus-scripts and make executable.
2. make directory /media/truecrypt
3. chown username.username /media/truecrypt

Now you can right click a file in nautilus and choose scripts->truecrypt to mount the volume, and it will show up in the browser with the same name as the file you mount.



```
#!/bin/bash

# -------- Set the following variables to your own config ----------------

# location of truecrypt binary
TRUECRYPT=/usr/bin/truecrypt

# file containing an encrypted volume
ENCRYPTEDFILE=$1

# where to mount the volume
MOUNTDIR=/media/truecrypt
MOUNTPOINT=$MOUNTDIR/$1
mkdir $MOUNTPOINT
# ------------------------------------------------------------------------

function update_volismounted {
VOLISMOUNTED=`$TRUECRYPT -l|grep $ENCRYPTEDFILE`
}


function unmount_volume {
zenity --notification --text "TrueCrypt dismount $ENCRYPTEDFILE"
zenity --question --title "TrueCrypt" --text "Dismount your TrueCrypt volume $ENCRYPTEDFILE?"
if [ $? == 0 ] ; then
$TRUECRYPT -d $ENCRYPTEDFILE

update_volismounted
if [ "$VOLISMOUNTED" ]; then
zenity --error --title "TrueCrypt" --text="TrueCrypt volume cannot unmount!"
unmount_volume
fi
else
unmount_volume
fi
}

update_volismounted
if [ "$VOLISMOUNTED" ]; then
# Message Output
zenity --error --title "TrueCrypt" --text="TrueCrypt volume already mounted!"
else
# mount the volume
gksu -p --message "Please enter your TrueCrypt password for $ENCRYPTEDFILE" | $TRUECRYPT -u $ENCRYPTEDFILE $MOUNTPOINT

update_volismounted
if [ "$VOLISMOUNTED" ]; then
unmount_volume
else
zenity --error --text="Mounting of TrueCrypt volume failed."
fi
fi
```

---

### Post by Khaine on 2007-04-20
Thats awesome :D

---

### Post by hades_6_6_6 on 2007-04-20
I've just tested it and love it\\:D/ 
That is exactly what I wanted. Thanks a lot.

---

### Post by Masuran on 2007-12-10
The unmounting didn't work on Ubuntu 7.10 and EasyCrypt  4.3a

To fix it I replaced this line
$TRUECRYPT -d $ENCRYPTEDFILE
with this line
$TRUECRYPT -d $MOUNTPOINT

Appearantly TrueCrypt couldn't unmount a volume when you pass the encrypted file path, only when passing the mountpoint.

---

### Post by chewearn on 2008-01-02
Here is my most recent modification to mount a partition.
You need to change 3 things:
1. TRUECRYPT=...
2. MOUNTPOINTPATH=...
3. list of /dev/xxx for the zenity dialogbox

```
#!/bin/bash

# -------- Set the following variables to your own config ----------------

# location of truecrypt binary
TRUECRYPT=/usr/bin/truecrypt

# where to mount the volume
MOUNTPOINTPATH=/home/user/

# list of /dev/xxx
ENCRYPTEDFILE=`zenity --height=420 --list --text="Test title" --radiolist --column=Select --column=Device \
  a "/dev/sda1" b "/dev/sdb1" c "/dev/sdc1" d "/dev/sdd1" e "/dev/sde1" \
  f "/dev/sdf1" g "/dev/sdg1" h "/dev/sdh1" i "/dev/sdi1" j "/dev/sdj1"`

# ------------------------------------------------------------------------


if [ $? == 1 ] ; then
#  echo Cancelled
  exit
fi

MOUNTPOINTDIR=`echo $ENCRYPTEDFILE | cut -c6-8`
MOUNTPOINT=$MOUNTPOINTPATH$MOUNTPOINTDIR


function update_volismounted {
  VOLISMOUNTED=`$TRUECRYPT -l | grep $ENCRYPTEDFILE | cut -c0-22`
}

function update_volismounted_w_passwd {
  VOLISMOUNTED=`gksu -p --message "Please enter your user's password" | $TRUECRYPT -l | grep $ENCRYPTEDFILE | cut -c0-22`
}

function unmount_volume {
  zenity --notification --window-icon=/usr/share/pixmaps/gnome-eog.xpm --text "TrueCrypt dismount $ENCRYPTEDFILE"
  zenity --question --title "TrueCrypt" --text "Dismount your TrueCrypt volume $ENCRYPTEDFILE?"
  if [ $? == 0 ] ; then
    update_volismounted_w_passwd
    $TRUECRYPT -d $VOLISMOUNTED

    update_volismounted
    if [ "$VOLISMOUNTED" ]; then
      zenity --error --title "TrueCrypt" --text="TrueCrypt volume cannot unmount!"
      unmount_volume
    fi
  else
    unmount_volume
  fi
}

update_volismounted_w_passwd
if [ "$VOLISMOUNTED" ]; then
  # Message Output
  zenity --error --title "TrueCrypt" --text="TrueCrypt volume already mounted!"
else
  mkdir $MOUNTPOINT

  # mount the volume
  gksu -p --message "Please enter your TrueCrypt password for $ENCRYPTEDFILE" | $TRUECRYPT -u $ENCRYPTEDFILE $MOUNTPOINT

  update_volismounted
  if [ "$VOLISMOUNTED" ]; then
    unmount_volume
  else
    zenity --error --text="Mounting of TrueCrypt volume failed."
  fi

  rmdir $MOUNTPOINT
fi
```

---

