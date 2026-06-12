---
title: "Cannot get past login. I think .ICEauthority, .Xauthority, and permission issue?"
date: 2014-02-07
forum: Desktop Environments
---

### Post by Dáire Fagan on 2014-02-07
Hi

Using the GUI for the user options I set my account so no password would be required on login. After doing this at boot I am not asked for a password and there is just a login button. Unfortunately when I pressed it white text on black appears for an instant and I am asked to login again. I was able to get passed the login screen last night after deleting .ICEauthority and then running sudo chown dusf:dusf ~/.Xauthority.

The same problem then occurred this morning and by mistake I not only deleted .ICEauthority but also .Xauthority after which I was still unable to login. I created a new user disf, which is able to login to X, and copied both files from there to /home/dusf but this made no difference. At one point I was following various suggestions and I think I may have messed up my /home and/or /home/dusf permissions. To try and correct this I ran a sudo chmod -R 755 /home and then a sudo chown dusf:dusf ~/.Xauthority.

I have also tired deleting .Xauthority which has been recommended to others but this also made no difference.

Trying to start X as root from recovery gives the error: error in locking authority file /root/.Xauthority. I cannot login to tty as root using my root password - same password works fine for sudo commands logged into tty as dusf.

The persmissions for /home are set to: drwxr-xr-x 6 root root 

The permissions for /home/dusf are set to: drwxr-xr-x 63 dusf dusf 

The permissions for /home/dusf/.Xauthority are set to: -rw------- 1 dusf dusf
 
The permissions for /home/dusf/.ICEauthority are set to: -rwxr-xr-x 1 root root 0

In /home/disf I can see the permissions for .Xauthority are set to -rwxr-xr-x  and .ICEauthority to -rwxr-xr-x. In /home/dusf I tried sudo chmod -rwxr-xr-x but it told me there was an input/output error although I was able to correct the .ICEauthority permissions - if it is even valid since I copied it from another users home dir.

Please advise?

As I could not set the permissions for /home/dusf/.Xauthority I deleted the file, and copied it over again from /home/disf. I then ran a sudo chown dusf:dusf ~/.Xauthority and it took the correct permissions. I rebooted but I still cannot get past login. I checked the permissions again and .ICEauthority had changed to something like -r--------. I deleted the file as I have booted before without it when there was a problem. I rebooted but I still cannot get past login.

I have also tried sudo xauth generate :0 .trusted but it gives the error 'No protocol specified. xauth: (argv):1: unable to open display ":0".

Can someone please help me with this?

---

### Post by Erik1984 on 2014-02-08
I don't know much about these files but if I do a quick Google search I've seen the suggestion to delete (or rename) the .Xauthority file. [s]If I understand correctly you have (accidentally) deleted the .ICEAuthority file but not the .Xauthority right?[/s] You could rename it to be safe (then you can put it back in case you ever need the old one):

If you are logged in as dusf (you can still do a TTY login right?)
```
mv ~/.Xauthority ~/.Xauthority_bak
```

**edit** You did delete Xauthority as it seems, you can still try to delete it again but I guess it won't do much.

