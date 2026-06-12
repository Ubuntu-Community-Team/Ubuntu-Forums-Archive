---
title: "[SOLVED] Ubuntu - no desktop or gnome..."
date: 2008-12-18
forum: General Help
---

### Post by Tom_T on 2008-12-18
Just installed 8.10 onto an IBM netVista 8309-22g.

Installation went well and I get presented with the GUI login screen.

Once I log in all I get is a pale brown screen and my mouse pointer !!  No toolbars or icons !!  The keyboard doesn't appear the work (scroll or num lock not working)

I've tried rebooting an running xfix, makes no difference.

Any ideas ??

Thanks

---

### Post by Tom_T on 2008-12-18
I can get into a terminal if that helps !!

---

### Post by kanikilu on 2008-12-18
Sounds like it might be a problem with X to me. Are there any warnings or errors in your logs (/var/log/Xorg.0.log)?

---

### Post by Tom_T on 2008-12-18
Thanks for the reply.

I did an upgrade from the terminal, rebooted and now it's sorted :)

Thanks

---

### Post by berkshire779 on 2008-12-18
I have the same problem with Ubuntu 8.10 after loading it on a Compaq EVO D15S.  I found an error file listed below:

cat .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for local=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /eetc/X11/xinit/xinput.d/default.
gnome-session[5007]:WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanger'
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1152x864) to maximum 3D testure size (2048): Passed
Checking for nVidia: not present.
Checking for FBConfig; present.
Checking for Xgl: not present.
gnome-session[5007]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout

I am assuming that the gnome virtual machine is what is missing from the installation CD.
You mentioned downloading an update from the internet via the terminal.  I am new to this OS and I am not familiar with all the commands yet, can you help by listing the commands needed to get the update and the web address where you got it?  Thanks for your time.

---

### Post by Tom_T on 2008-12-18
I'm new to this, so you will have to bear with me as well !!

When I booted up I got the normal GUI login screen, it was only when I logged into that that I got nothing.

I rebooted and at the login screen, I clicked on options and selected the one for terminal. When I logged in then I had a running terminal window.

In there I ran:
sudo apt-get update
sudo apt-get upgrade

Once that completed, I ran sudo reboot, when it came back up it worked fine !!

I was connected to the router when I did this, and the PC got it's network details from DHCP.

Hope that helps.

---

### Post by jenkinbr on 2008-12-18
@Tom_T - As your problem is solved, you should mark this thread as such.  To do so, at the top of the page is a menu titled 'thread tools'.  When clicked, you should see the option to 'mark thread as solved'.

Thanks.

---

### Post by Tom_T on 2008-12-18
Thanks :)

---

### Post by tomthumb99 on 2009-01-25
This did not work for me, screwed up my system even more. I now have another few hours putting the system back.  The simple answers should be avoided. I have learn that in the past few months, that the ubuntu apt-get upgrade command installs all types of software not needed (upgrade was clean, video drives a mess now).  Initial problem still present in syslog.

Does anybody have an ans to the orginal problem that will just will focus on the exact problem:

gnome-session[5007]:WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanger'

I read a thread that it might be related to the Nivdia 177 video driver?  But this message sounds more core to the gnome software.  

I also get 'pluseaudio' erros and module-x11-xsmp.c erros, also adding to my x win problems.  The upgrade did not fix that either...

---

### Post by kooijman on 2009-01-29
I just set up the ubuntu-desktop version as a windows application from the CD and ran into similar problems: after logging in with my username and pw I get a blank yellow screen. Couldn't get out at all, not even with ctrl-alt-del, so I cut the power. To cut a long story short, I eventually got to inspect the files in a recovered system as "root" and found the problem mentioned above in the .xsession-errors file in the home directory of my "user" (this is a hidden file). I think I found the solution for the problem of "gnome-wm not being present" on the internet in a different forum [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/316958](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/316958) It says there that at startup gnome looks for gnome-wm.desktop in /usr/share/applications but in my distribution it was *not*there. It was, however, present in /usr/share/gnome/autostart. So I followed the advice and copied gnome-wm.desktop in the first mentioned directory. This took care of the first error message (missing gnome-wm) in .xsession-errors. (Incidentally, this problem was supposed to be solved in the current ubuntu distribution of Oct. 2008).
But now I am still stuck with the last-mentioned error message:
"x-session-manager[4881]:WARNING: Application 'gnome-wm.desktop' failed to register before timeout".
Further rooting around on the internet gives me the impression that this may have something to do with "compiz" cutting in too early, because x-session takes too long doing chores. The next to last message in the error file is "Checking for Xgl: not present". This is the second time this message occurs in the file, and I think it is not fatal in itself. Just takes too long. Would it help to replace compiz with metacity as default in .gconf and how do I go about that if I can't use gconf-editor (is not available at the root-prompt)?

---

### Post by kooijman on 2009-01-30
Eureka!
I just took Tom T's advice and my problem is solved. I now think it therefore has to be a problem with the CD that is sent out as distribution for rel. 8.10. I received my CD this week from Breda in the Netherlands (so it probably was mailed in mid-January, 2009). I suspect something was missing/wrong with this distribution on the CD, or the solution to the problem with Gnome (whatever it was) would not have worked.
To recap for other victims:
After you have gone through recovery, which is probably necessary if you didn't properly exit from the system in your extremity :-) (i.e. hit ESC during the countdown before ubuntu starts; this gives a menu with recovery mode as the second option; after recovery go for normal start-up, as it is not necessary to use the root-prompt as I did originally) don't login, but click "options" in the lower-left corner of the screen and select "failsafe terminal" (this leads you through a login sequence after all, but opens a terminal in the blank screen).
Then you have to update your distribution, i.e. first get an updated package list and then upgrade with this list. One has to do this as "root", but it is easiest to just use the "sudo" command (one is prompted for ones user password for the first use).
>sudo apt-get update
>sudo apt-get upgrade
in that order obviously. In my case 225MB of patches and such was downloaded, which took two hours and then among other things a new Gnome configuration was activated, but this only becomes operational after all x-sessions have ended, so type "exit" at the prompt (or "reboot", as this has to happen eventually anyway). 
I have not rebooted yet, as I first wanted to savor my new system :-) So I started up the included firefox browser to tell you about this feeling of joy.
Still, I have to end on a somber note. Not only am I cross about the substandard CD, but I also discovered a glaring security hole. As I wrote in my previous post, I yesterday used the "root"-prompt in the course of the recovery process. I was able to do this without any password!!! I intend to close this hole as soon as possible as root does not seem to be password protected. But that does not help other people, of course. So please beware, if you were not aware of this.

---

