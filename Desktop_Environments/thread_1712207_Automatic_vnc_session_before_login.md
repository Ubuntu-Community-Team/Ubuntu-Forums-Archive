---
title: "Automatic vnc session before login"
date: 2011-03-22
forum: Desktop Environments
---

### Post by warda on 2011-03-22
hi all,

I tried to find answer but they all scattered or I just not able to locate it. I'm sorry if  cross-posting and don't mind be directed to the thread already on the forums

I have Ubuntu 10.10 desktop downstairs (only powr cable and network)

and vista box upstairs.

I am able to remote to that ubuntu (am using tightvnc) but would like to be able to turn it off remotely (which I can) but then to be able to login into it with no need  of disconnecting screen and keyboards from vista and dragging it down to first login locally...

is it possible to have vnc session to running ubutu box with no user logged in as you get in windows?

I've seen similar posts but not like defined step-by-step answer how to..

 thanks a lots guys

---

### Post by Krytarik on 2011-03-22
It's just a wild guess, but how about running "x11vnc" through GDM's startup script, like described for xrandr here:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

or placing a launcher into "/usr/share/gdm/autostart/LoginWindow"?

[https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

---

### Post by warda on 2011-03-22
hi Krytarik,

thanks for reply - will try suggestions soon and will see how it'll go..

---

### Post by warda on 2011-03-22
> **Krytarik said:**
> 

or placing a launcher into "/usr/share/gdm/autostart/LoginWindow"?

[https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

Hi I just follow this steps. I installed x11vnc successfully on ubuntu but when trying to login using vnc viwer get error message:

**unable to connect to host: connection refused (10061)**
??
how can i correct it?

cheers

---

### Post by Krytarik on 2011-03-22
Are you sure that x11vnc is running at the login screen?

You should test the same setup within a running session before.

---

### Post by warda on 2011-03-24
hi yes i was sure.

I decided to do it a new again

I reinstalled ubuntu 10.10.

I follow steps from [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941)
on the step 3. when you required to put the code on the end of  **/etc/inetd.conf  **I think starts the 1st problem. my comand create new file rather then editing existing - inetd.conf is not existing

so I create that file with the code in side

and then try to run
**sudo /etc/init.d/inetd restart**

but get message

sudo: /etc/init.d/inetd: command not found


sorry - but as am not professional and only enthusiast of ubuntu can do only as much as follow steps :(
but they DON'T work for me...

so my question is still open: can you remote to ubuntu 10.10 from windows machine after the ubuntu was rebooted and no user is logged in yet? without using Internet connection or services like team viewer?

thanks!

---

### Post by Krytarik on 2011-03-24
You are following a 6-year-old guide?!

You should put the x11vnc command into the startup script, like I said before.

Just yesterday I noticed this post, it advises to put the command at the end of those script:
[http://ubuntuforums.org/showthread.php?p=10172825](http://ubuntuforums.org/showthread.php?p=10172825)

But it is really neither necessary to include x11vnc into the boot process, nor would it work that way.

---

### Post by warda on 2011-03-28
> **Krytarik said:**
> You are following a 6-year-old guide?!



ooups!

havant relised it's that old !!lol!

I will give a try with script once I get my hands back to it and will post update

thanks!

---

### Post by asmoore82 on 2011-03-28
Check out the "headless" howto in my signature!

The box I wrote that on is still chugging along nicely at work -
We use it everyday with SSH, VNC and RDP!

---

### Post by warda on 2011-03-28
hi asmoore82, thanks for joining in..
i got to the point where I need to start vnc service with the comand
 ***sudo start vnc-myuser***

but I get message: ***start: Job failed to start***

when I try restart instead it goes: ***restart: Unknown instance:***

so still no luck..

---

### Post by warda on 2011-03-31
hi just quick update

I got it finally working following howto guide but have problem

I am connecting from my vista using microsoft rdp which connects but my remote desktop is just grey - no icons or menus at all

---

