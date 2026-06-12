---
title: "Top Bar Gone, can't bring up terminal (or anything else)"
date: 2013-06-12
forum: Desktop Environments
---

### Post by JohnBN on 2013-06-12
<Newbie asks:>
This old Dell is running ok, but somehow the top bar is gone, and CTRL-ALT-T isn't bringing up a terminal window.
I've moused everywhere, clicked on everything I can think of... nothing.  
All I can see is the desktop icons for Computer, Trash, Firefox, Solitaire (which at least makes this puppy do SOMETHING!:p), etcetera.  Can't even log out or shut down!
Noteworthy: if I minimize a window, it disappears... well, *I* don't know where it goes.

In short: **HELP**!

Don't know version - can't see it in anything 'cuz I can't get into anything.  Can't even get it to network 'cuz it doesn't know my WiFi!

---

### Post by VMC on 2013-06-12
Are you running Unity, Gnome? What Ubuntu version.

---

### Post by grahammechanical on 2013-06-13
So, we are going to have to guess. You do not give us a clue as to why this should suddenly happen? Did you do an update? Not knowing what version and assuming that it is later than Ubuntu 12.04 and again assuming that it is a video drvier issue. I suggest that you try right clicking the desktop and selecting Change Desktop Background. That will let you open System Settings and when you open Software & Updates and go to the Additional Drivers tab you can experiment with different video drivers.

Pressing Ctrl+Alt+F2 might bring you to a command line. Log in and run

```
sudo shutdown -r now
```

that will reboot

```
sudo shutdown -h now
```

will shut down and switch off the computer.

Regards.

---

### Post by JohnBN on 2013-06-14
Thanks for the replies!
Version = I don't know, can't get into anything to tell, but it was installed in late 2011.
As for incident specifics - also don't know, it was in someone else's posession (I put it together for an overseas friend's elderly mother so they could keep up via email & chat).
Anything could have happened.
Compounding issues:
It won't boot from USB.
It doesn't have an optical or floppy drive.
I know precious little about using Ubuntu - but I'm sure going to learn more soon!
  I like what I know so far!

The mouse pointer adheres to the screen limits, the icons on the desktop look and act normally, it's getting into settings that's baffled me.  I suppose I could update it if I could get into a command line - and with some help from those here who know.

John

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]JohnBN; Hi !

A quickie response from me.
Do you know the original "username" and password to gain administrative access to the operating system ?
What means exactly are you employing to get to the desk top ?
What results - when at the desk top - of the key combo ctl+alt+f1 ?

In order to provide you better assistance you will have to have access to a command line terminal. Then we can provide you the commands to provide to us the needed info.
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by JohnBN on 2013-06-15
Thanks guys!

Sigh... just spent 1/2 hour entering process, errors, what did what when... and I see it's not here!

Got into terminal, did shutdown-restart, same.  Got networking, internet, firefox running now, so hopefully errors will be forthcoming.

First error says I don't have required hardware for Unity - choose Ubuntu classic at login... not getting a login screen, that's the first thing I see after powerup.

Brief message about power management not working in upper right, then the Gconf error I will try to paste in here.
Firefox opens, gives error that is basically a repeat of the one I'm going to try to past in this thread.

Looks like there was a failed update that flushed the video driver.
It was all there at one point - it's a Dell Latitude C400 and was purring like a kitten until it gagged a few months ago!
Will happily do what is needed to put this back in service - Mrs. B. used it to keep in touch with her overseas son, my friend.
Besides, I'm not stupid, I just don't know any Ubuntu!  Last Unix was early 90s too.  I do however have 25+ years of being an electronics engineering technologist and have been an MCSE for a while too... I can do this with a little help!  :D

John

---

### Post by JohnBN on 2013-06-15
Here's the error:

GConf error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: GetIOR failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus))

<BTW: I'm actually using the C400 to enter this, so there is hope!>

What's next?

---

### Post by Bashing-om on 2013-06-16
John, Hi ! and good evening;

