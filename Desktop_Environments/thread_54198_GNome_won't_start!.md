---
title: "GNome won't start!"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Muiske on 2005-08-03
Okay, I have the following problem.



After booting Linux, I get the normal Ubuntu login screen. I try to log in but after I've entered my username/pw it hangs for a while and then displays the login screen again. Nothing I can do seems to help. I've tried to run it in safe mode, alternative GNome sessions but everytime the problem arises. 

Logging in at a shell is possible, and I can access all features of the system. 

When I stop the gdm, remove .Xauthority, .ICEauthority and clean the /tmp dir the problem stilll persists. 

'startx' gives this error message:

xauth: timeout in locking authority file 
   -> this message is displayed four times

then it starts the login screen but I still can't login to Gnome / X / whatever.






Anyone? Please?  ](*,)

---

### Post by amohanty on 2005-08-03
> Logging in at a shell is possible, 

Do you mean the recovery mode?

ALso what does:
>> ls -l ~/.XAuthority
and
>> ls -l .ICEAthority

return?

AM

Forgot:
What does 
>> xauth -v 
return?

---

### Post by Muiske on 2005-08-04
amohanty, thanks for your reply.




> Do you mean the recovery mode? 

No, I mean logging in 'text modus' after I have completely killed gdk. I get there by pressing Ctrl + Alt + F1 and commanding 'gdk stop' (with sudo).

> ALso what does:
>> ls -l ~/.XAuthority
and
>> ls -l .ICEAthority

return?

AM

I have not tried that yet, but I think it will just give blank results since I removed both files..... what does the '-l' option do?

> Forgot:
What does 
>> xauth -v 
return?

I will try that as soon as I am home (and have access to my Linux box) again. 


Muiske

---

### Post by Muiske on 2005-08-04
[QUOTE=amohanty]
What does 
>> xauth -v 
return?[/QUOTE]





$  xauth -v

Returns with the same error as described earlier: 
xauth: timeout in locking authority file
/home/muiske01/.Xauthority


I discovered I can still login as root... I cannot, however, login using my username (muiske01). 

I've tried to see what .xsession-errors says:




/etc/gdm/PreSession/Default: Registerin your session with wtmp and utmp
:running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "muiske01" 
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:8266): WARNING **: Unable to read ICE authority file: /home/muiske01/.ICEauthority



So that leaves me with the same problem. Basically put, something might have changed with the permission of the home directory. However, when I try to change that manually using the chmod (chome muiske01.muiske01 /home/muiske01/.X[file]) and chown commands it does not change anything.

I have, following advice of a more experienced user, deleted the .Xauthority and .ICEauthority files and cleaning the /tmp dir. It should restore the values to default, but apparently it does not work. 


I'm getting quite desparate now. There must be a fairly simple solution for this! 

Can anyone please help? I need to get access to my linux again!!   :-|

---

### Post by professor_chaos on 2005-08-04
[QUOTE=Muiske]$  xauth -v

Returns with the same error as described earlier: 
xauth: timeout in locking authority file
/home/muiske01/.Xauthority


I discovered I can still login as root... I cannot, however, login using my username (muiske01). 

I've tried to see what .xsession-errors says:




/etc/gdm/PreSession/Default: Registerin your session with wtmp and utmp
:running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "muiske01" 
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:8266): WARNING **: Unable to read ICE authority file: /home/muiske01/.ICEauthority



So that leaves me with the same problem. Basically put, something might have changed with the permission of the home directory. However, when I try to change that manually using the chmod (chome muiske01.muiske01 /home/muiske01/.X[file]) and chown commands it does not change anything.

I have, following advice of a more experienced user, deleted the .Xauthority and .ICEauthority files and cleaning the /tmp dir. It should restore the values to default, but apparently it does not work. 


I'm getting quite desparate now. There must be a fairly simple solution for this! 

Can anyone please help? I need to get access to my linux again!!   :-|[/QUOTE]
 Can you change the permission/owner of .Xauthority???

---

### Post by Muiske on 2005-08-05
[QUOTE=professor_chaos]Can you change the permission/owner of .Xauthority???[/QUOTE]


I tried with chmod muiske01.muiske01 /home/muiske01/.Xauthority


Should I do something else? And if so, could you give me the commands? I want to change the permission (or ownership) of these files to 'muiske01' which is my user account. That should fix it....

---

### Post by professor_chaos on 2005-08-05
You didn't mention this so....

Try ```
ls -la /home/muiske01/.Xauthority
``` 
this will give you info on the ownership and privilages of that file.

if the owner listed is not you (maybe root), then 

```
sudo chown muiske01 /home/muiske01/.Xauthority
``` 

then just to make sure privilages are wide open...

```
chmod 777 /home/muiske01/.Xauthority
```

---

### Post by amohanty on 2005-08-05
>  what does the '-l' option do? 

That provides the file listing in long format ie tells you who own it and what rights its has.

Basically what has happened is that now root owns the .XAuthority fie in your account!!! So you as the user cannot login.

If you follow prof..chaor' suggestions it will revert the ownership and rights to you which will allow you to login.

AM

---

### Post by Muiske on 2005-08-06
professor_chaos and amohanty, thanks a lot. I figured it out yesterday....


sudo chown muiske01 /home/muiske01/.ICEauthority



did the trick. So it was an ownership / permission issue after all.


Thanks! :)

---

### Post by panth0r on 2005-09-08
Thank you all so much, I was just having the same problem and it turned out hat root was the owner of .ICEauthority, and thanks to professor_chaos, I was able to get it working again... and I was seconds away from re-installing, thanks again!

---

### Post by outchy on 2006-02-11
this just helped me with my problem, which was quite similar.  for future reference, this what i got when i booted up my machine today:

Your session only lasted less than 10 seconds.  if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem:  ~/.xsession-errors

i couldn't log in with any method except for failsafe terminal mode but at least i could look at the ~/.xsession-errors file.  here's what it said:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -1 ":0" "outchy"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8536): WARNING **: Unable to read ICE authority file: /home/outchy/.ICEauthority

so i looked at my /.ICEauthority ownership and sure enough, it was owned by root.  i had just installed komposé and yakuake the night before, so i suspect one of those to be the culprit.  any thoughts on which one did it and why?

thanks for this thread, you saved my install too :)

---

