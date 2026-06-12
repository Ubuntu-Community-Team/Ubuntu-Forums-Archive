---
title: "Serious Network/SUDO (?) Problem"
date: 2005-09-21
forum: Desktop Environments
---

### Post by pawel_z_wroclawia on 2005-09-21
Hello,

I am using Hoary with KDE (Kubuntu installed on top of Ubuntu). Recently, I've tried installing PC-BSD and it messed up my GRUB. With my bro's help, I've managed to repair it (thanks, Misiek), but (probably due to some unsuccessful attempts) the system behaves strangely now. I've no network and when I try to run network-admin it doesn't accept my password, saying it's not correct (the same thing happens with user administration, on the other hand, Synaptic works just fine). The same thing happens when I try to run it from the console with sudo. On the other hand, when I try to run it from the console as a root, it won't let me run X (huh?). 

Moreover:
1) When I try to run network-admin _the second time_, it does not ask me for password and automatically assumes it's wrong.

2) Root console doesn't work - when i click on the menu item, simply nothing happens. I have to do sudo from the console to bring up root mode (I don't know if it's related, it had been like that even before I started messing with PC-BSD).

Seems a serious problem and I have no idea what's wrong  ](*,) . Any help will be much appreciated! 

Should I clarify something? (This, however, may take some time, as Ubuntu is at home, with no net access, and right now I'm using Windows at work to post this.)

---

### Post by leezer3 on 2005-09-21
You're stuck in precisely the same hole as me, with no end in sight :(
(Have a search for my thread 'severe priveldges problem')
Only thing I can really suggest at the mo, is to use root access by killing X at startup, with CTRL+ALT+F1, logging in using the root & your root password and then running 
```
killall gdm
start x
```
- This will give you a working root GUI.

Cheers

-Leezer-

---

### Post by Xiata on 2005-09-21
[QUOTE=leezer3]You're stuck in precisely the same hole as me, with no end in sight :(
(Have a search for my thread 'severe priveldges problem')
Only thing I can really suggest at the mo, is to use root access by killing X at startup, with CTRL+ALT+F1, logging in using the root & your root password and then running 
```
killall gdm
start x
```
- This will give you a working root GUI.

Cheers

-Leezer-[/QUOTE]
 Yeah... THATs safe. (/sarcasm)

The Root Terminal menu entry usually doesn't work in kde, because it does not depend on kdesu to log it in, try editing its link to use kdesu if you use kde. gksudo doesn't really like to work all the time.

You can always just run the program from run but specify that it has to be run as root. Or sudo bash in a console, or just use gnome like ubuntu was designed for.

[size=1]edit: gksudo... kdesu... bleh![/size]

---

### Post by leezer3 on 2005-09-22
I never said it was safe  :roll: 
The point is, that if he is in the same situation as I am, then sudo won't work either. This means that the only method that I have found that works to get root priveledges is to do this.
Ditto, run as root simply doesn't work, just kicks me straight out again.

Please, spare the lectures- Give me a way to fix this!  ](*,) 

Cheers

-Leezer-

---

### Post by pawel_z_wroclawia on 2005-09-22
I guess I wasn't clear enough in my first post. 

First of all, I do have Gnome (but I chose to use KDE, installed KDE packages after installing basic Ubuntu with Gnome). And I have the same problems under Gnome... see below. 

Anyway, the current situation. With my bro's help (thanks again :-)), I managed to get the net working with ifconfig. But that's just the beginning.

Now my problem  is that some of the graphical applications that require root privileges do not work (e.g. network-admin). Examples of error messages:

When I give command:
pawel@ubuntu:~$ network-admin

or:
pawel@ubuntu:~$ sudo network-admin

an error message window appears:
The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key

then:
The "network-admin" program was started with the privileges of the root user without the need to ask for a password, due to your system's authentication mechanism setup.

It is possible that you are being allowed to run specific programs as user root without the need for a password, or that the password is cached.
This is not a problem report; it's simply a notification to make sure you are aware of this.



And the command:
root@ubuntu:/home/pawel # network-admin

