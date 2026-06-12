---
title: "Need help badly! - login/x problem"
date: 2006-06-06
forum: Desktop Environments
---

### Post by i++ on 2006-06-06
i was playing half life with wine, when i changed the resolution in half life, from 640x480 to 800x600, and my computer suddenly crashed... i usually run my desktop at 1280x1024.

I restarted the machine, and logged in... i get a blank screen with the default brown background for a few seconds.. then it logs me out again :( 

if i log in with a failsafe terminal session then the terminal is in the bottom right corner, as if there's something wrong with x. any help with this would be a lifesaver as my computer is useless otherwise!!

heeeellllpp! :)

thanks, i++

---

### Post by i++ on 2006-06-06
p.s. if i load up recovery mode kernel, then login as root and startx, it works, but not sure what to do from there, and i know its a bit stupid to login as root, so i dont want to do things that way, even if i knew how, unless its as a last resort..

---

### Post by nkhansen on 2006-06-06
Sounds like a horrible problem. Is the login screen displaying correctly? If so, it could be a problem with your user account. This is still bad, but not so much.

At the terminal, you could try adding another user, ie:

```
$ sudo adduser test
```

Then try to log in with htis user. Maybe it could help you? If this works, it could be corrupted files in you home directory. Or wrong permissions.

To make sure that all the files in a user's homedir is owned by the user do this:
```
$ cd /home/user
$ sudo chown -R user:user *

```
Change 'user' to the correct username.

---

### Post by i++ on 2006-06-06
yeah the login screen displays fine, at 1280x1024 by the looks of it, same as its always been.

okay so i logged in as myself, into a failsafe terminal session.
added a new user called test, set the pw and etc..

exit the failsafe terminal... and login as test...

it works! it all logs in okay, and home dir all belongs to 'test'

can i use this to fix my usual user ?

---

### Post by i++ on 2006-06-06
or could i just migrate the settings and profile? is there a feature like that in dapper?

---

### Post by Ramses de Norre on 2006-06-06
To copy over the whole home dir without breaking links use this command:
```
cd /path/to/old/homedir
find . -depth -print0 | cpio --null --sparse -pvd /path/to/new/homedir
```
I can't think of another solution for now..

---

### Post by i++ on 2006-06-06
okay brilliant thanks, will do that for now!

what about permissions and stuff? i dont have as much/any access to things that i used to have in say the administration menu etc...

also, is there any error log or anything that i can look at / post here? i get no errors or anything on the screen, not even the splash that usually shows loading nautilus ...etc

---

### Post by Ramses de Norre on 2006-06-06
You can still log into your previous user in a tty no? So do that and then sudo vi /etc/group
and add the name of your new user to the admin group (more users are seperated by ",").
You should have sudo priviliges then.

EDIT: If you don't know vi: press i to go into insert mode, make your changes, press esc, shift+q, wq! enter.

---

### Post by mlind on 2006-06-06
You can revert gconf settings to default using gconftool-2 --recursive-unset,
but it would be nice to know the subset of elements what to 'unset', like just 'panel'.

this way you can revert certain settings to defaults, until you find the culprit.

Does ~/.xsession-errors contain any useful debug about the error?

---

### Post by i++ on 2006-06-06
from ~/.xsession-errors

```
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed the application.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed the application.
The application 'update-notifier' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed the application.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed the application.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed the window manager.
```

before all that i get loads of this..

```
(gnome-panel:5113): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion 'src != NULL' failed

(gnome-panel:5113): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

:S doesnt look good though, will reconfiguring X help?

---

### Post by mlind on 2006-06-06
well those errors were not very useful, something is causing X to crash..
what about erros on /var/log/Xorg.0.log ?

I don't think reconfiguring would do any good because it works for another user.
Have you tried logging into a "Default Gnome Session" from login screen instead?

---

### Post by i++ on 2006-06-06
logging into a Default Gnome Session doesnt work either. 

my log file is [here]("http://www.badlydeveloped.com/Xorg.0.log")

its a huge file, so im not sure what part may be of interest/help, but near the end there is a lot of ```
drmOpenDevice: node name is /dev/dri/card225
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
```

thanks for your help:)

EDIT -- (II) fglrx(0): Largest offscreen area available: 1280 x 410 - that doesnt look good :S picked that from the log file, any help?

---

### Post by mlind on 2006-06-06
Just by grepping entries (WW) and (EE) you'll see that everything isn't allright.


```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

```
maybe you should try to reconfigure Xorg again like you said

```

