---
title: "Mysterious Padlock on File ???"
date: 2008-09-11
forum: Desktop Environments
---

### Post by 22moondune on 2008-09-11
I am fairly new to Linux and Ubuntu for that matter.  I have been noticing that sometimes when I copy a file or move a file from a disc or flashdrive to my desktop, it will suddenly have a padlock on it.  This prevents me from deleting the file, dragging it anywhere else, and modifying it.  I know that the permissions in Linux are different from Windows by far, but is there a way I can get rid of the padlock?  I need to modify some files.

---

### Post by atoc on 2008-09-12
Right click on the file and select "properties".
There's a permissions tab. Change it so you have read/write access and you're golden.
The file's permissions from the cd are inherited when you copy it over (in my experience,sometimes that happens, sometimes it doesn't. Can't explain why).

---

### Post by ache109 on 2008-09-12
what if there are thousands of files that are locked? Is it acceptable to the CTRL + A thing and choose read and write to perissions?, Examples are my pictures..... from my golden cds

---

### Post by russo.mic on 2008-09-12
Sounds like the whole volume has it's permessions set as such.  Just change the permessions of the whole volume using the above method, only select the icon for the volume.

Also, you could go to a terminal and hit 

sudo chmod 777 '/somepath/somefiles'

Russo

---

### Post by IanW on 2008-09-12
To change permissions for everything in a particular folder, right-click on the folder and select the "Permissions" tab, set your permissions as needed, and click the button at the bottom of the permissions tab that says "Apply Permissions to Enclosed Files".

---

### Post by slick1a on 2010-06-21
and if the access drop down box is greyed out what then? 

also if "permissions of 'drive' cannot be determined"   what then?

---

### Post by Pengwyn44 on 2010-06-22
Are you logging in as 'root' when you are trying to remove the padlocks? If so it should be straightforward.
You can use the file browser Nautilus as root by opening a terminal and entering "gksudo nautilus". You will be asked for the root password. Next double click on "Media"to see the attached drives. Then change the permissions.

---

### Post by slick1a on 2010-06-22
Hmm so i logged in as root with my root pw.

through root i can see the offending files which do not have the padlock.....when i view said files from source they are still padlocked.

also when i try from source to unlock padlocks , it tells me im not the owner so therefore cannot do anything with them.

here are some of my findings.:

root@slick-desktop:~# sudo nautilus

(nautilus:7628): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(nautilus:7628): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:7628): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:7628): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:7628): WARNING **: No marshaller for signature of signal 'ShareCreateError'
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (process:7659): WARNING **: Couldn't change nice value of process.

** (process:7669): WARNING **: Couldn't change nice value of process.

** (process:7680): WARNING **: Couldn't change nice value of process.

** (process:7690): WARNING **: Couldn't change nice value of process.

** (process:7701): WARNING **: Couldn't change nice value of process.

** (process:7711): WARNING **: Couldn't change nice value of process.

** (process:7722): WARNING **: Couldn't change nice value of process.

** (process:7732): WARNING **: Couldn't change nice value of process.

** (process:7742): WARNING **: Couldn't change nice value of process.

** (process:7753): WARNING **: Couldn't change nice value of process.

** (process:7763): WARNING **: Couldn't change nice value of process.

** (process:7774): WARNING **: Couldn't change nice value of process.

** (process:7784): WARNING **: Couldn't change nice value of process.

** (process:7795): WARNING **: Couldn't change nice value of process.

** (process:7805): WARNING **: Couldn't change nice value of process.

** (process:7815): WARNING **: Couldn't change nice value of process.

** (process:7826): WARNING **: Couldn't change nice value of process.

** (process:7836): WARNING **: Couldn't change nice value of process.

** (process:7847): WARNING **: Couldn't change nice value of process.

** (process:7857): WARNING **: Couldn't change nice value of process.

** (process:7875): WARNING **: Couldn't change nice value of process.

** (process:7885): WARNING **: Couldn't change nice value of process.

** (process:7895): WARNING **: Couldn't change nice value of process.

** (process:7906): WARNING **: Couldn't change nice value of process.

** (process:7916): WARNING **: Couldn't change nice value of process.

** (process:7926): WARNING **: Couldn't change nice value of process.

** (process:7937): WARNING **: Couldn't change nice value of process.

** (process:7947): WARNING **: Couldn't change nice value of process.

** (process:7958): WARNING **: Couldn't change nice value of process.

** (process:7968): WARNING **: Couldn't change nice value of process.

** (process:7979): WARNING **: Couldn't change nice value of process.


which im guessing is not good.

---

### Post by slick1a on 2010-06-22
now it may be worth mentioning that nautlius and myself have had a bit of a tiff of late ...what with all aspects of 'places' (pictures , music documents etc etc) opening in VLC....instead of nautlius

i created another user ~ problem solved....but not convenient!

so ~ brainwave ~ uninstall VLC (which i swareby)  ~ problem solved.

When using hardy everything worked perfectly...now having upgraded to karmic things are a little shady.. i.e cannot burn anything...

Which brings me back to said locked files which are greyed out not allowing the option to change the permissions.

I need to unlock these files to free up space on hdd...which in turn i will burn (most of which are avi files :P ) if only i could unlock and burn.

i can change permissions in root , but cannot delete...grrr

---

### Post by slick1a on 2010-06-22
** (process:7968): WARNING **: Couldn't change nice value of process.

** (process:7979): WARNING **: Couldn't change nice value of process.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

