---
title: "X Error: BadDevice, invalid or uninitialized input device 168"
date: 2006-07-09
forum: Desktop Environments
---

### Post by sup on 2006-07-09
sometimes, when I start applications from terminal (opera, for example), I got this:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
it does not seem to cause any troubles, but I wonder, what it means, any ideas? I tried to google it but without much succes

---

### Post by Jun-Dai on 2006-07-15
Me too.

I just got it loading kcmshell fonts.  :-(

---

### Post by Jun-Dai on 2006-07-16
I figured out on some other threads that this is most likely due to some "wacom" devices in your xorg.conf.  Be sure to comment them out in your xorg.conf (there were three such devices in mine).  Also be sure to comment out the references to them in the ServerLayout section (one reference to each), otherwise X won't start up again.  Here are the sections commented out:
```

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
```
. . . and much farther down:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

```

---

### Post by sup on 2006-07-17
I see that did the trick, thanks:-).

---

### Post by robins_web on 2006-07-25
Thanks! I was having the same problem, and this fixed it. Much obliged!

---

### Post by Lord Illidan on 2006-07-27
Regarding the wacom thing, any reason why they are enabled by default in Xorg.conf?
These errors confused the hell out of me, I wonder what they would have done to a new user.
Surely it isn't too much to ask to confirm during installation if the user has any wacom tablets or what not?

---

### Post by rand0m3r on 2006-07-28
Sorry i'm new to kubuntu and need some help.

i used kate /etc/X11/xorg.conf to open the file and make the changes. however, it won't let me save, something about write privileges i think.

i type su to login as root, and to my surprise i don't even have the password to root. i thought that the default login i make was the root. 
what do i do now? i still have this problem, and its stopping me from using automatix and other programs.

---

### Post by sup on 2006-07-28
You need to use sudo, i.e. sudo kate /etc/X11/xorg.conf, it will prompt you for YOUR (not root's) password and then it will be possible to save it.
If you want to make graphical launcher, use gksudo, if you want to havbe root's terminal, type sudo su (Et least I think it is this command)... there is a way to enable root's account (su passwd maybe, i do not remember, search wiki for root account or something and you should find your way, this is very common question to newbies), but it is not recommended - and I think it is right since sudo works so nicely.

---

### Post by rand0m3r on 2006-07-28
this is a bit weird.

i thought sudo was just su but only applied for a single command. hence the password for sudo and su should be the same. anyway i did sudo kate /etc/X11/xorg.conf and made those changes. the error msgs still pop-up, but everything seems to work now.

---

### Post by rjz35 on 2006-07-29
Make sence to disable the Tablet things in the conf file. didn't think of that before.

any it helped me thnx alot.

---

### Post by ButteBlues on 2006-07-30
I get the same thing but for 166. I disabled wacom, but still get it. Which one is 166?

---

### Post by dinub1 on 2006-08-16
Thank you for your tip. I edited my xorg.conf file in order to comment the lines per your tip, related to a Wacom device. Upon saving the conf file, error stopped appearing.
I got this following last update via Adept. Must be a bug in the programming. I do not have a Wacom scanner/plotter whatever that is installed. I beleive this is an error introduced perhaps when Xorg components were updated automatically.
The error always appeared whenever via terminal I tried to edit a file, like etc/resources.list. It gave me that error usually twice then it would enter the edit mode successfully. I never had this before. Thanks again.

---

### Post by jetpeach on 2006-08-25
What is wacom?  I'd like to remove these lines as well, but don't want to if it's going to break other things.  I searched the web but couldn't find a simple explanation.
And does anybody know if this is fixed in edgy?  It's quite annoying to have so many errors in the default install...

---

### Post by Flyingrunner on 2006-08-30
I had the same troubles with the error message. I'd get it when I'd run Automatix. The error that comes up is:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I edited the xorg.conf file and commented out the wacom, but I still get the error message when I run Automatix. Any ideas? Thanks.

[I restarted my machine and it fixed it. Thanks for the help whoever it was that posted the guide on how to get out the wacom]

---

### Post by lucien_nicholson on 2006-09-06
It seems when I run Firefox 1.5 it won't open and I get this message:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

The numbers are a bit different, but essentially the problem seems to be the same.  However, I can't open Kate using sudo, I can only open the xconfig file as myself, not as root.  That is, when I run sudo kate /etc/X11/xorg.conf, Kate freezes and I can't fix the problem that's causing all this and incidentally, I get the same message along with this one below it:

Failed to open device
ScimInputContextPlugin()
WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified
~ScimInputContextPlugin()


  I can only open Kate not as root, thus I can't save changes.  Is there a way I can fix this problem?  Or get root priveleges after I open kate as myself?

Thank you for your help.

---

### Post by sup on 2006-09-06
what about sudo vi /etc/X11/xorg.conf or change nano for vi if you prefer. (to write in vi, press i, to leave it, press escape and q! or wq - former will not save changes to the file whereas the other will)

---

### Post by lucien_nicholson on 2006-09-07
Sup, diky za to.  Ja to zkusim, ale ja Ubuntu jeste dobre nezam.  I'm glad to see a Czech here.  I used to live in Lipnik nad Becvou.  Like I said, I'll give it a try and thanks for your help. Uvidime jak to pujde.

---

### Post by sup on 2006-09-07
:-), there is quite a few of us here I think. There is also a czech forum here: [http://forum.ubuntu.cz/index.php]("http://forum.ubuntu.cz/index.php") with some helpful people but obviousle there are many more here then there.

Other option would be to log in as root and edit xorg.conf then ([https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c](https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c))

---

### Post by palsyboy on 2006-09-09
I can't speak for anyone else, but I think I might be able to help lucien:

In my experience, you get errors such as that when you're trying to run an application as root.  The X server doesn't always play nicely with running some graphical stuff as root within another user's profile.  Both of these errors seem to come from that problem.  But I think it might be a good idea to try the Xorg commenting first.

The reason you can't open kate as root is that it's a graphical text editor, and being graphical, it's doesn't want to run as root.  I always use nano to edit config files.  And whenever you use nano, remember to use the -w option to account for wrapping.  If you make lines wrap, then you can corrupt the formatting of t a config file.

Anyway, go ahead and run
```
$ sudo nano -w /etc/X11/xorg.conf
```
and it should work with no problem.  And in nano, you have to hit Ctrl+X to save, and then confirm with a Y.

After you're finished editing xorg.conf, you'll need to restart the X server for changes to take effect.  You can do this by either logging out of KDE or else hitting Ctrl+Alt+Backspace.

---

### Post by jetpeach on 2006-11-20
A launchpad bug for this is here
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/42553](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/42553)
it has 8 duplicates but is still unconfirmed.  hopefully it will be confirmed soon and fixed.  if this wacom stuff is just for tabletPCs, it should simply be removed, this error causing havoc and confusion for so many

---

### Post by datakid on 2007-01-27
Thanks for the simple fix! Helps :)

---

### Post by mirceade on 2007-03-30
I think this should go down as a bug for the Feisty Installer. Or is it already?

---

### Post by frm on 2007-04-08
I did have the same problem. Many thanks for this post!

---

### Post by frm on 2007-04-08
seems to be already filed: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42553](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42553)

---

### Post by ingie on 2007-04-21
this is off topic, but since it was asked in context

> **rand0m3r said:**
> this is a bit weird.

i thought sudo was just su but only applied for a single command. hence the password for sudo and su should be the same. anyway i did sudo kate /etc/X11/xorg.conf and made those changes. the error msgs still pop-up, but everything seems to work now.

hi rand0m3r,

the reason is that sudo is designed to allow admins to enable root privileges to a user without needing to give the root password to that user... so this is why sudo, [and the equivalent X tools in ubuntu]   ask for the user's password

the file /etc/sudoers defines which users are allowed this privilege and it is possible to restrict the root powers to certain things... [ i wont go into that here, since it is off topic.. but suffice to say, you wouldn't for example allow sudoers to use passwd on an open server... as they could then lock out root]

this method [ using sudo in preference to su ] is "pushed" by ubuntu - and good on them i say, took me a bit to adjust, but the value is in making a more secure system straight from the box...

hope that clarifies...

'ingie

---

### Post by vando on 2007-04-22
After commented those lines, I am still getting the errors when I gvim a file.  Here's my version of the error:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: not found

Any help would be much appreciated.  I did also restarted X by logout and login again, but the errors are still there.

Thanks.

---

### Post by Syock on 2007-06-29
> **jetpeach said:**
>  if this wacom stuff is just for tabletPCs, it should simply be removed, this error causing havoc and confusion for so many

Just what kind of havoc did it cause? Disabling it would then cause havoc for those with slate TabletPCs don't you think?

EDIT : Okay, I realized that certain installation scripts won't continue when meeting with X error.
Maybe TabletPC should be added as an option in the Gutsy suggestion "What computer type are you installing on?", but that's another story.

EDIT2: I'm saying this because I'll be getting a new TabletPC tomorrow. Yay!! But it has a keyboard to work with, not having stylus by default wouldn't hurt as long as i get to edit xorg.conf

---

### Post by aethernaut on 2007-07-13
I found this thread via Googling an error and since the last post was just a few weeks ago I'll go ahead and bump it by adding my own bit of oddness:

I downloaded [**[COLOR="Blue"]Stani's Python Editer[/COLOR]** ]("http://pythonide.blogspot.com/") from svn and ran it from the commandline: ```
python SPE.py
```

Which gave me the famous error:

```
Launching application...
X Error: BadDevice, invalid or uninitialized input device 169
    Major opcode: 145
    Minor opcode: 3
    Resource ID:  0X0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
    Major opcode: 145
    Minor opcode: 3
    Resource ID:  0X0
Failed to open device
```

Yes: it printed the same error out twice...dunno if that  means that it tried it twice and gave up or what?

Now what makes this *extra wacky* is that the program in question DID launch and, in fact, seems to work just fine (I've saved and reopened .py and .txt files and played around with the interface and haven't seen anything amiss with the IDE itself yet).

As with most of the others posting before me: I do not have a Wacom (nor anything else other than a standard mouse and keyboard) on this system and I can't imagine why it's throwing an error related to such a device in the terminal window on launch?

I'm running Kubuntu Fiesty with python 2.5 and was thinking that it was wxPython related until I tripped over this thread.

:-k

This is more a curiosity than an issue for me (it's just a weird error message); but I figure adding it here can't hurt and maybe it'll add another clue for the people who do the bug-squashing : )

---

### Post by mistrynitesh on 2007-08-29
I get similar errors few times, but he input device is 169, major opcode is 145 and minor opcode is 4. Will the above suggestion work for me?

---

### Post by gigabz666 on 2007-08-29
> **aethernaut said:**
> I found this thread via Googling an error and since the last post was just a few weeks ago I'll go ahead and bump it by adding my own bit of oddness:

I downloaded [**[COLOR="Blue"]Stani's Python Editer[/COLOR]** ]("http://pythonide.blogspot.com/") from svn and ran it from the commandline: ```
python SPE.py
```

Which gave me the famous error:

```
Launching application...
X Error: BadDevice, invalid or uninitialized input device 169
    Major opcode: 145
    Minor opcode: 3
    Resource ID:  0X0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
    Major opcode: 145
    Minor opcode: 3
    Resource ID:  0X0
Failed to open device
```

Yes: it printed the same error out twice...dunno if that  means that it tried it twice and gave up or what?

Now what makes this *extra wacky* is that the program in question DID launch and, in fact, seems to work just fine (I've saved and reopened .py and .txt files and played around with the interface and haven't seen anything amiss with the IDE itself yet).

As with most of the others posting before me: I do not have a Wacom (nor anything else other than a standard mouse and keyboard) on this system and I can't imagine why it's throwing an error related to such a device in the terminal window on launch?

I'm running Kubuntu Fiesty with python 2.5 and was thinking that it was wxPython related until I tripped over this thread.

:-k

This is more a curiosity than an issue for me (it's just a weird error message); but I figure adding it here can't hurt and maybe it'll add another clue for the people who do the bug-squashing : )

I had exactly the same thing. Programs run perfectly fine but that error comes up three times before it opens. Turns out that in my xorg.conf file there were three references to devices using wacom. Followed the third post in this topic and no more errors. Just seems to be a strange little bug which automatically sets up tablet devices.

---

### Post by g.a. on 2007-10-23
I had the same error and commented the wacom-devices as suggested. however, Xserver  did not show up and I had to un-comment again those lines entering in line mode and using vi.

any reason for that?

thanks

---

### Post by tuesday20102001 on 2007-12-20
I forgot all about this trick. I use to experience these type of errors when starting firefox-1.06 from the command line. I recently check my .xsession-errors (log file) on a recently upgraded laptop, and I find these errors. I do not use the wacom devices so this fix worked for me, thanks allot.

---

