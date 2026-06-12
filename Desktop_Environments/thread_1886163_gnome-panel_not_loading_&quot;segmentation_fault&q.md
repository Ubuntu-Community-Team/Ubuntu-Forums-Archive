---
title: "gnome-panel not loading: &quot;segmentation fault&quot; error"
date: 2011-11-24
forum: Desktop Environments
---

### Post by yoramdavid on 2011-11-24
Hi,

When booting into Ubuntu gnome, the gnome-panel does not load.
running the command gnome-panel, the panel loads for a second, then crashes and returns an error:
```
gnome-panel

(gnome-panel:16821): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed
Falha de segmentação (segmentation fault)

```

If I use the "sudo" command, then the gnome-panel loads but also returns an error:
```
sudo gnome-panel

(gnome-panel:16943): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x206ad70'

** (gnome-panel:16943): WARNING **: Could not get presence from session manager.

** (gnome-panel:16943): WARNING **: Could not ask session manager if shut down is available: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```
But many programs do not load (some return the error that they cannot be opened as "root", others return the error that "not found", other return the error "not possible read file". Perhaps because everything is launched as "sudo" since the gnome panel is now running as "sudo"?

I once tried to boot in the recovery mode. To my surprise, It booted with the root account and there the gnome panel was working.

Anyone has an idea of what is happening?
Thank you in advance for any help.

---

### Post by yoramdavid on 2011-11-30
Since no solution was available, this is what I did:

1 - Create new account with administrator privileges. (there is a way to create a new temp account)
2 - Backup home folder of old account.
3 - Login into new account
4 - Delete old account with its files.
4 - Create new account 2 with same username as old account
5 - Login new account 2 and delete previous account
6 - Replace (some) of the home folder into new account to keep settings of programs (worked for Thunderbird, not for Firefox)
Panel works in new account.

Is this a solution?
Perhaps better than re-installing the system again, which was not possible now.
Shall I mark this threat as solved?

---

### Post by yoramdavid on 2011-12-09
Ubuntu 11.10 gnome-classic desktop

Yesterday when uninstalling clementine, my gnome-panel disappeard.
I used the command:
<code>sudo apt-get purge clementine</code>
I tried to reinstall clementine but it would not install.

I then ran a backup with simple backup restore, and the gnome-panel came back but when I rebooted the computer, I was caught in the login gdm loop not being able to login with the gui.

I tried the following solution without success:
<code>
ls -Shla | grep "Xauthority"
sudo mv .Xauthority Xauthority.old
sudo shutdown -r now
</code>

What shall I do? Delete my account again and create a new one again?
Any easier solution?
This is very frustrating.

---

### Post by yoramdavid on 2011-12-17
Hello all,

I am still having many problems here.
Gnome-panel was working again, then while installing Audacity (re-installing), the panel disappears when I click on the main menu.
Not when I click on the programs or icons, but when I click on the main menu, the panel vanishes then reappears.... :(

Any way to fix this?

Any help would be appreciated.

Thank you.

---

### Post by yoramdavid on 2011-12-17
Please help, I cannot access my programs via main menu.

This is the code generated when running gnome-panel from the console:
```
gnome-panel

(gnome-panel:15338): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion `GTK_IS_ORIENTABLE (orientable)' failed

(gnome-panel:15338): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x2328810'
Falha de segmentação

```

When I click on the main menu, the error generated is:
```
Falha de segmentação
```
(Segmentatin fault)

---

### Post by matt_symes on 2011-12-17
Hi

First thing i would run - to eliminate them - are hardware tests. 

Test your memory (leave it running overnight) and your hard drive for bad sectors. Check the SMART status of the drive if you have it. 

If this is a laptop has that manufacturer tests then run them (Dell have done this).

Test all cabling and ensure everything is seated correctly. Test the power supply and voltages.

When you have done that then look for software problems.

Kind regards

---

### Post by yoramdavid on 2011-12-17
> **matt_symes said:**
> Hi

First thing i would run - to eliminate them - are hardware tests. 

Test your memory (leave it running overnight) and your hard drive for bad sectors. Check the SMART status of the drive if you have it. 

If this is a laptop has that manufacturer tests then run them (Dell have done this).

Test all cabling and ensure everything is seated correctly. Test the power supply and voltages.

When you have done that then look for software problems.

Kind regards

Thank you matt_symer,

Smart status is on and there were no errors found on a check for bad sectors I did.
I will do the memory test tonight.
It is an HP laptop, I will check if they have diagnostic tools for linux.
I have an adaptor made for HP, therefore I do not think the problem is there.

It always happens when I install or uninstall an application.

Kind regards too :)

---

### Post by matt_symes on 2011-12-17
Hi

> **yoramdavid said:**
> Thank you matt_symer,

Smart status is on and there were no errors found on a check for bad sectors I did.
I will do the memory test tonight.
It is an HP laptop, I will check if they have diagnostic tools for linux.
I have an adaptor made for HP, therefore I do not think the problem is there.

It always happens when I install or uninstall an application.

Kind regards too :)

Post back the results of the memory test. 

It's not a fool proof way of testing memory but it may give more confidence that the issue is software. Then we can attempt to track down the problem.

Kind regards

---

### Post by yoramdavid on 2011-12-17
> **matt_symes said:**
> Hi



Post back the results of the memory test. 

It's not a fool proof way of testing memory but it may give more confidence that the issue is software. Then we can attempt to track down the problem.

Kind regards

Hi,

I will post.
I have downloaded a diagnostic file for HP computers but it is an .rpm and I cannot install it. Alien did not work, says it cannot convert it on this system.

Thank you and kind regards,

Yoram

---

### Post by yoramdavid on 2011-12-17
hello,

I ran Mametest86 v4.20, it is an option on the BURG boot menu I have.
It ran all night (about 10 hours), this morning it was still running, it was on test 10, then a while later it was on test 4, was it looping or is it another set of tests?
Anyway, I closed the lid to take the laptop downstairs and it was turned off when I opened it. Wonder why, overheated?
Luckily I had taken a photograph of the results so far. There are errors, please see the picture attached.

[IMG][[IMG]http://img263.imageshack.us/img263/623/mametest.jpg[/IMG]](http://imageshack.us/photo/my-images/263/mametest.jpg/)[/IMG]

---

### Post by matt_symes on 2011-12-18
Hi

It looks like you may have failing memory there and that could be the cause of your crashes and program instability.

It may be time to get a new memory stick.

You may have other problems as well but your memory looks like it's failing. You could doulbe check by making sure it's seated correctly, check for dust and run the texts again.

I would wait for someone else to chime in with an opinion first but that is what is would be considering; replacing your memory stick.

Kind regards

---

### Post by yoramdavid on 2011-12-18
> **matt_symes said:**
> Hi

It looks like you may have failing memory there and that could be the cause of your crashes and program instability.

It may be time to get a new memory stick.

You may have other problems as well but your memory looks like it's failing. You could doulbe check by making sure it's seated correctly, check for dust and run the texts again.

I would wait for someone else to chime in with an opinion first but that is what is would be considering; replacing your memory stick.

Kind regards

Thank you matt_symes,

So, that could be the cause of instability.
It is a laptop and I am not comfortable opening it, so I will wait until I get home to have that sorted out.

Yoram

---

