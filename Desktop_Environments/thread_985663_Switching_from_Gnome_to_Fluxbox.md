---
title: "Switching from Gnome to Fluxbox"
date: 2008-11-17
forum: Desktop Environments
---

### Post by Robotman on 2008-11-17
I've got an HP 2133 mininote with Ubuntu 8.04 on it.  Gnome runs VERY slowly on that machine, so I'd like to replace it with Fluxbox, which I've gotten to know from Fluxbuntu.  I'd also like to replace Nautilus with Thunar.
Does anyone have any advice for me?  From what I gather I should just download the Fluxbox and Thunar packages via Synaptec, but I want some confirmation on this before I muck about in there. ;)
I'm also wondering if I need to change any configuration files after I install those packages.
Any advice from those who've done something similar is appreciated.

---

### Post by CJ Master on 2008-11-18
> **Robotman said:**
> I've got an HP 2133 mininote with Ubuntu 8.04 on it.  Gnome runs VERY slowly on that machine, so I'd like to replace it with Fluxbox, which I've gotten to know from Fluxbuntu.  I'd also like to replace Nautilus with Thunar.
Does anyone have any advice for me?  From what I gather I should just download the Fluxbox and Thunar packages via Synaptec, but I want some confirmation on this before I muck about in there. ;)
I'm also wondering if I need to change any configuration files after I install those packages.
Any advice from those who've done something similar is appreciated.

Downloading the fluxbox package will allow you to use fluxbox in ubuntu, from an option in your session menu.

However, downloading and installing fluxbuntu will add a ubuntu-derivative that installs programs recommended for fluxbox.

I would personally just sudo apt-get install fluxbox

---

### Post by unix-vocab_trainwreck on 2009-02-15
> **CJ Master said:**
> Downloading the fluxbox package will allow you to use fluxbox in ubuntu, from an option in your session menu.

However, downloading and installing fluxbuntu will add a ubuntu-derivative that installs programs recommended for fluxbox.

I would personally just sudo apt-get install fluxbox

Cj Master,If you use "sudo apt-get install fluxbox" does it remove gnome in the process? also, are there any consequences to removing gnome.(and to Robotman), exactly what is nautilus and do you have to learn any new commands if you replace that? .(Note, I'm nearly a complete greenhorn when it comes to linux/unix and terminal use:confused:. Just started 3 days ago:popcorn:)

thanks 
(i hope this isn't against forum etiquette or anything)

---

### Post by malspa on 2009-02-15
To unix-vocab_trainwreck:  **sudo apt-get install fluxbox** won't remove GNOME, but I don't think there's any reason not to just open up Synaptic, search for Fluxbox, and install it from there.  Last time I installed Fluxbox (in Debian Etch), I also installed feh, fluxconf, and fbpager, all of which are helpful to have (for me).  Nautilus is just the GNOME file manager and Thunar is the Xfce file manager and you can add Thunar without removing Nautilus.  I think using Fluxbox might force you to get comfortable with the command line a bit, and with Linux in general, so consider yourself warned. :cool:  For me, it sure helped me to understand how a lot of things are put together in other desktop environments and window managers.

To Robotman, I can't think of any configuration files that were there before that I've had to change.  But Fluxbox itself requires a bit of tweaking, of course, and you'll want to get your ~/.fluxbox/menu configured to your tastes.  Whenever I install Fluxbox, I don't remove any GNOME or KDE stuff that's already there on the system.  I've done several Fluxbox installations.  Once I'm logged into it, it always seems fast and crisp compared to GNOME or KDE.  I like to use a few KDE apps in combination with Fluxbox (mainly Konqueror and Amarok) but those are probably not important to you.

One habit I've gotten into, I keep copies of ~/.fluxbox/menu files that I've used in the past, so that when I do a new installation I copy and paste one in and then tweak it to fit the distro I'm using.  This seems to make installing and setting up Fluxbox go much faster for me.  I can share some of those with you if you'd like -- I found it helpful to see some examples of that file.  Or you can find some other examples elsewhere on the internet, of course.  Of course you'll have to make sure that in the ~/.fluxbox/init file the **session.menuFile:** line says ~/.fluxbox/menu.

The only other thing I'd add here:  I remember stumbling around quite a bit the first time I installed Fluxbox (it was in Mepis), and had to Google around a lot to find info about getting it set up.  If you keep good notes, it helps quite a bit when you go to install it again later.  At this point, for me it seems quick and easy to install and set up, but there are a few differences when it comes to installing it in different distros.

---

### Post by unix-vocab_trainwreck on 2009-02-15
Thanks for the heads up malspa, i usually end up trying these new unfamiliar things and end up in a fix. Though still, My original objective in starting with Ubuntu  was to learn more about linux/ Unix's non-graphic Ui. So since i eventually intend to switch to fluxbox, is there any clear cut way to improve (learn from the scratch) more efficient and confident command-line usage? I understand a few commands with sudo, but about 89% of the time, i mostly end up with invalid commands:). 

Thanks for your help once again.

---

### Post by malspa on 2009-02-15
> **unix-vocab_trainwreck said:**
> is there any clear cut way to improve (learn from the scratch) more efficient and confident command-line usage?

Hm.  I'd say that just because you WANT to learn, you're on the right track!  I want to tell you to keep checking out things in the forums and keep trying new things, get your hands dirty.  I remember at one point where it hit me that I'd become comfortable at the command line and I didn't really know how that had happened!  I'd definitely recommend getting used to looking at manpages.  Especially, take a good look at **man man**, the page that talks about manpages.  If you don't know, the "q" key will get you out and back to a command prompt.  Also, Google around about Linux BASH commands, that sort of thing.  I ended up bookmarking a handful of sites to refer to and also wrote up a list of BASH commands and some notes on usage.  I think those things helped me get a feel for things.  I still use the GUI most of the time but it's quite helpful to be able to go back and forth, especially because so many times when you ask a question at the forums, folks will reply with a command to run, even though lots of times there's an alternative GUI approach.  I think the main thing is practicing with some of the more basic commands.  I remember taking long looks at things like **man ls** and **man cal**, playing around with the **ls** and **cal** commands, getting a feel for things.  I know that might sound dumb but I had to start somewhere, I guess.

---

### Post by RedSquirrel on 2009-02-15
> **unix-vocab_trainwreck said:**
> If you use "sudo apt-get install fluxbox" does it remove gnome in the process?

GNOME will still be there. After you install Fluxbox, Fluxbox will be available in the **Sessions** list at the login screen. You can choose from there whether you want to use GNOME or Fluxbox.

You can even use GNOME applications when you are running Fluxbox. They will be available in the Fluxbox menu (just right-click on the desktop when you are running Fluxbox).

For learning about Fluxbox, see:

[http://fluxbox.org](http://fluxbox.org)
[http://fluxbox-wiki.org](http://fluxbox-wiki.org)



> **unix-vocab_trainwreck said:**
> So since i eventually intend to switch to fluxbox, is there any clear cut way to improve (learn from the scratch) more efficient and confident command-line usage?

The guides at [http://tldp.org](http://tldp.org) might help, for example:

[Introduction to Linux]("http://tldp.org/LDP/intro-linux/html/index.html")

You could also look at the sticky threads at the top of the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum.

---

### Post by unix-vocab_trainwreck on 2009-02-16
Thanks to all for your usefull links and instructions. Come to think of it, in the past few days, the command-line has gotten significantly less daunting.

Once again thanks :popcorn:

---

