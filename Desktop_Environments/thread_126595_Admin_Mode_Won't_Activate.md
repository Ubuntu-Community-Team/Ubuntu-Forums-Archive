---
title: "Admin Mode Won't Activate"
date: 2006-02-06
forum: Desktop Environments
---

### Post by anmlcrckrs on 2006-02-06
I've got kubuntu installed and everything worked great with the live cd, but I can't get the administrator mode to stay on when I log into it from my account.  I'm looking to enable my two network interfaces, but it won't let me.  Any suggestions?

---

### Post by towsonu2003 on 2006-02-06
What do you mean by the Administrator Mode? Root (su)? Take a look at this: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) - any command that needs root privileges are run tru sudo command in ubuntu. The password is the password you gave to ubuntu during install. 

If not, what steps do you take in the "Administrator Mode" to enable your network interfaces?

---

### Post by Peter41az on 2006-02-07
first, go to system, then users and groups. check the box that says show all users and groups. then double click root. select "set password by hand" then type an admin password in there. click ok, then go back and try it. hopefully thats what you are looking for ;)

---

### Post by Jucato on 2006-02-07
I think he is experiencing one of the previous KDE 3.4.x bugs, where you activate Administrator Mode, enter your password, switch to Administrator mode, and then get thrown back to non-administrator mode after a few seconds. I think upgrading to KDE 3.5 will solve that.

---

### Post by anmlcrckrs on 2006-02-07
I've looked into updating KDE and from what I've gotten I need to have an internet connection for the Kubuntu downloads.  Can you give me some instructions on how to update KDE from a downloaded CD?

---

### Post by GeneralZod on 2006-02-07
[QUOTE=anmlcrckrs]I've looked into updating KDE and from what I've gotten I need to have an internet connection for the Kubuntu downloads.  Can you give me some instructions on how to update KDE from a downloaded CD?[/QUOTE]

It's really best to have your network working.  A workaround for the bug you are experiencing is to do

```

sudo kcontrol

```

from the command line.

---

### Post by Jucato on 2006-02-07
What kind of internet connection do you have? If it's a Broadband/Cable connection with a router/modem, you don't need to have your eth0 activated. just go to the terminal and type "sudo pppoeconf". I'm using a DSL connection ever since I installed Kubuntu, and my eth0 is still disabled. Though I find that a bit strange...

---

### Post by seakiwi on 2006-02-07
[QUOTE=Fenyx]I think he is experiencing one of the previous KDE 3.4.x bugs, where you activate Administrator Mode, enter your password, switch to Administrator mode, and then get thrown back to non-administrator mode after a few seconds. I think upgrading to KDE 3.5 will solve that.[/QUOTE]

The bug is still present in KDE 3.5 - I don't know if it's fixed in the latest version 3.5.1 as I haven't upgraded yet, but I sure hope so.

---

### Post by anmlcrckrs on 2006-02-07
Well, I've found a workaround.  Installing Ubuntu allowed me to use my ethernet connections.  Looks like it was the KDE issue,  hopefully when Dapper Drake comes out I can actually get it.  And I'll try and install the new one on this system now.  Thanks a bunch guys!

---

### Post by Peter41az on 2006-02-07
well now that i fully understand it is the same problem i was also plagued with at one time, It was the very bug that caused me to go back to Ubuntu and load Kubuntu-desktop on top of it. I tried every trick in the  book i could think of, including Sudo passwd -root , never could get it to work. I finally did a little digging and found out i wasnt the only fish in the ocean with that problem. I think it finally was rooted to a KDE problem as many here have speculated correctly. It was also doing it with 3.5. 
I did get my Averatec 12" laptop loaded back today.... Im amazed the wireless card worked right out of the box! Typing on it right now :)

---

### Post by Jucato on 2006-02-07
Is this really a bug? So I tried it again. Went to KControl > Internet & Network > Network Settings. Went into Administrator mode to enable eth0. then it went back to being disabled after a few seconds. At least it detects that I have an eth0. This is on Kubuntu. But regardless of my eth0 state, I'm still connected to the internet through it (DSL, broadband).

If I remember correctly, my Ubuntu Live CD and full install both detected and enabled by eth0. But in both cases, pppoeconf still worked perfectly, regardless of eth0 state.

I'm just guessing here, but this behavior might be due to how KDE and GNOME handle network devices in different ways. I'm not sure so I can't give a definite answer. All I'm sure is that in Kubuntu, I could connect to the internet even if eth0 is disabled. Just went to pppoeconf.

---

### Post by gonesolo on 2006-02-08
I had the same problem trying to activate my wireless card. in the end I went to bash and used iwconfig to configure the ESSID for my card and then ifup to activate the card. After a reboot it activated normally during boot up.

---

### Post by bbango on 2006-02-08
Im having similiar problems as many of you already are having.  i just recently installed the new version of kununtu on my laptop but i have no internet or network access.  my eth0 is deactivated and i can't go into administrator mode to activate it.  i click it and enter my password then it kicks me back out to normal user mode. 

also, i've tried entering in the sudo kcontrol and going to network there and when i click enable device (on my eth0), it enables for about 2 seconds then switches back to disabled.

when i do an ifconfig eth0, i do not even see an internal ip address.

Some of you have said that it is a bug in KDE.  can anyone verify this or is there a work around?!

please help, thanks!

---

### Post by Jucato on 2006-02-08
Are you trying to enable eth0 for broadband internet access? If yes, you could try this:
```
sudo pppoeconf
```
If I'm not mistaken (again this is just a guess), KDE only enables a network device if and only if it's actually connected to a network. I don't think it considers an internet connection as a type of network so it doesn't enable eth0 even if it's connected to the internet. Again, just my theory.

---

### Post by bbango on 2006-02-08
Ok - so I got home and my router/cable modem was turned off so i turned that back on and turned my laptop on and now my eth0 is enabled and i have an ip address.. which is good.  

but i still dont have internet access.  i tried the sudo pppoeconf but it said that it scanned my 1 interface (eth0) but the access concentrator of my provider did not respond.  hmm not sure?

---

### Post by bbango on 2006-02-08
ok,, i forgot i put a manual ip address in the configuration of device eth0.  and when i try to ping other computers on the network - host unreachable. so i do not believe my eth0 is really enabled.... although the kcontrol says it is.

---

### Post by bbango on 2006-02-09
yea im an idiot.... 

i didnt have my routers ip address under the routes tab....  this appears to have taken care of my situation ...

---

