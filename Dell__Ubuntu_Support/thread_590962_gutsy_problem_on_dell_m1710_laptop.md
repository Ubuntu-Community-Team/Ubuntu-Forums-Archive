---
title: "gutsy problem on dell m1710 laptop"
date: 2007-10-25
forum: Dell  Ubuntu Support
---

### Post by phobophile on 2007-10-25
ok, newb here so bear with me.

got a Dell XPS laptop (m1710), system MXG061.

intel core 2 duo 2.16GHz, 2GB DDR2 SDRAM.

NVIDIA geforce go 7950 gtx.

running XP pro, feisty and (hopefully) gutsy

 fresh install of gutsy from alternate CD. Install worked fine, even got the full disk crypto running without too many hassels. updated everything fine, downloaded some themes fine, rebooted 3 or 4 times no worries. (last thing i did was download and install - but not configure - tor and privoxy)

But now, i get an error message after grub when it tries to initialise the kernel and will not load (works in recovery mode tho).

most common error is :

[ 4.532000] usb 1-1 device not accepting address 2, error -71


sometimes it gives 4 lines of error messages but all quote ( -71) at the end. ( just got a couple)

[ 4.848000] hub 1-1.2:1.0: connect-debounce failed, port 2 disabled


[ 4.848000] hub 1-1.2:1.0: cannot disable port 2 (err = -71)


[ 4.848000] hub 1-1.2:1.0: hub_port_status failed (err = -71)


any help greatly appreciated, as i really would like to avoid having to do a re-install. ( i've definately not got any usb devices plugged in.)

i've managed to change the error, by altering the place of the usb drives in the bios boot priorities menu, i even disabled the usb boot ability. but gutsy still wont load

---

### Post by phobophile on 2007-10-25
lil help?  :)   

i'm gona do a reinstall later today if no-one has any ideas.

---

### Post by phobophile on 2007-10-25
OK, through trial and error (mostly error) i figured out this is a problem between gutsy and  usplash-theme-satanic ([www.ubuntusatanic.org](www.ubuntusatanic.org)) .  

interestingly enough, it worked after i installed it and rebooted, it's only from cold starts that it causes those errors. 

to resolve  (from recovery):

update-alternatives --set usplash-artwork.so \
/usr/lib/usplash/usplash-theme-ubuntu.so

update-initramfs -u

then just removed the package after a successful boot.

---

### Post by parker13 on 2007-10-26
> **phobophile said:**
> OK, through trial and error (mostly error) i figured out this is a problem between gutsy and  usplash-theme-satanic ([www.ubuntusatanic.org](www.ubuntusatanic.org)) .  

interestingly enough, it worked after i installed it and rebooted, it's only from cold starts that it causes those errors. 

to resolve  (from recovery):

update-alternatives --set usplash-artwork.so \
/usr/lib/usplash/usplash-theme-ubuntu.so

update-initramfs -u

then just removed the package after a successful boot.

Hi Phobophile,

I'm sorry to hear that one of our packages caused this problem. I have to say that it's the first time I've heard of anything like this. I'd be very interested to hear from anyone who has had a similar experience.

I've raised a bug on Launchpad for this issue.

[https://bugs.edge.launchpad.net/usplash-theme-satanic/+bug/157465](https://bugs.edge.launchpad.net/usplash-theme-satanic/+bug/157465)

Thanks,
Garry.

---

### Post by phobophile on 2007-10-29
hey Garry, thanks for the reply.    and cheers for the themes, love the desktops and screensavers.  

keep up the good work

-P

---

