---
title: "School environment.."
date: 2006-12-29
forum: Education &amp; Science
---

### Post by WSCAman on 2006-12-29
Hey, so it was recently proposed at the school where I work that we begin using Edubuntu for all the workstations on our network, also we have four servers running sun and redhat. My issue is that I have no idea what to consider, or how to go about securing the workstations in terms of thier local security.


 (I dont know if this should be in this forum or the security one)

---

### Post by bluefrog on 2007-01-02
you need to physically secure the machines by disabling cdrom/usb boot (basically just boot from HDD), securing bios, and assign a password to root to prevent people from booting in recovery mode and gain root access without password (ubuntu default).

other than that, it all depends on your network configuration, if you have centralized authentication, if you want to have one, if you don't care and just set up local users.

James

---

### Post by highvoltage on 2007-01-02
Hey WSCAman

Edubuntu is quite secure by default. It uses SSH for remote logins, as apposed to XDMCP, which means that user data is always encrypted over the network, The other benefit of Edubuntu is its Ubuntu base, so there's a large amount of support and a large amount of knowledge out there for it. Good planning never hurts for an implementation like this. I suggest you explain your setup to the Edubuntu mailing list, which you can find at [http://lists.ubuntu.com](http://lists.ubuntu.com)

There are many subscribers to the list who are able to give you advice, who have also set up many labs before.

-Jonathan

---

### Post by CanadianNorth on 2007-10-29
Hi there,

I am in a similar situation. How can I prevent users from changing the background, for example, or editing the menu?

---

### Post by Crafty Kisses on 2007-10-30
> **WSCAman said:**
> Hey, so it was recently proposed at the school where I work that we begin using Edubuntu for all the workstations on our network, also we have four servers running sun and redhat. My issue is that I have no idea what to consider, or how to go about securing the workstations in terms of thier local security.


 (I dont know if this should be in this forum or the security one)

It's pretty secure, don't worry about it. :)

---

### Post by LaserJock on 2007-10-30
> **CanadianNorth said:**
> Hi there,

I am in a similar situation. How can I prevent users from changing the background, for example, or editing the menu?

You might want to look into pessulus and sabayon.

-LaserJock

---

### Post by jeffbilling on 2007-11-04
> **CanadianNorth said:**
> Hi there,

I am in a similar situation. How can I prevent users from changing the background, for example, or editing the menu?


I am also embarking on this journey (I am concentrating on using Gcompris at the moment - brilliant program if you are working with young students).

I am working with students with special needs and on a single machine. I give each student a user name and password (very simple usually their own name again) and once I have set them up I just kill everything on the window except the application(s) I want them to have access to. Works a treat.

---

### Post by uwishurockedthishxc on 2007-11-05
also disable the ability to execute .exe files off flash drives.

---