Lets start by cleaning things up and looking at what you have for graphics.
Terminal codes: (curticy of oldfred)
```
#housecleansudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
#All that does is update it again.
##and now the graphics stuff,
##Post back to us the outputs of:
sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
[INDENT=2]for starters, then we will see what is

[/INDENT]

---

### Post by JohnBN on 2013-06-19
As requested, answers to above.  As a programmer, I assume at least some of this is meaningful... or you're just having a laugh at my expense, in which case, you owe me a beer and I'm good with it.  ;)


sudo apt-get autoremove
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."
<So I did.  Lots of stuff happened, which I don't know how to C&P into here, but you probably know anyway.>

sudo apt-get autoremove
<Lots of stuff happened, which I don't know how to C&P into here, but you probably know anyway.>
<It asked if I wanted to continue, yes seemed appropriate at the time.  No apparent errors.>

sudo apt-get clean
<No responses.>

sudo apt-get update #resync package index
<Lots of stuff happened, which I don't know how to C&P into here, but you probably know anyway.>
<Lots of "W: Failed to fetch [http://.](http://.).. 404 Not Found [IP: 91.189.92.xxx]">
"E: Some index files failed to download. They have been ignored, or old ones used instead."

sudo apt-get upgrade #newest versions of all packages, update must be run first
<Lots of stuff happened,and I "yes"ed a couple of times.  A bunch of stuff "failed to fetch..." again.>
"E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing."

sudo apt-get update
<Did what it did last time.>

sudo apt-get --fix-missing
<I obviously don't understand that one, 'cuz I got the "help" for apt-get.  I assume --fix-missing is supposed to be non-literal.  Duh.>

sudo apt-get dist-upgrade
<Lots of stuff happened,and I "yes"ed a couple of times.  A bunch of stuff "failed to fetch..." again.>
"E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing."
<Sigh.  Shake head.  Move on.>

sudo apt-get -f install
"0 upgraded, 0 newly installed, 0 to remove and 107 not upgraded."

sudo dpkg --configure -a
<No responses.>

##and now the graphics stuff,
##Post back to us the outputs of:

sudo lshw -C display
<This is where I'd love to be able to C&P!>
*-display:0
description: VGA compatible controller
Product: 82830 CGC [Chipset Graphic Controller]
vendor: Intel
physical id: 2
bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
version: 04
width: 32bits
clock: 33MHz
capabilities: pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:11 memory:e0000000-e7ffffff memory:f4f80000-f4ffffff
*-display1 UNCLAIMED
description: display controller
Product: 82830 CGC [Chipset Graphic Controller]
vendor: Intel
physical id: 2.1
bus info: [EMAIL="pci@0000:00:02.1"]pci@0000:00:02.1[/EMAIL]
version: 00
width: 32bits
clock: 33MHz
capabilities: pm bus_master cap_list 
configuration: latency=0 maxlatency=11
resources: memory:d8000000-dfffffff memory:f4f00000-f4f7ffff

lspci -nnk | grep -iA3 vga
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset host bridge [8086:3575] (rev 04)
 Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphic Controller] [8086:3577] (rev 04)
 Subsystem: Dell Device [1028:00c8]
 Kernel driver in use: i915
 Kernel Modules: intelfb, i915


What's next?

---

### Post by JohnBN on 2013-06-19
Ya know, if it's easier to somehow re-image this thing, I'm all ears... bearing in mind it doesn't have any drives and won't boot from USB.  The only thing on it to be salvaged are the bookmarks in Firefox.

The upgrade process was suggested after a restart... it says it may take several hours... I'm going to drink... 11.04 sounds like a good number to raise a glass to.

Hopefully it won't explode in the process.

Cheers!

---

### Post by Bashing-om on 2013-06-19
[COLOR=#000000]JohnBN; Hi !

Ok, making lots of headway. But, at this point let's pause and look at what we are working with... all those errors point to the reactions of the software repository... Maybe like you are running an old version and those repositories the system's package manager is trying to access are no longer in existence !
It is not good to operate with a out of support version ... no longer supported, means just that ..no support. So to keep from beating a dead horse, let's see what we are working with. From the terminal copy and post the output of terminal codes:
```
lsb_release -a
uname -a
```pasting that output between code tags ("#",at the top of the post).
[/COLOR][INDENT=2][COLOR=#000000]
a tale in the telling
 [/COLOR][/INDENT]

---

### Post by SuperFreak on 2013-06-20
> **JohnBN said:**
> Ya know, if it's easier to somehow re-image this thing, I'm all ears... bearing in mind it doesn't have any drives and won't boot from USB.  The only thing on it to be salvaged are the bookmarks in Firefox.

The upgrade process was suggested after a restart... it says it may take several hours... I'm going to drink... 11.04 sounds like a good number to raise a glass to.

Hopefully it won't explode in the process.

Cheers!


You would do better with 12.04. It is a Long Term release and supported till 2017. I am not sure if 11.04 is still supported
A fresh install rather than upgrade will likely be less troublesome

---

### Post by JohnBN on 2013-06-26
Sorry for the late reply - you guys are awesome for helping this old goat out, but the daughter's wedding preparations take priority!  :D

And I quote:
{lsb_release -a}
No LSB modules arer available.
Distributor ID: Ubuntu
Description: Ubuntu 11.04  <That answers THAT question!>
Release: 11.04  <Re-runs already?>
Codename: natty

{uname -a}
Linux Sally-Dell-Latitude 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i386 GNU/Linux
<And that answers some other questions.>

Yup... now thinkin' full-blown update to latest release is the way to go.
Mentioned before: this thing has no external media boot capability.  Won't boot from USB, doesn't have removable media drive.  
Whatever gots to be done, gots to be did by network or remove HDD and attach to another box.

What's next?

---

### Post by SuperFreak on 2013-06-26
Hopefully someone will help with this as it is beyond me, how to do a full install without media or USB drives. I do believe though that temporarily installing your hard drive in a computer with USB boot connection or a CD/DVD burner is likely how you should do it. You will likely have to edit FSTAB also.
Good Luck and I hope someone posts help for you

---

### Post by kurt18947 on 2013-06-26
Putting the hard drive in another machine should work, I've done it.  If you're not feeling confident, you could disconnect every hard drive except the one you're installing to.  That way you'll not have any 'oopses' on a working machine.  Just do a minimal install, enough to get it to boot.  Then reinstall in the intended machine, get networking functioning, run updates etc. etc.  At least that's what I did.

---

