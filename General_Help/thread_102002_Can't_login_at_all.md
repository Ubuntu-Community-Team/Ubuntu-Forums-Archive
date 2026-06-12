---
title: "Can't login at all"
date: 2005-12-11
forum: General Help
---

### Post by XeroXer on 2005-12-11
Ok I made a mess yesterday.
I just searched all the forums for a way to get my network working.
And I found this ([http://ubuntuforums.org/showthread.php?t=5409]("http://ubuntuforums.org/showthread.php?t=5409")) and thought I'd give it a try.
The only BIG problem is that I got "Ubuntu Breezy Badger 5.10".
Stupid as I am I didn't even read what this was for.
I just started changing the files. (made backups of course)

But now I can't even log in.
When I try to log in with my regular user I just get a message saying:
**Authentication failed!**
And then the login screen comes back on.
If I write a user that does not exist or if I enter the wrong password for my user, then it just goes back to writing username and says I entered wrong information.
So it knows that I have entered the right information but the login is still broken.

This was a BIG misstake bye me but hopefully there is a way to save my precious computer...
???

---

### Post by kaamos on 2005-12-11
Not too sure about this, but you could try:

Try selecting recovery mode from the grub menu and then run the command
```
chown **username**:**username** /home/**username**/.Xauthority
```
Of course replacing username..

Lycka till!

---

### Post by XeroXer on 2005-12-11
[QUOTE=kaamos]Not too sure about this, but you could try:

Try selecting recovery mode from the grub menu and then run the command
```
chown **username**:**username** /home/**username**/.Xauthority
```
Of course replacing username..

Lycka till![/QUOTE]

I got in to the recover mode area.
Entered:
```
chown xeroxer:xeroxer /home/xeroxer/.Xauthority
```
Got back:
```
chown: cannot access `/home/xeroxer/.Xauthority`: No such file or directory
```

---

### Post by kaamos on 2005-12-11
Does the "Authentication failed!" failed message come up when you try to login from the command line? Test by booting normally and when in the graphical login press: ctrl+alt+f2

If you can login, try the command: startx
If it gives errors, try posting them here..

EDIT: before the startx command you might have to do this: sudo /etc/init.d/gdm stop
This kills the graphical login manager.

---

### Post by XeroXer on 2005-12-11
[QUOTE=kaamos]Does the "Authentication failed!" failed message come up when you try to login from the command line? Test by booting normally and when in the graphical login press: ctrl+alt+f2

If you can login, try the command: startx
If it gives errors, try posting them here..

EDIT: before the startx command you might have to do this: sudo /etc/init.d/gdm stop
This kills the graphical login manager.[/QUOTE]

When I try to login through the command line I get the error "Login incorrect" instead.

---

### Post by kaamos on 2005-12-11
Ok, try chowning everything in your home folder to yourself. So back to the rescue mode and:```
chown -R xeroxer:xeroxer /home/xeroxer
```
Notice the R is capital (means recursive)

Note that these are pretty general tricks to get the login going, and you should check the files that you edited trying to get NT Domain Authentication to work, and look if there's something out of place.

---

### Post by XeroXer on 2005-12-11
[QUOTE=kaamos]Ok, try chowning everything in your home folder to yourself. So back to the rescue mode and:```
chown -R xeroxer:xeroxer /home/xeroxer
```
Notice the R is capital (means recursive)

Note that these are pretty general tricks to get the login going, and you should check the files that you edited trying to get NT Domain Authentication to work, and look if there's something out of place.[/QUOTE]

I went into recover mode and entered:
```
chown -R xeroxer:xeroxer /home/xeroxer
```
No utput from it but no error either.
What am I supposte to do after that? :-)

---

### Post by kaamos on 2005-12-11
Reboot (the command is "shutdown -r now" if you're still in rescue mode), boot normally, and try to login both from graphical and command line. If does not work I suggest you start checking the files that you altered earlier. The command to change a file in a text editor in rescue mode is "nano /path/to/file".

I hope your system going soon. :)

---

### Post by kaamos on 2005-12-11
I attached the mentioned files from my breezy box in a zip archive.

---

### Post by XeroXer on 2005-12-11
[QUOTE=kaamos]Reboot (the command is "shutdown -r now" if you're still in rescue mode), boot normally, and try to login both from graphical and command line. If does not work I suggest you start checking the files that you altered earlier. The command to change a file in a text editor in rescue mode is "nano /path/to/file".

I hope your system going soon. :)[/QUOTE]

I tried booting both ways but it didn't work.
So I went into rescue mode to alter the files:
[INDENT]/etc/login.defs
/etc/nsswitch.conf
/etc/samba/smb.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/pam.d/sudo[/INDENT]

But I don't know how the files:
[INDENT]/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/pam.d/sudo[/INDENT]
was from the beggining.

The other files:
[INDENT]/etc/login.defs
/etc/nsswitch.conf
/etc/samba/smb.conf[/INDENT]
are back to their original states.

Still can't login from any of the two ways. :-(

---

### Post by kaamos on 2005-12-11
^ zip file before your post. :rolleyes:

---

### Post by XeroXer on 2005-12-11
Well now all the files I altered are back to their original state.
But still I can't login through any of the two ways.
This is starting to get more strange every second...

---

### Post by kaamos on 2005-12-11
Now that is indeed strange..

If you have rebooted after changing the files (and are indeed sure that they are now breezy defaults) and still can't log in, I'm out of suggestions. Sorry. :(

---

### Post by John Jason Jordan on 2005-12-11
[QUOTE=kaamos]Not too sure about this, but you could try:

Try selecting recovery mode from the grub menu and then run the command
```
chown **username**:**username** /home/**username**/.Xauthority
```
Of course replacing username..[/QUOTE]
I am having the same problem. It started after I had to use the power button because Kdar had locked up Linux. (Mouse, keyboard dead, CPU at 2 GHz.) My username is jjj. When I try to log in I get:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem. 
__ View details (~.xsession-errors file)
/etc/gdm/PrreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PrreSession/Default: running: /usr/binX11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x “/var/lib/gdm/:0.Xservers” -h “” -l “:0” “jjj”
       /etc/gdm/Xsession: Beginning session setup...
No profile for user ‘jjj’ found
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X
_IceTransmkdir: ERROR: cannot create /dev/X
_IceTransPTSOpenServer: mkdir(dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Devil5:
_IceTransMakeAllCOTSServersListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Devil5:
_IceTransMakeAllCOTSServersListeners: failed to open listener for isc
_IceTransISCOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Devil5:
_IceTransMakeAllCOTSServersListeners: failed to open listener for sco

** (gnome-session:8220): WARNING **: Unable to read ICED authority file: 	    /home/jjj/.ICEauthority

That was after trying chown as suggested by kaamos above.

I have 64-bit Breezy Live/Install CDs that I got at a local LUG meeting. I can get into the filesystem, and everything looks normal. My home directory appears intact, including all my files.

I hope someone can tell me what to do to fix this problem!

---

