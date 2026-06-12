---
title: "custom runlevel for fluxbox"
date: 2008-07-13
forum: Desktop Environments
---

### Post by frj on 2008-07-13
Hi,

Iam not sure if this is the most appropiate part of the forum, but in the end what it is about is desktop environments.

I would like to create a new runlevel that does not start gdm. Instead i would like it to start fluxbox. I have done some research on how to do this and it seems as since the introduction of Upstart it is not as easy as i hope. But maybe my solution would work anyway, i also have some question marks about my plan. 

Is it possible to just remove some of the symlinks from /etc/rc4.d/, like gdm and maybe some other services that i do not want. Does not seem like update-rc.d can disable/enable scripts for a specific runlevel? 

Then instead of a script that start gdm i am thinking of one that just startx. Then have fluxbox set as default. 

I do not think that the above would be a problem? But in order to login in runlevel 4 i would have to enter my username and password at tty. Is it possible to auto-login as some user? Possible to pass credentials via grub or spawn fluxbox from a loginscript as a specific user. 

I know that the idea with auto-login might sound crazy. The reason why i would like to autostart fluxbox without any kind of login on runlevel 4 is because i sometimes use my desktop as a media center connected to my projector. 

The alternative would be to login as a seperate user in gdm and have fluxbox started. But i would like to be able to choose desktop-mode or media-mode in grub. 

Any input on how or if this can be done is appreciated. Comments on my suggestion, if possible, is most welcome.

Frj

---

