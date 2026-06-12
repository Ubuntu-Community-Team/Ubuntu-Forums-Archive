---
title: "Ack! Strange problem connecting to internet"
date: 2005-10-29
forum: Desktop Environments
---

### Post by linuxlizard on 2005-10-29
Hey all,
I set up a computer for my folks at my house. I have cable modem here, so I installed ubuntu and updated and tweaked and installed all the packages and stuff they would need here. They only have dial-up. I am in the process of ending my dialup ISP, but still have access for a few weeks, so I went ahead and set up gnome-ppp here, and tested by dialing my account and surfing for a while. Went to my folks house, opened gnome-ppp, changed the log in name, password and telephone number to the ones needed by my folks for their ISP, and then the thing farted. It dials, logs in, connects but then disconnects a few seconds later. If I get firefox running faster than it disconnects, firefox cannot access the internet for those few seconds it is connected.  I checked the log and it complained about permission to access a couple of files- sorry can't remember the names and I left the computer at my folks. So I then tried changing the permissions on those two files so my mom's account had write permission and tried again, the log then complained about something else, said something would be flaky, told me "I guess that's it for now, folks" or soemthing similar and gnome ppp hung up again like before. So, I changed back to my ISP info and it logged on and acted normally. I tried uninstalling completely and reinstalling gnome-ppp from their house, but I don't believe it really completely uninstalled and removed the files because when I reinstalled it still had the logon, password and phone number.

So basically the problem behavior ubuntu is giving me is this- gnome-ppp will log onto my ISP no problem. Gnome-ppp will not stay connected to my folks ISP. It logs on and the ISP accepts it. It seems to be a permissions problem on the ubuntu machine.

Can anyone offer any advice? unfortunately I can't get to the log file until I visit again (about an hour away). Meanwhile they are using my ISP.

Thanks!

---

### Post by jimbob on 2005-10-29
I think my problem is the same.  There is something aboutthe line that is causing it but I don't know what.

Check my post: [http://www.ubuntuforums.org/showthread.php?t=81557](http://www.ubuntuforums.org/showthread.php?t=81557)

---

### Post by linuxlizard on 2005-10-31
hmmm, yeah could be...

I guess difference I see is that the same machine has no problem when it connects with my isp, only when I change it to theirs. So ubuntu actually working right, just seems to have some sort of problem giving permissions when logging on with their user name to their isp.

I forgot to mention also, that I can get it to work just fine with their ISP if I go to system-administration-networking and make it dial and connect through that. When that is done, though, you have to be in root (I guess, it asks for the password when you start up networking). My folks are in their 70s and there is small chance I can get my mom to go through all the steps necessary to connect that way. She surfs the web and checks her e-mail, but it's sort of a small miracle because I can't get her to understand the difference between logging on to ubuntu, logging on to their ISP and logging on to yahoo (the ISP is really my dad's from work, and she uses yahoo mail). She gets confused about what is the internet, what is her webmail and what is her computer- it's all sort of the same thing to her. Occasionally she doesn't use her word processor because she forgets it doesn't tie up the phone line. See what I mean? I've elimated a lot of the problem by autologging her into ubuntu and sticking a big icon of a telephone on her desktop which dials and connects her to the internet when she clicks on it. So I just don't se her using networking to get on. 

But maybe the fact that I can use their networking app to connect to their ISP, but gnome-ppp will allow me to connect with my account but not theirs, and the fact that when I had the computer connected to the internet through my cable modem when it was at my house setting up ubuntu will all give someone clues about what the problem is. gnome-ppp dials, connects, accepts their password, etc. It just hangs up again a few seconds later.

Anyone? I really need help with this, any help much appreciated! My dialup ISP, which they are temporarily using, is being disconnected soon since I got cable, so the temporary solution of having them use my dialup will soon come to an end. I need to get this problem fixed. The only other solution I've come up with is to reinstall their ubuntu from scratch at their place and do all the updates from dialup. I spent quite a while setting their machine up and all the updates on dialup, and tweaking their machine again so multimedia works, reinstalling the printer driver, nvidia, speeding up the drives, and about 20 other little tweaks would take me a month at least going to their place for a few hours once a week. Obviously I really want to avoid doing that.

---

### Post by Dria on 2005-11-04
IMHO, the problem is here:
[... gnome-ppp dials, connects, accepts their password, etc. It just hangs up again a few seconds later.]

I'm having a LOT of problem letting Gnome-PPP understanding that my ISP uses CHAP authentication, and your situation looks the same.
The only thing I've managed to do until yesterday night is logging in manually, following instructions found on [http://www.theory.physics.ubc.ca/ppp-linux.html]("http://www.theory.physics.ubc.ca/ppp-linux.html").

At least you can find out if CHAP authentication is really your problem.

Ciao,
        dria.

---

### Post by linuxlizard on 2005-11-04
Thank you for your response :D 

Do you or anyone else know if there's a file that gnome-ppp uses that could be edited to force it to use CHAP?

---

### Post by Randux on 2006-02-01
Hey Lizard, if you are able to get to your ISP from a cable modem, can you please tell me how I can specify the ISP's ip address, and my userid/password?  I can get to my cable provider's homepage, but I can't get them to gateway me to my ISP.

Thanks,
Rand

---

### Post by Hereford on 2006-02-02
FWIW, my ISP identifies a PPP connection by requiring a capitol 'P' in front of my normal login ID for connection.  I keep forgetting this since I only set this up when changing computers or OSs.  When I brought up Ubuntu, I breezed through the setup stuff and had the same problem.  Your parents' ISP might have some similar gadget that is as easily overlooked as this.

---

