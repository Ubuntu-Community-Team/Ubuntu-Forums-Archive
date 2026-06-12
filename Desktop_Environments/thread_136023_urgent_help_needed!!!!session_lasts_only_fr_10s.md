---
title: "urgent help needed!!!!session lasts only fr 10s"
date: 2006-02-25
forum: Desktop Environments
---

### Post by krait on 2006-02-25
hi,

i hv not been able to use comp. i log in and it says "session only lasted for 10 seconds" and brings me bak to the login screen. the same is the case even if i try Failsafe gnome. I am only able to use the failsafe terminal.

i had installed Kommander before i shut down, if it is of any relevance. this is the xsession-errors file i got:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bharath"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:9226): Gdk-WARNING **: locale not supported by Xlib

(gnome-session:9226): Gdk-WARNING **: cannot set locale modifiers
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/sparta:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/sparta:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/sparta:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9226): WARNING **: Unable to read ICE authority file: /home/bharath/.ICEauthority

--------------------------------------------------------

i run only ubuntu on my machine and would really appreciate help to get this sorted immediately.

thanks a ton in advance.

---

### Post by scifi on 2006-02-25
Is your hardware ok? 
Please run some hardware tests like memtest and a harddrive test (e.g. from ubcd: ultimatebootcd.com)

Tried reinstalling?

---

### Post by krait on 2006-02-25
my hardware i m sure is fine. it has been workin well for so many days and i havent changed anythin. reinstalling will cost me a lot of time which i cant afford at the moment. is there no other way to sort this out? this problem has come somewhere out of the blue, its cra z.

im a relative newbie and am really hoping some of the more advanced users can help me get this sorted in a jiffy.

thanks

---

### Post by krait on 2006-02-25
someone????anyone?????please.......

HELP.....

---

### Post by Madpilot on 2006-02-25
While Ubuntu is booting, watch for the "Grub" screen. Hit ESCAPE when you see the short Grub countdown.

This will bring you to the Grub menu - use up arrow/down arrow to get to the Recovery Console option, and hit Enter

You'll be presented with a command line prompt. Type "rm /home/bharath/.ICEauthority" with no quotes around it, then "shutdown -r now". This will restart your computer.

Let it run, and it should restart normally. Post here if it doesn't.

EDIT TO ADD: This will solve your problem if the .ICEauthority problem is your only issue. If it's more complex, it won't, but it won't hurt. Keep us posted.

---

### Post by abowman on 2006-02-25
I did a new install last night and used easyubuntu.  Everything seemed to work great, but this morning I tried to login and discovered the same problem that Krait had.
I'll try the solution that MadPilot suggested.

---

### Post by abowman on 2006-02-25
It worked.  Thanks

---

### Post by John Jason Jordan on 2006-02-25
This problem happens all the time and is a constantly repeated question. The source of the problem is running certain KDE apps. The system works fine until you log out. Then you get the "your session lasted for less than 10 seconds ..." error message when you try to log in again. The solution is super simple, but baffling to someone who is new to Linux.

What happens is that, for some reason, running certain KDE apps goobers up a hidden file in your home folder. The file is .ICEauthority. (Note the dot in front, which is what makes it hidden in Nautilus or whatever you use for a file manager; also remember that Linux files are case-sensitive.) Whenever you log in, the system automatically makes a new copy of .ICEauthority, so you can just delete or rename it. Here's how you do it:

1) Type Ctrl-Alt-F1. This will take you to a command line. The shell with the login prompt is still running and we'll go back to it in a minute.
2) The prompt should say "<ComputerName> Login:." So just type your username and your password when it prompts you for it. Then the prompt will say "<Your UserName>@<ComputerName>:~:" This means that you are in your home folder.
3) Now just type "sudo mv .ICEauthority foo." This will prompt you for your root password and then rename the ".ICEauthority" file to "foo." (The .ICEauthority file requires root permission to change, so you have to use sudo.) After you log in successfully you can use Nautilus or your file manager to delete "foo." The reason for renaming it instead of deleting it is for "just in case JJJ's instructions were wrong and it turns out I really need this file." Always better to rename first, and delete later.
4) Finally, type Ctrl-Alt-F7, which will take you back to the shell with the login prompt. Proceed to log in as usual. For me it always works. Don't forget to go back and delete "foo."

And I hope someone has reported this bug. I love the Gnome shell but, like most Gnome users, I need certain KDE apps as well. Not all of them cause this problem, but several do. 

And a final tip: Once you're back in, open Gedit (Accessories > Text Editor), copy the above instructions, paste them into Gedit, and save the file as "hacks_and_screwups" or whatever you want to call it, and then make a printout of it. Add other instructions to this file as you go along and reprint each time. Keep the paper copy with your computer so you have a reference that you can access when you can't log in or something else goes haywire.

---

### Post by lakelovers on 2006-02-25
I had this problem a short while back. I Googled "ICEauthority" which lead me back to the Ubuntu forum. The first answer for the problem said to use this command:

sudo chown (your login name) /home/(your log-in name)/.ICEauthority

Don't forget the "." before ICEauthority.

So, I did the command and everything has been hunky dory since. 

Of course, you problem may be more involved. I'm a know-nothing Ubuntu user so I can't vouch as a problem solver.

---

