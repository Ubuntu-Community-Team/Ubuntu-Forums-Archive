---
title: "Network Related Issues"
date: 2005-12-13
forum: General Help
---

### Post by Fergal1982 on 2005-12-13
Ok. Ive installed Ubuntu onto a PC whose only connection to the internet is Via a USB Connection at present. So far i have discovered the following issues:

1. after entering username and password, i get an error stating
> Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts
2. When attempting to run sudo, i get the following error
> sudo: unable to lookup ubuntu via gethostbyname ()
3. When clicking on System>Administration>Networking, it appears to be loading, but then finishes and nothing comes up on screen (no error msg either).

Im fairly sure they are all related to the network issue. But have no idea where to even start in resolving the issue, and would appreciate any help. If we could get the USB network connection working that would be a bonus, but id be happy to get this up and running properly.

Thanks
Fergal

---

### Post by Original Brownster on 2005-12-13
Hi,

from a terminal type

less /etc/hosts

You should have an entry near the top like:

127.0.0.1 localhost.localdomain localhost ubuntu

my hostname is ubuntu and I suspect yours is too. You should have this line in the /etc/hosts file so the name can be resolved to the local ip 127.0.0.1 ie itself.

When you say usb connection to the internet could you give more information please. Do you mean you have a usb modem, if so what model / type etc.

Regards

---

### Post by Fergal1982 on 2005-12-13
i have a BT Broadband ADSL Router. It has one ethernet connection, and one USB connection. This PC is currently hooked up to the USB connection (laptop got the ethernet).

Model i believe is a Bt Voyager 205.

The hosts file only contains > 127.0.0.1 localhost

not sure how to update this since its a read-only file, both in gedit, and vi.

Fergal

---

### Post by aclaunch on 2005-12-13
You could try being root with "sudo su" in a terminal and see if that works; then you can edit your /etc/hosts file.

Good Luck, 
Alan

---

### Post by Original Brownster on 2005-12-14
[QUOTE=Fergal1982]i have a BT Broadband ADSL Router. It has one ethernet connection, and one USB connection. This PC is currently hooked up to the USB connection (laptop got the ethernet).

Model i believe is a Bt Voyager 205.

The hosts file only contains 

not sure how to update this since its a read-only file, both in gedit, and vi.

Fergal[/QUOTE]
Hi,
I would use:
sudo vi /etc/hosts

but if you like gedit, from the menu there's an option to run application as different user, choose this then enter  root as the username and your password and gedit as the app. to run.

edit the localhost line so it is like my example and it should be good.

If your laptop is running windows I would go for the easy option and use the usb connection to your laptop and use the ethernet connection to your pc as this is real easy to configure.

Regards

---

### Post by Fergal1982 on 2005-12-14
given the issues with Sudo, im not entirely sure if this will work. will give it a go when i get home.

---

### Post by Original Brownster on 2005-12-14
[QUOTE=Fergal1982]given the issues with Sudo, im not entirely sure if this will work. will give it a go when i get home.[/QUOTE]
Hi,
What issues with sudo?

Regards

---

### Post by Fergal1982 on 2005-12-14
Number 2 in the original post. it refuses to run sudo.

---

### Post by Original Brownster on 2005-12-14
Now that is interesting, what about switching to a another TTY (ctrl-alt + F2) then logging in and trying sudo? 

Regards

---

### Post by Fergal1982 on 2005-12-14
nope. same error.

---

### Post by Original Brownster on 2005-12-14
Have you tried booting into recovery mode (single user mode)  and editing the files?

---

### Post by Fergal1982 on 2005-12-14
ummm. nope. can get into vi into the file this way. what do i need to enter? should i just append 'ubuntu' to the end of what is currently in hosts?

---

### Post by Fergal1982 on 2005-12-14
got it. it seems to have resolved the issue.

trying to set a root password now, but following the command in the FAQ just brings up a password prompt, and entering a password just makes it reject the password.

---

### Post by Original Brownster on 2005-12-15
[QUOTE=Fergal1982]got it. it seems to have resolved the issue.

trying to set a root password now, but following the command in the FAQ just brings up a password prompt, and entering a password just makes it reject the password.[/QUOTE]

Hi,
Glad you got it sorted.
With regards to setting a root password, please read [this]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin") if you haven't already and sorry if you knew this, but it explains why it's better to  leave root disabled.

Regards

---

### Post by Original Brownster on 2005-12-15
[QUOTE=Fergal1982]got it. it seems to have resolved the issue.

trying to set a root password now, but following the command in the FAQ just brings up a password prompt, and entering a password just makes it reject the password.[/QUOTE]

Just a thought, if your trying to set the password with the command:

$sudo passwd root

You are in fact being asked for your user password first, Then you will be asked for the root password followed by a confirmation.

Regards

---

