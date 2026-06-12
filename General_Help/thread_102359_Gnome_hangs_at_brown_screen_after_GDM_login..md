---
title: "Gnome hangs at brown screen after GDM login."
date: 2005-12-11
forum: General Help
---

### Post by senectus on 2005-12-11
***Solved***
It seems it was something to do with my audio setup, I took my user out of the audio group and logged in and it works!. Now to find out _why_ it broke.
Another breakthrough.. I logged back in while _in_ the audio group, the system locked up again, so I went to ctrl-alt-F1 and did a killall -9 esd, all of a sudden I get logged into Gnome!!

so now I do a "esd" from the command line and I get:
```
:~$ esd
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

```
So it looks esd related, and Gnome didn't like me changing my sound card along withe the main board.
Oddly enough I still get sound from GDM, just not inside gnome...



On the weekend I had my PC burn out it's CPU/main-board.. so I zipped out and bought a new pair to install.
After installing I found that when I log into GDM it starts up gnome with a brown screen, I get no splash screen pop up, no icons, no panels and no right click. I can move my mouse around I can still ctrl alt f1 etc.

I spent a huge amount of time trying to fix it but got no where.
I created a new user and logged in as that user and it all worked perfectly... (so I'm now using that user and trying to pull the FireFox/evolution/cedega profile stuff over).

I've had a huge amount of advice from the Ubuntu and the Gnome community (thanks) but it's all for naught :-(

Things I've done.
[LIST=1]
[*]Deleted everything (hidden included) from the /tmp/ directory
[*]Renamed my home directory, created a new one and gave it the correct permissions
[*]Reinstalled video driver
[*]Installed NEW video driver
[*]Used alternative video driver
[*]dpkg-reconfigure gdm
[*]dpkg-reconfigure xserver-xorg
[/LIST]

It _must_ be something to do with my original user profile because it's limited to that user.
one more thing I've noticed is that the PC's sound card (now an on-board AC97 instead of the old SBLive I was using) seems to be no longer working.. would "esd" maybe cause problems with my old login?

Any other idea's?

---

### Post by 23meg on 2005-12-11
What's your video hardware? Which drivers did you try using? If the user isn't a member of the "video" group, try adding it there.

---

### Post by senectus on 2005-12-11
Nvidia GForce FX6600GT with the standard ubuntu nVidia drivers/Vesa drivers/latest nVidia drivers off the web.

interestingly enough, the _old_ account _is_ a member of the group video, but the _new_ account that works _isn't_ a member of that group.. :confused:

---

### Post by 23meg on 2005-12-11
If you ever downloaded drivers from the repos, remove nvidia-glx, the linux-restricted-modules package, do "sudo rm /etc/init.d/nvidia-*", look at the "installed files" for the nvidia-glx package in Synaptic and remove them by hand one by one, and reinstall the drivers with the official installer.

---

### Post by senectus on 2005-12-11
this problem occurred before I had updated the video drivers.. It went from a working system to a non working system with no changed other than the removal of the PCI sound card and the addition of a new main-board and CPU.
Same video card as before, no new drivers.
Besides.. surely if it's going to be video drivers it'll be broken for _all_ users that log in not just my old account??

---

### Post by Nope on 2005-12-12
I had this exact problem with my GF6200, the way to fix it is when Ubuntu starts boot into recovery mode “or safe mode, whatever it's called” which will bring you into the console. You should be familiar with VIM.
Type “cd /etc/X11”
Then “sudo vim xorg.conf”
scroll down to the Driver section and change “nv” to “vesa”
save changes and exit
type exit in the console to brin you back inti X.
maybe somebody can explain it better than I can, but that's how it's fixed.

---

### Post by senectus on 2005-12-12
Sorry mate but as I've already said in the first post, I've already tried the vesa driver. It did not work.
Besides that it's not logical for that to be the case for one user but not for the other. the video driver is a constant. If it doesn't work for one it's not going to work for either.

---

### Post by bb002 on 2005-12-12
After replacing the motherboard and cpu did you reinstall Ubuntu?

I noticed that when ever I had to reinstall Ubuntu (I'm a noob and screw up my config pretty bad. Like a moron I didn't make a back up first.) and I preserved the /home directory, that I had to chown the folders in /home back to their proper owners. I'm say this because you said you checked permissions but nothing about ownership. As far as I know permissions don't mean jack if the ownership is wrong. Try reowning your home directory with "sudo chown -R username:groupname /home/mydir". Ubuntu usually make your groupname the same as your username. After reown your home dir see it everything works.

---

### Post by senectus on 2005-12-12
no, no reinstall required (this is Linux after all :-) ).
But in answer to the real question, I've been very careful to check permissions fully and that includes ownerships, also when I created the new home directory I left it empty.. so there was _nothing_ (not even .files) in it before I restarted GDM/X and after there was only the usual .files that gnome creates on it's first time firing up.

---

### Post by senectus on 2005-12-12
the thing that stumps me is that anything that is unique to the user is in /tmp/ and /home/userdir/ and after i blow those away and clean them out completely everything _should_ go back to normal. 
but the problem remains.. 
If I log in as another user there is no problem.

It's aggravating.

---

### Post by RAOF on 2005-12-12
Since your new user works fine, it **has** to be something in your configuration files.  Maybe when your computer danced the electric cha-cha, one of the gnome config files got zapped?  Either keep working with your new user, or you could selectively rename the .config directories in your old user and see which one allows you to login properly.  I'd be guessing it'd be one of: .metacity
.gnome2
.gnome2_private
.gnome
.gconf

---

### Post by senectus on 2005-12-12
But I'm zapping _all_ of those files and allowing Gnome to recreate them the next time I log in.
It doesn't fix the problem.. 
bizarre isn't it? :confused:

---

### Post by RAOF on 2005-12-12
Yes.  Really bizzare.

Well, at least the new user works :???:

---

### Post by fannymites on 2005-12-12
*Deleted*  Misread the first post.

---

### Post by senectus on 2005-12-13
[QUOTE=RAOF]Yes.  Really bizarre.

Well, at least the new user works :???:[/QUOTE]

well yes technically it works, but I'm having a hell of a time pulling stuff from my old profile over..
Stuff like cedega, firefox and evolution appear very finicky about doing things like that.
It's proving to be a pain in the fat cheeks.
I just wish i could go back to my old login :-(

---

### Post by bb002 on 2005-12-13
Try removing the "broken" user from the "audio" (think that's the right name) group and seeing what happens. Then try readding it and seeing what happens.
If I read your posts correctly you are using a new audio device and the new user was created after you started using the new audio card.

If the above doesn't work try renaming the broken users home directory then deleting the broken user and recreating it. After that I would like to inform you that i'm stumped...

---

### Post by senectus on 2005-12-13
[QUOTE=bb002]Try removing the "broken" user from the "audio" (think that's the right name) group and seeing what happens. Then try readding it and seeing what happens.
If I read your posts correctly you are using a new audio device and the new user was created after you started using the new audio card.

If the above doesn't work try renaming the broken users home directory then deleting the broken user and recreating it. After that I would like to inform you that i'm stumped...[/QUOTE]

lol thanks :-)
Some good (and new!!) suggestions for me.. I'll try them as soon as I go home tonight!

---

### Post by bb002 on 2005-12-13
Well...I actually do have another idea but it'll probably be shot down...reinstall anyone? :D

---

### Post by senectus on 2005-12-13
I _really_ don't want to do that.. so *bang bang* :-) 

Any idea how to make VNC work on GDM.. I may be able to fix it from work ;-)

---

### Post by bb002 on 2005-12-13
Try this: [http://ubuntuforums.org/showthread.php?t=76638](http://ubuntuforums.org/showthread.php?t=76638)
I haven't done this myself, thought about it though, so I don't know if there are any security risks involved. I know nothing about XDMCP. Like I'd be able to spot a security risk anyhow...

---

### Post by bb002 on 2005-12-13
Think I thought of one. I don't know if vnc traffic is encrypted. Or if this setup will even ask you for a password.

---

### Post by senectus on 2005-12-13
[QUOTE=bb002]Try this: [http://ubuntuforums.org/showthread.php?t=76638](http://ubuntuforums.org/showthread.php?t=76638)
I haven't done this myself, thought about it though, so I don't know if there are any security risks involved. I know nothing about XDMCP. Like I'd be able to spot a security risk anyhow...[/QUOTE]

Excellent.. now if I just hadn't logged out of gnome via VNC 5 min's ago...
:rolleyes: 

anyone know if you can turn on XDMCP from the cmd line? :eek:

---

### Post by bb002 on 2005-12-13
Well I know that you can add "-X" to ssh to forward X applications, though it can be pretty slow at times. So be patient. I often use this method which is why i haven't done the vnc to gdm method. It maybe slower but I know for a fact it is encypted.
BTY using ssh to forward X applications requires you to be using an X server. Meaning no windows. dunno about mac, it is *nix based so it may work, I wouldn't bet on it though. I've seen references to a X-Win32 that allows running of X apps on windows but I've never found a download link.

So the command would be "ssh -X user@machine" once you log into your machine you can run "gksudo gdmsetup" which is the launcher for "System -> Administration -> Login Screen Setup"

Also you can add an ampersand ("&") to the end of any command to background it so you can have more than one x app running at once but you can't do it to a sudo type command if you get asked for a password. It will act like you terminated the command. Enjoy!

Well it is 01:00AM here well past my bedtime. Besides I think I've helped you avoid your work duties(or whatever it is you are supposed to be doing) enough already. :D

[edit]
Found some typos i missed when i previewed...

---

### Post by senectus on 2005-12-13
heheh yes, you have thanks.. maybe i should get back to work :D

---

### Post by senectus on 2005-12-13
[QUOTE=bb002]Try removing the "broken" user from the "audio" (think that's the right name) group and seeing what happens. Then try readding it and seeing what happens.
If I read your posts correctly you are using a new audio device and the new user was created after you started using the new audio card.

If the above doesn't work try renaming the broken users home directory then deleting the broken user and recreating it. After that I would like to inform you that i'm stumped...[/QUOTE]

You little ripper :-)
I've removed my user from that group and I can now log into my normal user account!!

bloody amazing :-) thanks!

---

### Post by bb002 on 2005-12-13
Well alright and to think that was wild guess of which dark corner to take a potshot at. :) Wish I had this kind of luck with women, I have a rather large supply of it.

Does your account go back to not working if you re-add your account to the audio group?

---

### Post by senectus on 2005-12-13
No it goes back to being broken, I've also found that when it's broken if I do a killall -9 esd my gnome session that has hung will suddenly start working.

another strange note.
I have working sound in GDM, but no working sound when _any_ other user logs in.

any idea how to force esd to reconfigure for my new soundcard?

---

### Post by markajharrison on 2005-12-17
Hey 23meg, whats the "official installer" you refer to ....

quote..

If you ever downloaded drivers from the repos, remove nvidia-glx, the linux-restricted-modules package, do "sudo rm /etc/init.d/nvidia-*", look at the "installed files" for the nvidia-glx package in Synaptic and remove them by hand one by one, and reinstall the drivers with the official installer.

---

### Post by senectus on 2005-12-17
[QUOTE=markajharrison]Hey 23meg, whats the "official installer" you refer to ....

quote..

If you ever downloaded drivers from the repos, remove nvidia-glx, the linux-restricted-modules package, do "sudo rm /etc/init.d/nvidia-*", look at the "installed files" for the nvidia-glx package in Synaptic and remove them by hand one by one, and reinstall the drivers with the official installer.[/QUOTE]

He means the package you download directly from nVidia...

---

### Post by bb002 on 2006-01-09
Ooops...Seems he started a new thread....I moved my post to there.

---

### Post by key134 on 2006-12-08
I don't understand how this is solved =/

I have the same problem where I changed my soundcard and now esd hangs on loing.  I don't know how to fix it other than killing esd, but I figured that out myself.  Is there are fix, or do you just do the same workaround that I do?

Keith

---

