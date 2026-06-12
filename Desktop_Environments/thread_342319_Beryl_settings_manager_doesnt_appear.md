---
title: "Beryl settings manager doesnt appear"
date: 2007-01-19
forum: Desktop Environments
---

### Post by Rollotamasi on 2007-01-19
I recently installed the beryl desktop manager which I only got working because of some great guides written but you folks.  After getting the desktop running though I cant seem to access the settings manager.  The icon shows up up in the corner, and I can select it and get the drop down menu, however when i click on settings manager nothing happens.  All the other option like select window manager work just settings manager does load.  Any advice?

Thanks all!

---

### Post by Paerez on 2007-01-19
maybe its not installed?
run:
```
sudo aptitude install beryl-manager
```

---

### Post by Rollotamasi on 2007-01-19
> **Paerez said:**
> maybe its not installed?
run:
```
sudo aptitude install beryl-manager
```

I ran that command and the out was

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jacob@TheBeast:~$ 

Doesnt look like it not being installed is the issue

---

### Post by Paerez on 2007-01-19
did you install "emerald" and "emerald-themes" packages?

---

### Post by oobuntoo on 2007-01-19
> **Rollotamasi said:**
> I recently installed the beryl desktop manager which I only got working because of some great guides written but you folks.  After getting the desktop running though I cant seem to access the settings manager.  The icon shows up up in the corner, and I can select it and get the drop down menu, however when i click on settings manager nothing happens.  All the other option like select window manager work just settings manager does load.  Any advice?

Thanks all!

Due to recent updates, you now need beryl-binding package and python librabry packages. I don't know what they are called exactly, but you can search for them with synaptic.

You can run beryl-setting from command line to see what else you may need.

---

### Post by mac.ryan on 2007-01-27
I have the same problem and couldn't work it around yet.
The only thing I can think of is that the fact I have an ATI (ie: no composite option) might affect the program... ?

---

### Post by ComplexNumber on 2007-01-27
> **Rollotamasi said:**
> I recently installed the beryl desktop manager which I only got working because of some great guides written but you folks.  After getting the desktop running though I cant seem to access the settings manager.  The icon shows up up in the corner, and I can select it and get the drop down menu, however when i click on settings manager nothing happens.  All the other option like select window manager work just settings manager does load.  Any advice?

Thanks all!
install ALL beryl-settings components. ie beryl-settings, beryl-settings-bindings, etc.

---

### Post by eatmuchpie on 2007-01-27
There's a bug filed for this: [http://bugs.beryl-project.org/ticket/815](http://bugs.beryl-project.org/ticket/815)

As a work around, try typing the following at the  command line:

python2.5 /usr/bin/beryl-settings

Hope that helps :)

---

### Post by mac.ryan on 2007-01-27
> **eatmuchpie said:**
> As a work around, try typing the following at the  command line:

python2.5 /usr/bin/beryl-settings

Hope that helps :)

It helped to individuate the problem: apparently there is a problem with the locale settings (something that I also noticed with other softwares like for example VLC), when I try to command-line beryl setting I get:

> (beryl-settings:18414): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 13, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.5/locale.py", line 476, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


running a "locale" gets:

> locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME=en_GB
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=


I imagine the problem is with the LC_ALL set to "", but the problem is that this setting prevent me to run softwares like "localeconf" too. So, my only option - I suppose - is to change that setting manually, but I couldn't find out - neither after 20 mins of googleing - where is the file containing such setting.

Any help for this newbye? :)

[COLOR="Red"]**EDIT - 29 Jan**[/COLOR]
Looking for something totally different, I found where the file is myself: /etc/profile
thanks anyhow for the support

---