btw is this you? [http://stackoverflow.com/questions/21610998/accidentally-deleted-iceauthority-and-xauthority-filesubuntu-12-10](http://stackoverflow.com/questions/21610998/accidentally-deleted-iceauthority-and-xauthority-filesubuntu-12-10) If you deleted more files it could be some other file causing the login trouble.

---

### Post by Dáire Fagan on 2014-02-11
> **Euroman said:**
> btw is this you? [http://stackoverflow.com/questions/21610998/accidentally-deleted-iceauthority-and-xauthority-filesubuntu-12-10](http://stackoverflow.com/questions/21610998/accidentally-deleted-iceauthority-and-xauthority-filesubuntu-12-10) If you deleted more files it could be some other file causing the login trouble.

No not me, it must be going around :)

> **Euroman said:**
> I don't know much about these files but if I do a quick Google search I've seen the suggestion to delete (or rename) the .Xauthority file. [s]If I understand correctly you have (accidentally) deleted the .ICEAuthority file but not the .Xauthority right?[/s] You could rename it to be safe (then you can put it back in case you ever need the old one):

If you are logged in as dusf (you can still do a TTY login right?)
```
mv ~/.Xauthority ~/.Xauthority_bak
```

**edit** You did delete Xauthority as it seems, you can still try to delete it again but I guess it won't do much.

Yes, and I think that may have been what is causing the problem in the first place. I would be happy enough at this point if I could just backup my home dir before reinstalling.

I logged in with the second account I created 'disf' and set it as an administrator. I was then apply to set my original account dusf to ask for a password - setting it to not ask for password seemed to cause the problem in the first place. Logged in as disf, and running thunar file manager as sudo I can access the dusf home dir but it now just shows two files, 'Access-Your-Privatew-Data.desktop' and README.txt. The README says to run just click on the other file or run encryptfs-mount-private but neither do anything. Trying to login top dusf as normal still brings the login screen up after I enter my password, and now when I log into a TTY as dusf and do ls -la I see the following:

Access-Your-Private-Data.desktop -> /usr/share/encrypts-utils/encrypts-mount-private.desktop
.cache
.encrypts -> /home/.encrypts/dusf/.encrypts
.Private -> /home/.encrypts/dusf/.Private
README.txt -> /usr/share/encrypts-utils/encrypts-mount-private.txt

There was no option mentioning encryption when I set dusf to ask for password.

I am trying to change dusf back to not asking for a password to see if it removes the encryption but the GUI button 'change...' is now not responding.

Can anybody help me out here? Like I said, I would be happy if I could just get access to backup the contents of my home dir.

---

### Post by felgro on 2014-02-11
Have a look at the latest Xorg.#.log in /var/logs/

---

### Post by Dáire Fagan on 2014-02-11
Thanks for the reply.

I have cat Xorg.5.log, what am I looking for exactly? Bottom of the log read 'Fatal server error: no screens found' if that helps...

---

### Post by felgro on 2014-02-12
> **dusf said:**
> Thanks for the reply.

I have cat Xorg.5.log, what am I looking for exactly? Bottom of the log read 'Fatal server error: no screens found' if that helps...

Ok, if it says that then I bet your /etc/X11/xorg.conf is full of bad information. Your symptoms are what I had to deal with recently trying to install to a [Dell system with a new Radeon card]("http://ubuntuforums.org/showthread.php?t=2204332"). Honestly, the best thing to do is probably gut xorg, fglrx and any proprietary drivers you have and rebuild them from scratch. Don't take my word for it - someone may offer some better advice I am unaware of. But it looks like you have trashed your entire display system to me.

---

### Post by Dáire Fagan on 2014-02-12
> **felgro said:**
> Ok, if it says that then I bet your /etc/X11/xorg.conf is full of bad information. Your symptoms are what I had to deal with recently trying to install to a [Dell system with a new Radeon card]("http://ubuntuforums.org/showthread.php?t=2204332"). Honestly, the best thing to do is probably gut xorg, fglrx and any proprietary drivers you have and rebuild them from scratch. Don't take my word for it - someone may offer some better advice I am unaware of. But it looks like you have trashed your entire display system to me.

Okay, well we are already having fish for dinner tonight so let's gut away!

Honestly, I just want to back up the 5GB or home partition before wiping and converting into Ubuntu server - I am happy once Xorg anyway long enough to establish that. Can you please advise on how to gut xorg and fglrx and any proprietary drivers I may have? I upgraded the old dell with a Radeon card.

---

### Post by felgro on 2014-02-13
> **dusf said:**
> Okay, well we are already having fish for dinner tonight so let's gut away!

Honestly, I just want to back up the 5GB or home partition before wiping and converting into Ubuntu server - I am happy once Xorg anyway long enough to establish that. Can you please advise on how to gut xorg and fglrx and any proprietary drivers I may have? I upgraded the old dell with a Radeon card.

Heh. This was all new to me a week ago - never had to deal with exploding display systems before, everything worked perfectly. Your best friend is google. Your second best friend is this Wiki -

[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide)

It covers all versions. Be prepared to get frustrated and to rebuild failed attempts. You need patience and diligence - there is no "right way". You need to deduce what will work for you. Sorry I can't be more specific. Took me a week of experimenting and tearing my hair out. But where there's a will there's a way. Critical - you MUST be able to access the 'net from your terminal environment.

---

### Post by felgro on 2014-02-13
What is your card btw?

---

