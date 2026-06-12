---
title: "usb keys not recognized"
date: 2005-08-01
forum: Desktop Environments
---

### Post by RevNomad on 2005-08-01
This is my first posting, I've been using Ubuntu on my Dell laptop for about 6 weeks.  Tonight it stopped recognizing my USB keys.  I have no idea what changed or where to go to make corrections.  This is a deal killer, I must have access to those keys.  

The keys themselves  are fine, at least my WinXP desktop recognizes and reads them.  It seems the problem is in Ubuntu or Gnome.  

Help!
Norman

---

### Post by Joeb on 2005-08-01
[QUOTE=RevNomad]This is my first posting, I've been using Ubuntu on my Dell laptop for about 6 weeks.  Tonight it stopped recognizing my USB keys.  I have no idea what changed or where to go to make corrections.  This is a deal killer, I must have access to those keys.  

The keys themselves  are fine, at least my WinXP desktop recognizes and reads them.  It seems the problem is in Ubuntu or Gnome.  

Help!
Norman[/QUOTE]


You might try typing:  sudo hotplug restart   (from the cli) and see if that fixes your problem.

Joeb

---

### Post by jasmuz on 2005-08-01
Open a terminal, and type: tail -f /var/log/messages
Plug in your USB Key, and watch if its recognized, paste the output to the forum.

If its recognized, try mounting it, to see what happens.

---

### Post by RevNomad on 2005-08-01
Well, I cannot paste it to the forum, as the laptop cannot connect to the 'net.  (winmodem)  but I'll try both suggestions and let you know.

Thanks.
Norman

---

### Post by RevNomad on 2005-08-01
Ok, hotplug restart did (apparently) nothing except push cpu usage to 100%

tail --f/var/log/messages gives this error message "unrecognized option"

I did some some checking and discovered lsusb which shows both keys as existing devices.

More suggestions please?
NTP

---

### Post by cwaldbieser on 2005-08-02
[QUOTE=RevNomad]
tail --f/var/log/messages gives this error message "unrecognized option"
[/QUOTE]

You need a space after the "-f".

```
tail -f /var/log/messages
```

Since you can see both keys with lsusb, you should be able to mount them manually with the "mount" command.  You first must figure out what device corresponds to a given USB key.  It usually ends up being /dev/sdb1 on my computer.  To find out what it is on yours:

Before plugging in the USB device:
```
$ ls /dev > before.txt
```
Then, plug in the usb device, and:
```
$ ls /dev > after.txt
```
And finally:
```
$ diff before.txt after.txt
```
Should tell you what devices were added after you plugged in.  For example, I see "sdb" and "sdb1".  The one with the number is the device I am after.

Next, you must have a directory where you are going to mount it.  /media/usbkey might be a good directory to create.  You may need to
```
$ sudo mkdir /media/usbkey
```

Now to mount it:
```

$ sudo mount /dev/sdb1 /media/usbkey
```

If you know the filesystem type, you can give that as a hint-- otherwise, the program will try to guess:

```
$ sudo mount -t vfat /dev/sdb1 /media/usbkey
```

Now you should be able to see the contents of the drive.

If this works, try searching the forums for "pmount"-- I vaguely recall that this program was associated with Ubuntu for mounting temporary storage in an easier fashion.  If not, let us know what went wrong.

---

### Post by RevNomad on 2005-08-02
Ok, I was able to access the usb key (and presumably the second one as well) from root.  I cannot write to it, mount it (although I can unmount it) from my user login.  Nor will Ubuntu respond to it being plugged in. 

 When I use the command line tools the people responding here have taught me I can mount, access etc.  again only from root.  

This is not acceptable.  I want to use Linux.  I like Ubuntu and the community.  I must be able to use these keys to transfer information from computer to computer.  I must be able to play movies and use my projector (but those are subjects for one or two more postings!).  Unless I can resolve this I will be forced to reinstall WinXP ](*,) .

Would a reinstall fix this?  Remember the laptop has no connection to the internet, unless I travel about 50 miles to a community college, the nearest wireless connection.

Eagerly awaiting your next suggestions.

Norman

---

### Post by Juergen on 2005-08-02
You're using the 'standard' Gnome as Desktop?
Try
```
ps aux | grep gnome-volume-manager
```and look if there are two lines (one will be for your grep)
This demon handles the 'automount' with correct permissions.

---

### Post by RevNomad on 2005-08-02
Yes, using Gnome.

Now heading off to try latest suggestion.


What if there is one line or 43 lines? :roll: 

NTP

---

### Post by RevNomad on 2005-08-02
Yes there were (at least) two lines.  But I have no idea what the codes mean or what to do now.

NTP

---

### Post by cwaldbieser on 2005-08-02
[QUOTE=RevNomad]Ok, I was able to access the usb key (and presumably the second one as well) from root.  I cannot write to it, mount it (although I can unmount it) from my user login.  Nor will Ubuntu respond to it being plugged in. 

 When I use the command line tools the people responding here have taught me I can mount, access etc.  again only from root.  
Norman[/QUOTE]

OK, I can explain that.  In order for the "mount" command to make it writable, you need an entry in your /etc/fstab.  However, I looked up the "pmount" command I mentioned before.  It turns out, that the point of that command is to mount external drives as a normal user without needing the /etc/fstab entry.  It is very similar to the mount command, but it always mounts under /media.  So if you had followed my advice from before and created the /media/usbkey folder, and your usbkey device is /dev/sdb1, then

```
$ pmount /dev/sdb1 usbkey
```
should mount your usbkey the way you want so you can read/write as a normal user if I am reading the docs correctly.

---

### Post by RevNomad on 2005-08-02
Hmmm, seems that I did that once :confused: 

I'll try again.  How do I convince Ubuntu or Gnome or someone to recognize and automount just as it did 12 hours ago?  

I just tried reinstalling but when it got to the paritioning part I gave up.  I even tried reinstalling WinXP but the reinstall CD (Dell) won't boot.   ](*,) 

NTP

---

### Post by RevNomad on 2005-08-03
Yea!!!!!!!!!!!!!!!!!!!!!!!!!

That worked, the system is now usable.  I still need to fix the automount problem.  But at least I can use the laptop again.

---

### Post by cwaldbieser on 2005-08-03
I think Jurgen was exploring the automounting aspect of your problem when he asked you to see if "gnome-volume-manager" was running.  According to the documentation, gnome-volume-manager is the program that is supposed to detect and automount the usb devices for you.  So if that program isn't running for some reason, that would explain why the automount was not working.

---

### Post by RevNomad on 2005-08-03
Hmmm I remember testing that based on other comments in this thread and others I have followed.  If I understood the messages correctly gnome-volume-manager is running.


NTP

---

### Post by RevNomad on 2005-08-03
Another thread [here](http://www.ubuntuforums.org/showthread.php?p=284824#post284824) discussed hal.  Once I got over the shakes (2001) I checked hal.  It's group memberships were messed up so I reset per that thread.  No joy.

What next?

NTP

---

### Post by RevNomad on 2005-08-03
Oh happy day! \\:D/  \\:D/  \\:D/  (I can't dance in real life either.)

Following a reboot the hal settings worked.  The machine now recognizes and automounts usb keys.
 \\:D/ 
 \\:D/ 
 \\:D/ 
 \\:D/

---

