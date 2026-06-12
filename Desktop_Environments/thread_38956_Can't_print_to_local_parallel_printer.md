---
title: "Can't print to local parallel printer"
date: 2005-06-02
forum: Desktop Environments
---

### Post by lakuma on 2005-06-02
I am unable to print to my Laser Printer that is connected directly to my machine via a parallel cable.  This is the message that I get from the /etc/cups/printers.conf file

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu Jun  2 18:22:59 2005
<DefaultPrinter Okipage-10ex>
Info Okipage-10ex
Location 
DeviceURI parallel:/dev/lp0
State Stopped
StateMessage Unable to open parallel port device file "/dev/lp0": Permission denied
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Linux recogizes the printer but it's not opening the parallel port. I've even tried switching the parallel port from /dev/lp0 to /dev/lp1 and nothing works.  Any help I would appreciate it!

---

### Post by cwaldbieser on 2005-06-03
If you type the following at the terminal:

```
$ ls -al /dev/lp0
```

can you see who has permissions for the device?  If your user account doesn't have sufficient permissions to access it, try adding yourself to the group that has write permission to it, or chmod the permissions so you have access.

---

### Post by lakuma on 2005-06-06
I checked to see who had write permissions to the parallel port and it's telling me only root does.  I added myself to the root group and I'm still unable to print!  It's still giving me the same message:

StateMessage Unable to open parallel port device file "/dev/lp0": Permission denied

I don't understand why it won't give me access to my own printer!

This is getting very frustrating because I need to be able to print.  Any advice I would greatly appreciate it.

---

### Post by sethmahoney on 2005-06-06
You can try going to System->Administration->Users and groups, then clicking on your user name, clicking Properties, clicking Advanced, and making sure any printer-related boxes are checked.

---

### Post by kenworth on 2005-06-06
Check to see if your printer is physically connected and can be seen by ubuntu by typing ;

sudo cat /etc/motd >  /dev/lp0

then ....

cat > /dev/lp0

and type Control-L character to feed page, followed by Control-D.

Advise if this works and you can read the output.

---

### Post by johnprgr on 2005-06-07
I had this problem also,  permissions are controlled by the file '/etc/udev/permissions.d/udev.permissions'.  My printer is usb and this is the line that handles it from my udev.permissions "usb/lp[0-9]*:root:lp:0666".  The "root:lp" is what user and group to set it up as.  You should be able to make your user a member of the "lp" group (using kuser) and all should be well.  I changed the mode to "0666"  this makes it writeable by "others" it was originally "0660" for mine.  Either way it should work.

Hope this helps

---

### Post by lakuma on 2005-06-10
Johnprgr...That worked perfectly!  Now I can print to my printer!  Thank you so much.  I knew I had to change my permissions to that port somewhere I just didn't know where or how.  I tried putting my self in different user groups thinking that might work, but it didn't.  But once I tried your suggestion it worked wonderfully!!  Thanks again for everyones help!!    :)

---