gives the following:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(network-admin:9164): Gtk-WARNING **: cannot open display:

I've heard that this may be a PAM problem... Anybody?

---

### Post by skoal on 2005-09-22
Pawel, I'm gonna take a stab here, and may be completely off base.  However, I know for certain GTK apps running in _KDE_ (requiring root privs), you have to X "Run as different user" in the menu editor, or it will fire up the app and give you various success (or results).

Now, that's what it sounded like in your first post.  Your second post, however, seemed a tad bit more "meaty" and complex than the simple problem (above).  You can safely ignore that last bit of error message ":0.0 refused server" while running as root (at the bottom in your last post).  It _should_ do that.  

Well, anyways, I only use KDE.  What package does the 'network-admin' app come from? I'll try 'er out for ya...

\\//_

---

### Post by pawel_z_wroclawia on 2005-09-22
1) The command for menu item "Networking" is:

gksudo network-admin

... so I don't think running as a different user would help, would it?

2) As I said, I first installed just Ubuntu, than installed KDE from packages. So, technically speaking, it's not "pure" Kubuntu... Don't know which approach is better. 

Anyway, the applications that won't work come from Ubuntu base installation - these are Ubuntu, not Kubuntu packages (BTW, is there Kubuntu graphical utility for network settings? Can't see anything like it...). They used to work all right... and, frankly, I have no idea what happened to them (these are not packages I would run on daily basis, so I can't even pinpoint the moment they stopped working... right now my wild guess would be: after I tried XFCE, but that may be just a coincidence).

That's as much as I know... but the same problem is with users-admin applications, so it's rather a global problem... with Gnome applications and PAM perhaps?

---

### Post by leezer3 on 2005-09-23
Yes, precisely the same hole as me!
Not quite sure one the KDE front, I would only ever use Gnome  :grin: , but for me, on this install, nothing requiring root priveldges has ever worked :(

Small thought though- Would the charset selected during install have any bearing on this (I selected En-UTF8, rather than plain En)

Cheers

-Leezer-

---

### Post by fordfan753 on 2005-09-23
[QUOTE=pawel_z_wroclawia
And the command:
root@ubuntu:/home/pawel # network-admin

gives the following:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(network-admin:9164): Gtk-WARNING **: cannot open display:

I've heard that this may be a PAM problem... Anybody?[/QUOTE]

To fix this, simply enter
```
xhost +
``` 
This changes who can access X, and will let root access X.

---

### Post by Dooglus on 2005-09-23
It sounds like your user might not be a member of the admin group.

Get access to a root shell somehow and run:

    adduser youruser admin
    adduser youruser adm

(where youruser is your account name).

After that, you should be able to use sudo, and run admin applications from your user account.

If you can't get access to a root shell using sudo, or by logging in with the root password, then you will be able to get root access by booting from a rescue CD.  Probably the CD you used to install ubuntu in the first place will have some kind of 'rescue' mode - I can't remember and I gave mine away months ago.


If this 'adduser' thing doesn't work, you can edit /etc/gdm/gdm.conf and change "AllowRoot=false" to "AllowRoot=true" to allow root to log in using gdm.  This is a dangerous thing to do, and should only ever be attempted as a last resort, and only when not on-line.  Don't forget to change it back before you plug yourself back into the net.

---

### Post by leezer3 on 2005-09-27
Its telling me that the group 'admin' does not exist, and that I am already a member of ADM. Thoughts?

Cheers

-Leezer-

---

### Post by Zwack on 2005-09-27
try grep ^adm /etc/group which should list all groups called adm*
I get two
adm (gid 4)
and admin (gid 109) with myself as the only members of them.

If you can get root access somehow (su, sudo) then check /etc/sudoers and see if it has a line like this in it.

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

If it does then members of the group admin should be allowed to use sudo.

Unfortunately /etc/sudoers is only readable by root so you will have to be root somehow in order to read it (rescue disk, stand alone linux boot, you have options for this)

sudo -l should list what permissions you have under sudo.

oh and id should tell you who you are and which groups you are a member of....

I hope that this helps,

Z.

---