(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
Unsupported Mode: -1232154624x0@0.000000

```

that could be your problem, something is asking for funny looking unsupported mode

You can also remove every wacom entry from Xorg.conf, but I don't think those
errors are fatal.

I'll get back to you in a minute..

---

### Post by i++ on 2006-06-06
okay thanks! i'll try reconfiguring xserver-xorg for the moment...

---

### Post by mlind on 2006-06-06
do this aswell from terminal

```

gconftool-2 --recursive-unset /desktop/gnome/screen

```

and try to login.

This will remove any custom screen resolution settings you've set from gnome.

---

### Post by i++ on 2006-06-06
my GDM no doesnt start, it starts in text mode.. so i login to my username, that works fine, so i type startx

dave@dave-desktop:~$ startx
xauth:  timeout in locking authority file /home/dave/.xserverauth.6521
xauth:  timeout in locking authority file /home/dave/.Xauthority
xauth:  timeout in locking authority file /home/dave/.Xauthority
xauth:  timeout in locking authority file /home/dave/.Xauthority

then it tries to load, i get the default mouse (x) and then

xauth:  timeout in locking authority file /home/dave/.Xauthority

:(

sudo startx works, however im not logged in as dave.. think im logged in as root.

---

### Post by mlind on 2006-06-06
don't use startx as root or you screw up ~/.Xauthority permissions.
Login your account from tty1 (Ctrl + Alt + F1)

try
```

sudo /etc/init.d/gdm stop
sudo rm ~/.Xauthority
gconftool-2 --recursive-unset /desktop/gnome/screen
sudo /etc/init.d/gdm start

```

/edit
if you removed those wacom devices from xorg.conf,
remember to take those out of "ServerLayout" section too.

---

### Post by i++ on 2006-06-06
okay brilliant thanks, that helped, i now have gdm login screen up. however, still same problems logging in...

after i reconfigured xserver-xorg, x could not start because the driver 'ati' was installed, and this doesnt work on my system, however i fixed it by nano /etc/X11/xorg.conf and changing ati to radeon.

still nothing when i log in as dave though ,no splash or anything :(

---

### Post by mlind on 2006-06-06
You said that everything worked fine for 'test' user, right?

You can achieve same by taking backups of .gconf .gnome .gnome2 (.nautilus ?)
folders, and then in this orde remove one directory and try to login to X session.

Just remove / rename one directory at time and try to login.
You will lose gnome preferences this way tho..

---

### Post by i++ on 2006-06-06
yeah test user is working 100%

okay will try that! so i take the .gconf... folders from the working test user? and place them into dave user? i will back everything up first.

Thanks for all this help mlind :D

---

### Post by mlind on 2006-06-06
No, don't take the .gconf settings from any other user, just delete the folder
and let gnome create new one from scratch.

---

### Post by i++ on 2006-06-06
oh okay, cool, i tried to backup the dir's... but i got this

dave@dave-desktop:~$ sudo cp ~/.gconf ~/.gconf_backup
cp: omitting directory '/home/dave/.gconf

how do i backup directories?

---

### Post by Ramses de Norre on 2006-06-06
You don't need to use sudo, that could mess up permissions in your home folder.
And you'll need to use cp -R.

---

### Post by i++ on 2006-06-06
after removing .gnome2 and then logging in i got an error message that said your session lasted less than 10 sconds which means that there may have been a problem with installation. try running a failsafe gnome session. 

this did the same thing..

the ~/.xsession-errors output is here

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "dave"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:5739): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission Denied
Could not create per-user gnome configuration directory '/home/dave/.gnome2' :  Permission Denied
```

im guessing this means it doenst have the permissions to re-create the folders i just removed... lol

brb 1 hour dinner

---

### Post by nkhansen on 2006-06-06
Hello again, back from work now. Have you tried the

```
$ cd /home/dave
$ sudo chown -R dave:dave *
```

Alternatively, you could delete dave's homedir, copy test to dave and change the owner back to dave:
**!Remember to back up dave's very important data!**
```

$ cd /home
$ sudo rm -r dave
$ sudo cp test dave
$ sudo chown -R dave:dave dave

```

Last command has a lot of daves in it, but this should work. ;-)

---

### Post by Ramses de Norre on 2006-06-06
```
$ sudo cp test dave

```
Shouldn't that be 
```
sudo cp -R test dave
```
or
```
sudo mv test dave
```

---

### Post by i++ on 2006-06-06
right, okay, i will give that a go, copying test to dave, however, i have rather a lot of data that i need to back up... so i'll be back tomorrow, leave it backing up overnight.

I will post the results of what happens and probably some more questions here tomorrow after i've tried that! thanks again

until tomorrow maybe!

i++

---

### Post by i++ on 2006-06-06
one last thing, i have all my documents on a partition /documents, this wont be affected will it? as the users should be stored on / ?

---

### Post by i++ on 2006-06-06
Success! using a combo of both of your replies i copied test to dave then renamed it dave, so now original login dave works, although without my settings, but thats easy to change back as it was a young install 

:D

thanks SO MUCH! you legends!

have now removed user test as well

thanks again,

i++

---

### Post by Ramses de Norre on 2006-06-06
No, but you'll want to change the owner of it.
```
sudo chmod -R new_username /documents
```

---

### Post by i++ on 2006-06-06
done, thanks :)!

```
sudo chown -R dave /documents
```

---

### Post by mlind on 2006-06-06
[QUOTE=i++]Success! using a combo of both of your replies i copied test to dave then renamed it dave, so now original login dave works, although without my settings, but thats easy to change back as it was a young install[/QUOTE]

Gnome related application preferences should be found in your ~/.gnome2
backup folder. Folder is usually renamed after the application, like ~/.gnome2/rhythmbox

Merging .gconf settings is possible too, but it's probably not needed.
You'll just want the application preferences.

---

### Post by i++ on 2006-06-06
okay thanks :)

gotta love it when something goes wrong and then u remember you backed it all up !

---

### Post by freddo on 2006-06-07
Hi! I have the same problem witch my Dell Latitude D620. Nice to se there is a solution to the problem. In my case I did'nt change anything. Just i fresh install, patches, VMplayer, 915resoultion with 1440/900 working fine.

What could be the reason for the problem? I++, still working fine?

---

