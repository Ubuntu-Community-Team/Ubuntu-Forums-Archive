---
title: "Root?  What root?"
date: 2005-05-02
forum: Desktop Environments
---

### Post by anon.irisX on 2005-05-02
Don't worry;  I am a Linux newbie, but I do know what root is. :D

I've successfully installed Kubuntu AMD64 this afternoon, although it was quite a frustrating installation process.

I am having one other minor problem besides this one, which I think I can fix now.   But, one thing is still quite confusing.  

When I was going through the installation, it never asked me to set up a root account.  This is quite irritating, because there is a couple of apps I really want to get on, but I can't log in as root.  

I open the package manager thing, and it asks for the password like I suppose it should.  But it doesn't know that I don't actually *have* a root password.  

Is there any way I can set this up without having to install the thing again?  

Thanks much.

---

### Post by nemin on 2005-05-02
[QUOTE=anon.irisX]
When I was going through the installation, it never asked me to set up a root account.  This is quite irritating, because there is a couple of apps I really want to get on, but I can't log in as root.  

I open the package manager thing, and it asks for the password like I suppose it should.  But it doesn't know that I don't actually *have* a root password.[/QUOTE]
Enter your own password:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by ltmon on 2005-05-02
What isn't explained in the Wiki is that the kdesu prompt (the prompt that asks you for the password when starting the package manager) is actually asking for the password of the first user that was added (i.e. the user you added during installation).

It's quite possible (and just as easy) to operate Kubuntu without a root password as the developers intended.


Cheers,

L.

---

### Post by davefr on 2005-05-02
I'm just a newbie but this root issue is a PIA.  I want to always be root and not be nagged every few minutes for a password to do simple things.

I just read about this fix.  Sudo gedit /etc/kde/kdm/kdmrc.  Find allowrootlogin and change it to true.

i haven't done it yet but it's supposed to work.  I'd also like an autologin as root and hope this fix makes that option possible.

---

### Post by siebzehn on 2005-05-02
[QUOTE=davefr]I'm just a newbie but this root issue is a PIA.  I want to always be root and not be nagged every few minutes for a password to do simple things.

[/QUOTE]

You should NEVER use the root account all the time.  This is the biggest problem with windows, by default your users have administrative permissions, you should never do this in linux.  Use the root account ONLY when needed.

---

### Post by gunnyman on 2005-05-02
[QUOTE=davefr]I'm just a newbie but this root issue is a PIA.  I want to always be root and not be nagged every few minutes for a password to do simple things.

I just read about this fix.  Sudo gedit /etc/kde/kdm/kdmrc.  Find allowrootlogin and change it to true.

i haven't done it yet but it's supposed to work.  I'd also like an autologin as root and hope this fix makes that option possible.[/QUOTE]

YIKES

root login is bad enough, but autologin???
make sure you aren't connected to the  internet in any way shape or form if you do that....

---

### Post by ubersoft on 2005-05-02
For the record, it seems that sudo dosen't always work.

I use inkscape for a lot of things -- and I need to use one of the CVS builds, not the version you can get using apt-get, in order to use fonts consistently without the application crashing.

Unfortunately, when I try to install the CVS build, it asks for the root login... and it doesn't recognize my regular account password, unlike KDE which does. So I had to create a password for my root account before I could install it.

sudo is a pretty cool idea, but circumstances have forced me to set up the very environment it was intended to prevent.

---

### Post by davefr on 2005-05-02
You're right but I wish Kubuntu made it easier to log out, log in again as root and perform all superuser functions, then log out and back in again as a regular user.

[QUOTE=siebzehn]You should NEVER use the root account all the time.  This is the biggest problem with windows, by default your users have administrative permissions, you should never do this in linux.  Use the root account ONLY when needed.[/QUOTE]

---

### Post by davefr on 2005-05-02
P.S. I tried this fix tonight and it worked great.  I find it a lot more efficient to switch user to root and do all your configuring then switch back to normal user mode.


[QUOTE=davefr]I'm just a newbie but this root issue is a PIA.  I want to always be root and not be nagged every few minutes for a password to do simple things.

I just read about this fix.  Sudo gedit /etc/kde/kdm/kdmrc.  Find allowrootlogin and change it to true.

i haven't done it yet but it's supposed to work.  I'd also like an autologin as root and hope this fix makes that option possible.[/QUOTE]

---

### Post by anon.irisX on 2005-05-02
If you actually have a root password, that is. :)

I used your suggestions, thank you, but I still can't change some things; for example, the time is 10 hours ahead (the time zone is set properly), but I still can't change that with my password.  It's so wierd!

---

### Post by ltmon on 2005-05-02
[QUOTE=anon.irisX]If you actually have a root password, that is. :)

I used your suggestions, thank you, but I still can't change some things; for example, the time is 10 hours ahead (the time zone is set properly), but I still can't change that with my password.  It's so wierd![/QUOTE]

This could be related to a windows partition.  Linux likes to set the clock to universal time, wheras windows likes it at local time.  When you boot into both you can get problems if it isn't set up correctly.  This would make sense 'cos us here on the east coast of Australia are at GMT+10.

