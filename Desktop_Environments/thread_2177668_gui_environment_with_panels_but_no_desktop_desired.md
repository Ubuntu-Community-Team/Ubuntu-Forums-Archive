---
title: "gui environment with panels but no desktop desired. Stop pcmanfm drawing desktop, ?"
date: 2013-09-29
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2013-09-29
Lubuntu, Raring, 32 bit. I have thunar set up to open automatically in ~/Desktop. I can't really see any reason to display the Desktop folder differently from other folders. On those occasions when I actually use the Desktop I find it easier to open it in my regular file manager (for now, that's thunar) in the details view anyway. So I thought maybe I could save some system resources by not drawing a conventional desktop at all. I tried taking out the "--desktop" option after pcmanfm in 
/etc/xdg/lxsession/Lubuntu/autostart and later tried replacing it with “–-no-desktop”. Neither seemed to have any effect. I tried unistalling pcmanfm altogether. Bad idea. It took the rest of lubuntu with it leaving me with the choices of untweaked openbox or untweaked lxde. I reinstalled lubuntu desktop environment. Now I'm back to square zero. I'm wondering if perhaps I need to specify thunar as my default file manager somewhere in a config file and somehow tell IT not to draw the desktop.

Any suggestions?

---

### Post by vasa1 on 2013-09-29
Check out [http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how](http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how) and also think about plain Openbox. I wrote a little about it here: [http://ubuntuforums.org/showthread.php?t=2173126&p=12787508#post12787508](http://ubuntuforums.org/showthread.php?t=2173126&p=12787508#post12787508)

I don't use any "desktop" now, and have Thunar as my file manager and lxpanel for a few essentials.

---

### Post by Dreamer Fithp Apprentice on 2013-10-01
Thanks much, Vasa1! That's a very good post of yours you linked to. I am tinkering with openbox and several other light weight window managers so that will be quite helpfull. I won't mark this solved until I've got everything working but I think you've pointed the way.

---

### Post by Dreamer Fithp Apprentice on 2013-10-02
Thanks again, Vasa1. I went with the "the simple way" from your first link, [http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how](http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how) , putting a script called pcmanfm, containing```
#!/bin/sh
thunar $* &
```in /usr/local/bin. This works. I assume it works  because at some time in the login process something issues a command  that tells pcmanfm by name to manage the desktop and in checking the  path the script is found before the real pcmanfm and so the command is  given to thunar instead. Presumably the syntax is meaningless to thunar  so thunar doesn't start managing a desktop. I do have some new error  messages that pop up in a script I have running at login that may be a  result of thunar complaining about arguments it doesn't know what to do  with. I wondered if perhaps this was starting some sort of invisible  instance of thunar which might defeat the purpose of saving whatever  resources managing the desktop costs but I looked at lxtask after loggin  in and I didin't see thunar so I presume thunar just said "I don't know  what you're talking about," and went back to sleep. I will experiment a  bit with that script file to see if I can understand what is happening  better and if I gain any insight I will post it. Or perhaps someone will  comment.

Anyway, this change gives the desired behaviour. I can boot with  Lubuntu, LXDE, or plain Openbox and in either case my desktop is plain  wallpaper and nothing seems broken.

As for the your second link, on migrating to using plain Openbox instead  of Lubuntu or LXDE, that has been something I've intended to try for a  while. If I had realised how easy it was to run the lxpanel without even  having to set it up again in plain openbox I'd have gotten to it  sooner. For explaining how you did that I am much in your debt. I'm about halfway through following your procedures from that link. I've  also installed some of the other ultra-light-weights - wm2, dwm, JWM,  i3, and blackbox - all of which I plan to experiment with.

---

### Post by vasa1 on 2013-10-02
> **Dreamer Fithp Apprentice said:**
> .... I've  also installed some of the other ultra-light-weights - wm2, dwm, JWM,  i3, and blackbox - all of which I plan to experiment with.
You're braver than I am :)

But I'm very happy with Openbox because lubuntu-rc.xml (or just rc.xml in plain Openbox) lets me customize things --- keyboard shortcuts, window snapping, application-specific window sizes and placement, etc.

---

### Post by Dreamer Fithp Apprentice on 2013-10-02
I think I found a better way.  Using the script that was sending pcmanfm commands to thunar instead was causing 2 error messages in a script I run at startup in Lubuntu sessions. When I logged in with plain Openbox I got several error messages in multiple xenity-style boxes, at least one of which referred to thunar. All of which was tolerable, but . . . 

I was on the right track earlier in looking at the "@pcmanfm . . ." line in /etc/xdg/lxsession/Lubuntu/autostart but instead of modifying it I should have simply deleted the whole line. I did that and deleted the pcmanfm script and it works with no error messages in lubuntu and now only one in openbox. 

It seems surprising to me that this worked for both Lubuntu and Openbox sessions. I would have expected to have to make a similar change in /etc/xdg/openbox/autostart (there was no /etc/xdg/lxsession/Openbox/autostart) but that file had no such line to delete and was in a different format, looking more like a bash script and was ENTIRELY commented out.

I think the other way was causing the command to pcmanfm to wake up and manage the desktop to be sent to thunar instead at which point it failed because thunar's syntax isn't the same as pcmanfm's. So essentially it was a happy accident that it worked and a roundabout way of doing things. This way I think the command is not issued at all.

---

### Post by vasa1 on 2013-10-02
> **Dreamer Fithp Apprentice said:**
> I think I found a better way.  Using the script that was sending pcmanfm commands to thunar instead was causing 2 error messages in a script I run at startup in Lubuntu sessions. When I logged in with plain Openbox I got several error messages in multiple xenity-style boxes, at least one of which referred to thunar. All of which was tolerable, but . . . ....
I **forgot** to mention that the option I chose from the askubuntu answer I linked to was the second one, the lxde-xfce hybrid one :(

Anyway, if you've got thing going well for you, that's what counts.

---

