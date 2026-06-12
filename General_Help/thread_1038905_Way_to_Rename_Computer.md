---
title: "Way to Rename Computer?"
date: 2009-01-14
forum: General Help
---

### Post by airjaw on 2009-01-14
I've looked under System Admin for a way but nothing available.
I tried on command line by editing /etc/hostname file.
This works temporarily but I am unable to open any new windows or programs, and the changes are reverted upon a restart.

is this a bug? Any help would be appreciated.
If its not possible, its not possible, just wanted to know if there was a way.
Thanks.

just to clarify i am talking about computer name, as in XYZ@random-computer-name   and the name that appears over a network.

---

### Post by iaculallad on 2009-01-14
Aahh.. the Host Name:
System->Administration->Network, under the General tab.
HTH.

---

### Post by airjaw on 2009-01-14
> **iaculallad said:**
> Aahh.. the Host Name:
System->Administration->Network, under the General tab.
HTH.

Thanks for your help, and I've found that solution before.
The problem is, I don't have "Network" under System -> Administration.
I have a "Network Tools" but that doesn't seem to be right.

Also, is there a way to do this via command line? I'm looking for a more reliable way to do this, a generic linux command line way. I don't want to do it through Ubuntu's System settings because as you can see from this situation, I cannot always rely on the menus in whatever distro I am using.

---

### Post by iaculallad on 2009-01-14
Open your terminal and issue the command below:

```
gksudo network-admin
```

EDIT: Doing it in the terminal by editing the /etc/hostname file:

```
gksudo gedit /etc/hostname
```

Save and Close.

---

### Post by airjaw on 2009-01-14
gksudo network-admin failed to open networkadmin.

i've tried sudo editing /etc/hostname
but like I said.. that only temporarily changes it. And then I can't open any new windows or programs, and when I reboot to fix that problem, the computer name has been reverted to what it was before.

---

### Post by Ahadiel on 2009-01-14
> **airjaw said:**
> gksudo network-admin failed to open networkadmin.

i've tried sudo editing /etc/hostname
but like I said.. that only temporarily changes it. And then I can't open any new windows or programs, and when I reboot to fix that problem, the computer name has been reverted to what it was before.
You need to modify /etc/hostname AND change the appropriate line in /etc/hosts.

---

### Post by airjaw on 2009-01-14
hmm.. just edited /etc/hostname

now /etc/hosts has the updated computer name already.. The same problem of not being able to open any windows or programs has started again.

my etc/hosts:

> 127.0.0.1       yy-lap1-ubu810  localhost.localdomain   localhost
127.0.1.1       abcd-laptop

Do I have to change "abcd-laptop" as well?

---

### Post by airjaw on 2009-01-14
ok weird, but editing /etc/hostname worked this time!
I have no idea why it worked this time and not the last several times I tried it. 

Also, am I supposed to have a "Network" option under System --> Administration?  Cuz I don't have that, and also running gksudo network-admin doesn't work either, even tho it asks me for my password.

---

### Post by fulton on 2009-04-25
Ahadiel, this worked like a champ. Thank you very much! (especially since the network applet in 9.04 no longer seems to have a function for renaming your host via the gui)

I changed /etc/hostname first. When I went to change /etc/hosts, surprisingly, my new hostname was already there.

---

### Post by coru-mx on 2009-04-27
> **fulton said:**
> Ahadiel, this worked like a champ. Thank you very much! (especially since the network applet in 9.04 no longer seems to have a function for renaming your host via the gui)

I changed /etc/hostname first. When I went to change /etc/hosts, surprisingly, my new hostname was already there.

Thanks! This way seems to be fine.

---