Maybe this will work for you, but I'm not sure (I don't dual boot):

How to stop Windows time from being reset to UTC (for dual booters).
01) $ sudo kate /etc/default/rcS
02) Find the line UTC=yes
03) Change it to UTC=no
04) Save the edited file.


L.

---

### Post by niney on 2005-05-02
you can use 'sudo su' to get a root shell if you need it.
Better than logging in as root...

---

### Post by anon.irisX on 2005-05-03
Oh now I get it.  So to log in as root from Konsole I do 'sudo su', instead of the usual 'su'.  That should work better, considering it won't take my password with su.  Unfortunately I can't just try it out, because I have to use my mums computer for the internet, and I don't think she would appreciate me putting Linux on it for her.  :D

---

### Post by Terracotta on 2005-05-04
[QUOTE=davefr]I'm just a newbie but this root issue is a PIA.  I want to always be root and not be nagged every few minutes for a password to do simple things.

I just read about this fix.  Sudo gedit /etc/kde/kdm/kdmrc.  Find allowrootlogin and change it to true.

i haven't done it yet but it's supposed to work.  I'd also like an autologin as root and hope this fix makes that option possible.[/QUOTE]

And what are the things you have to get your root password for in regular use????
I'm never asked for my pasword unless I want to change some SPECIAL stuff, or when I want to install anything, wich doesn't happen THAT often  :smile:
about the autologin: I'ld like that too: no one else but me uses the computer and without a password no one can make changes on my system, so it's usefull, and if you have a laptop you can always turn it off in case someone wants to steal it. I understand completely why people say you shouldn't be root all the time, but calling autologin worse than being root all the time is quite confusing??? :???:

---

### Post by davefr on 2005-05-04
Editing files outside of Home, installing apps, configuring Control Panel settings.

I did enable root login capability but just turned it off since it appeared to be screw up my Knemo install. (ie icon went to root but not to non-root users).

I suppose I can get bye the way Kubuntu handles root access.  It's kind of a PIA but that's probably because I'm doing lots of initial setup/config/installs.

I wish there was a command to enable everthing as root on a temporary basis.  I thought sudo su would do that but it only applies to a terminal window and not the KDE interface.






[QUOTE=Terracotta]And what are the things you have to get your root password for in regular use????
:[/QUOTE]

---

### Post by siebzehn on 2005-05-04
[QUOTE=Terracotta]And what are the things you have to get your root password for in regular use????
I'm never asked for my pasword unless I want to change some SPECIAL stuff, or when I want to install anything, wich doesn't happen THAT often  :smile:
about the autologin: I'ld like that too: no one else but me uses the computer and without a password no one can make changes on my system, so it's usefull, and if you have a laptop you can always turn it off in case someone wants to steal it. I understand completely why people say you shouldn't be root all the time, but calling autologin worse than being root all the time is quite confusing??? :???:[/QUOTE]
 The problem I see with autologin is that anybody can change/delete your personal files.  Ok, nobody can mess with the system, nobody can uninstall programs, but your own stuff is at risk.

---

### Post by Terracotta on 2005-05-04
[QUOTE=siebzehn]The problem I see with autologin is that anybody can change/delete your personal files.  Ok, nobody can mess with the system, nobody can uninstall programs, but your own stuff is at risk.[/QUOTE]

Anyone can do that from over the internet? didn't know that :-). But isn't someone capable of doing that from over the internet once you logged in as well?? I thought that was what the root was for, to protect people from other guys/girls on the net to mess with your computer since they can't do what you can't, but once you're logged in, I thought they can acces your computer and do whatever you can, no matter autologin or not, correct me if I'm wrong please :-), always willing to learn.

@davefr: ok, it seems like you're changing your computer's behavior all the time than :-), for "normal" use I think that the sudo thing ain't a PIA, unless you're still learning and do need it alot, (yeah, I'm a noob too, but I've learned a lot the last few months :^o  )

---

### Post by wwwolf on 2005-05-05
[QUOTE=davefr]Editing files outside of Home, installing apps, configuring Control Panel settings.

I suppose I can get bye the way Kubuntu handles root access.  It's kind of a PIA but that's probably because I'm doing lots of initial setup/config/installs.
[/QUOTE]

You could just edit the sudo script. It's located at etc/init.d/sudo and it has the time limit set inside that file. You could set it to 20 hours or so if you wanted. Then you could run sudo commands and not be promted for the password for a very long time. 

HTH,

wwwolf

---

### Post by subhankar on 2005-05-05
In the console, type :-

sudo -s -H 

Then give your own password. You'll have a permanent root shell to do your configs :-)

Regards,
Subhankar

---

### Post by Zillion on 2005-05-05
oops wrong forum.. deleted my reaction

---

### Post by anon.irisX on 2005-05-07
[QUOTE=subhankar]In the console, type :-

sudo -s -H 

Then give your own password. You'll have a permanent root shell to do your configs :-)

Regards,
Subhankar[/QUOTE]
 I will try that thanks. :D

---

