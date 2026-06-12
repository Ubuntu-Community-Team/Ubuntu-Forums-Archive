---
title: "Oopps..just broke Ubuntu !!!"
date: 2005-02-24
forum: Desktop Environments
---

### Post by marcadams on 2005-02-24
Whoops...I have just broken Ubuntu. I would be very, very grateful if someone could help me recover my desktop!

I wanted to install a game, so I looked thro' the Universe repositry and found "Billards".
I installed this and run it. Unfortunately I was unable to get out of the application, so I pressed my Power Off button, which tells Ubuntu to shut down (rather than simply kill the power). So it should have shut down gracefully.

I rebooted, but now:

- I get a message saying my session lasted less than 10 seconds, which may be due to an installation problem
- The reboot appears to get to the point just BEFORE the splash screen is about to start (I.e. graphically showing the various items initialising).

The only way I can get into Ubuntu is to use the failsafe Terminal option (which I am using now).

Unfortunately I cannot copy the error messages into this screen (due to my failsufe logon), so I will briefly describe the messages. I have sent the error file to work, so I will post this tomorrow. However, in summary:

etc/gdm/presession/Default: Registering your session with wtmp and utmp
etc/gdm/presession/Default: running: /usr/bin/X11/sessreg    <and a load of parameters>
etc/gdm/Xsession: Begining session start up...

** (gnome-session: 5002): WARNING**: Unable to read ICE Authority file: home/marc/.ICEauthority


... and that is it - no other messages. I only have the normal Gnome desktop configuration...I don't have an ICE Desktop installed.  

Should the system be trying to read this file, or is the file just unreadable / got incorrect info?


Any help in getting my desktop back will be VERY much appreciated.. 

Thanking-you
Marc

---

### Post by cka on 2005-02-24
See if typing "ls $HOME/.ICEauthority" returns anything.


- If it does, rename the file to something like .ICEauthority.broken and reboot.

- If it doesn't, make one and chown it to yourself (touch $HOME/.ICEauthority ; chown $USER:$USER $HOME/.ICEauthority ; chmod 600 $HOME/.ICEauthority), and reboot.

If none of that works, perhaps somebody else with more experience can help.

---

### Post by marcadams on 2005-02-25
Thanks Cka - I will try this as soon as I get back from work.

On a slightly different note, does anybody know what this file is for? 

With a largely standard Ubuntu install, should it even be there?

Lastly - as this is a file, something must be trying to read it...does anybode know what could be referencing it?


I now have the complete listing of the .session-errors file

"
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "marc"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:5225): WARNING **: Unable to read ICE authority file: /home/marc/.ICEauthority
"

Does this provide anyfuther insight?

Thanks Again
Marc

---

### Post by marcadams on 2005-02-25
Hi Cka;

I just renamed the troublesome file, and rebooted - my system is back and running!
Yippee - thanks alot.

Can someone tell me what this file was for, in case I have to re-configure something.


Thanks for the help
Marc

 \\:D/

---

### Post by valadil on 2005-02-26
The file basically says that a given user is logged into this machine from a certain ip and don't confuse it with the same user from another ip.  For a desktop machine and not a professional workstation its pretty much worthless.  This file has been giving us shit at work and we've just told people to remove it.  Haven't seen any bad side effects from doing so so far.

---

