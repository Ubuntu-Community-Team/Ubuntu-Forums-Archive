---
title: "Help regarding an error message ..."
date: 2006-09-21
forum: Desktop Environments
---

### Post by mmmpancakes on 2006-09-21
I've attached my JVC digital camcorder to my PC via Firewire. I open Kino, which starts fine, but when I click the capture tab, I get an error message at the bottom that says "WARNING: raw1394 kernal module not loaded or failure to read / write /dev/raw1394!" .

I can't seem to capture video from this point. I searched the forums/Google without luck.

---

### Post by ape on 2006-09-21
So, is the raw1394 module loaded?  Type 'lsmod | grep raw1394' in a terminal window and see if you get anything back.  

If nothing is output from the command, type 'sudo modprobe raw1394' and hit Enter.  If you get no error messages, issue the lsmod command above again and see if you now have the module loaded. If the module is loaded, try your application again.

---

### Post by mmmpancakes on 2006-09-21
When I do lsmod | grep raw1394 in the terminal, this is my output:

raw1394                30956  0
ieee1394              299832  3 raw1394,sbp2,ohci1394

Then, when I do sudo modprobe raw1394, I get no error messages. 

The error message persists when I start Kino. 

Any ideas?

---

### Post by ape on 2006-09-22
Okay, so on to the next steps<G>:

1. Does the device /dev/raw1394 exist?
2. What are the permissions on it?


If the device isn't showing up, or the permissions aren't set properly, try looking at the following thread:

[http://ubuntuforums.org/showthread.php?t=2792]("http://ubuntuforums.org/showthread.php?t=2792")

Specifically pay attention to the entries about adding the raw1394 and video1394 modules to the /etc/modules file (if they don't already exist) and the links regarding getting the permissions to stick with udev.

Good luck.

---

### Post by mmmpancakes on 2006-09-22
Ok, I was able to search the /dev folder, and I do -not- see raw1394. 

Any pointers on how to get it there? I couldn't find it in the link Ape provided.

---

### Post by mmmpancakes on 2006-09-22
Update:

Ok, I did

mknod /dev/raw1394 c 171 0

and now, raw1394 is showing up in /bin

Now, according to the link, I want to edit the /etc/init.d/bootmisc.sh file with the following:

Quote:
# Begin Edit. 20041031 RCB - Added to hopefully get the raw1394 devicenode.
mknod /dev/raw1394 c 171 0
chown root:video /dev/raw1394
chmod 666 /dev/raw1394
#End Edit

: exit 0 

I located the file, but when I open it, it won't let me make changes, saying I'm not logged in as owner. I'm logged in as the only user on this system. How do I do that?

And, once I do, do I simply add the code above to the document? Does it matter where? 

Thanks again!

---

### Post by mmmpancakes on 2006-09-22
bump [-o<

---

### Post by ape on 2006-09-23
Okay, so the commands above should be done at the terminal using the sudo command:

i.e 'sudo mknod /dev/raw1394 c 171 0'

and 
'sudo <insert your favorite editor here> /etc/init.d/bootmisc.sh'

These shouldn't be done as a normal user.

Once you've completed the above, reboot the machine and see if you are able to access the raw1394 device.

---

