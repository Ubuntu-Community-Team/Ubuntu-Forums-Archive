---
title: "NVIDIA xrandr screen rotate problem"
date: 2008-01-30
forum: Desktop Environments
---

### Post by higgylm on 2008-01-30
[B][COLOR="Red"]**SOLVED**
[/COLOR][/B]
Hi there first off all thanks for looking,

For some reason i can cannot rotate the graphics 90[SIZE="1"]o[/SIZE] out put on my screen using xrandr, usually there is an option under preferences>screen resolution, however it doesn't appear.

I get this error message when using terminal to try and rotate...

xrander -o right

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Attached is a copy of my xorg.conf file.

any help appreciated :)

Thanks

---

### Post by higgylm on 2008-01-30
SOLVED

added

Option "Rotate" "left"

to my xorg.conf file

---

### Post by grantek on 2008-04-28
Thanks - I found this while googling for a solution to my screen rotate problems. I'd previously had the rotate option in my xorg.conf as needed, but I liked switching between rotated for coding/viewing documents, and normal for widescreen gaming.

I generated an xorg.conf with the help of nvidia-settings, but needed to add the option to allow RandR rotation:
```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
    Option         "RandRRotation" "true"
EndSection
```

After that, rotating the screen worked in Preferences->Screen Resolution :guitar:

---

### Post by Cygnus on 2008-05-10
Adding the option RandRRotation was not enough for me. It did not work until I used both:

Option   "RandRRotation" "true"
Option   "Rotate" "left"

and then ran xrandr -o left.

---

### Post by kid709394 on 2008-05-12
Hi new to linux..

How do u edit the xorg.conf and save it? tried to edit the file and it comes with the msg says "Could not save the file /etc/X11/xorg.conf

How do i gain root access to the file and make the changes?

Thanks

---

### Post by Cygnus on 2008-05-12
> **kid709394 said:**
> 

How do i gain root access to the file and make the changes?



If you are in a console you type 'sudo' before the command you want to use to edit the file. For example in kubuntu I can use 'sudo kate /etc/X11/xorg.conf' to edit the file as root in the kate editor.

---

### Post by foxmajik on 2008-07-09
I had to perform the following operations:

1. Install nvidia-settings

```
$ sude apt-get install nividia-settings
```

2. Open nvidia-settings as superuser

```
$ sudo nvidia-settings&
```

3. Click on X Server Display Configuration
4. Click Save to X Configuration File
5. Edit the resulting X configuration file

```
$ sudo nano /etc/X11/xorg.conf
```

6. Add this to the Device section underneath the Board Name line:

```
Option          "RandRRotation"      "on"
```

7. Save the file
8. Restart X with Ctrl-alt-backspace
9. Click on System --> Preferences --> Screen Resolution

I then found that I had the left, right, normal and upside down rotation options which could be applied dynamically.

For some reason just adding the Option line to the Device section didn't work, I had to use the nvidia control panel to create a new x.org config file and then add the line to it.

I hope this will help other nvidia users and I hope this will be fixed in a future version of ubuntu.

---

