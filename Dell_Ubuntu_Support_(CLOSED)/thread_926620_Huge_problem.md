---
title: "Huge problem"
date: 2008-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by renkinjutsu on 2008-09-22
I have a Dell Vostro 200
i ran the Ubuntu8.04 Live CD and it booted up fine,
that's when i decided to install Ubuntu...
after installation, Ubuntu booted up fine again, then every time after that, it wouldn't boot again.  It would bring me to a screen that resembles a commandline and says "busybox".

now here's the problem.. Ubuntu wouldn't boot, so for some reason, i decided to delete the partition Ubuntu was installed onto, and now the Grub loader keeps giving me an error, and i can't even boot onto Vista anymore.
and i CAN'T even boot onto the 8.04 Live CD anymore... i'm guessing the first time was just a fluke.  Right now, i'm typing this post while running on a Gutsy Gibbons Live CD...
is there anyway i can fix this mess?

---

### Post by gbrainin on 2008-09-22
I'm not familiar with that particlar model, but it sounds very similar to the IDE/RAID issue that is a known problem with 8.04 on the Inspiron 530.  As an experiment, try changing the hard drive mode from IDE to RAID (it's a setting in the BIOS setup) and then booting from the 8.04 CD.  If that works, then that is probably the issue.  See: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot").

---

### Post by larry80 on 2008-09-22
I had the same problem with my vostro 200.

to fix it I had to go into the BIOS and change the Drive controller to "RAID" and it worked fine.

[https://answers.launchpad.net/ubuntu/+question/40525](https://answers.launchpad.net/ubuntu/+question/40525)

Overall it works perfectly fine with this setup, and I've just left mine like this and dual boot windows xp and ubuntu fine :)

---

### Post by renkinjutsu on 2008-09-23
Wow, thanks guys!
i changed it to RAID in my BIOS, and now it boots up perfectly!
Great help.

---

### Post by gbrainin on 2008-09-23
Glad that helped.  I'm not sure if Vista will work with the RAID mode, but if it doesn't, you can switch back to IDE and use the boot switch mentioned in the web page instead.

---

