---
title: "Remote Assistance (not Remote Desktop)"
date: 2009-06-20
forum: Desktop Environments
---

### Post by fermulator on 2009-06-20
Hi there,

Does anyone know if there's a similar product for Ubuntu like the "Windows XP Remote Assistance"? (See [http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/remoteassist/intro.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/remoteassist/intro.mspx) for additional details if you don't know what I'm talking about)

Indeed, there are many "remote desktop" solutions for Linux in general such as VNC, VINO, and NX, but there doesn't appear to be an easy solution for "Remote Assistance".

Consider:  User Alice is a Ubuntu newbie.  Her friend Bob has configured her computer for Ubuntu to try, to help make the world a better place.  For security purposes, Bob doesn't want to simply enable VINO remote desktop or else Alice's computer would always be exposed to the Internet.

How can Alice (in a nice and easy way), send her Bob a "Remote Assistance" invitation?  What could this entail?
 1. Alice goes "System --> Help and Support"
 2. Within the Ubuntu Help Center, Alice should be able to click "Ask for Remote Assistance" (by means of e-mail, file, etc.)
 3. In doing so, Alice's computer would automatically enable VINO (or some other means of assistance) for a limited time period (configurable by Alice if she so desired).
 4. Once Bob received said request he can easily connect to Alice's computer to provide GUI assistance.  Bob MUST be able to see and control Alice's screen at the same time as Alice.  Future enhancements would include the already included on Windows "text box", "webcam", or "microphone"....

I've found a few tidbits here and there on the Internet, but not really useful I don't think:
 * [https://blueprints.launchpad.net/ubuntu/+spec/remote-assistance-in-help/](https://blueprints.launchpad.net/ubuntu/+spec/remote-assistance-in-help/)
 * [http://bitsofclever.com/node/3](http://bitsofclever.com/node/3)

Any tips?

---

### Post by fermulator on 2009-10-06
"le bump"

---

### Post by wah fun on 2009-10-28
Yes! Yes! I am a linux newbie and am frustrated with trying to setup rdesktop in order to provide remote assistance to an XP user that does not have a static ip. I am afraid my doze roots are showing but this is one feature that windows does very well and a similar capability in linux would be very helpful.

I have googled for hours and have found nothing very helpful, so if you have found a solution, would you please post it?

thx

---

### Post by bhaverkamp on 2009-10-28
I did this for my Dad. What I ended up doing was setting up SSH port forwarding on his router with port obfuscation. Mostly I just ssh into his box when required. On occasion when he is confused by something on desktop I VNC in. I find this easier than the XP way which required him to constantly send me invites.

---

### Post by fermulator on 2009-10-28
> **wah fun said:**
> Yes! Yes! I am a linux newbie and am frustrated with trying to setup rdesktop in order to provide remote assistance to an XP user that does not have a static ip. I am afraid my doze roots are showing but this is one feature that windows does very well and a similar capability in linux would be very helpful.

I have googled for hours and have found nothing very helpful, so if you have found a solution, would you please post it?

thx

wah fun: What you're asking for is not the purpose of this thread.  From your post, I'm understanding that you are running Ubuntu, and there is a remote user you wish to provide desktop support to whom is running Windows XP.  Indeed, ubuntu is unable to accept a "remote assistance invitation" from Windows.  This is quite frustrating.  My solution is having a VMWare XP machine ready to accept the invitation ... not ideal ... but it works.

The purpose of this thread is to address the issue that given two users ExpertUser and NoviceUser, they are both running Ubuntu.  NotiveUser has no "simple way" to request remote assistance from Expertuser.

---

### Post by mbeierl on 2009-11-25
I'm going to add myself as a "me too" to this thread.  It appears that this is not currently possible, but it's always worth bumping just in case...

---

### Post by fermulator on 2009-11-26
> **bhaverkamp said:**
> I did this for my Dad. What I ended up doing was setting up SSH port forwarding on his router with port obfuscation. Mostly I just ssh into his box when required. On occasion when he is confused by something on desktop I VNC in. I find this easier than the XP way which required him to constantly send me invites.

bhaverkamp: So you  must have forwarded the VNC port also yes?  Isn't it risky to always have that port forwarded and exposed?  
I was under the impression that VNC is very unsecure because its extremely easy to hack into?

---

### Post by Grenage on 2009-11-26
I distrust VNC, it has frequently discovered security issues.  If I were to configure remote GUI access, I would use NX; it's very secure (SSH) and very fast.

---

### Post by rocketsbay on 2010-07-17
You can try Yuuguu.

[http://www.yuuguu.com/download/linux-update-site](http://www.yuuguu.com/download/linux-update-site)

and for the key:

[http://getsatisfaction.com/yuuguu/topics/apt_signing_key](http://getsatisfaction.com/yuuguu/topics/apt_signing_key)

---

### Post by mgmiller on 2010-07-17
Install gitso from the good folks at google.  There are versions for windows mac and linux, easily installed from a .deb  It makes remote support almost trivially easy.

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by mbeierl on 2010-07-20
I was pointed to TeamViewer a few weeks back and wondered how I could have missed it in my quest for decent remote assistance.  It also works well for screen sharing for demos or presentations.

[http://www.teamviewer.com](http://www.teamviewer.com)

[edit]I should also mention that it can work behind a firewall or NAT too.

---

### Post by Johann-1.0 on 2010-08-21
I agree with Fermulator. Why there isn't an easy way to give remote assistance to a Windows or Linux computer?
I really don't understand how this can be so easy between Windows computers and so difficult even between Ubuntu Users.
I don't remember I have to set the router thing and all that stuff to make remote assistance possible in Windows.
There should be a way to give remote assistance, between Linux users and between Linux and Windows computers in an easy way; maybe as reverse connection.
My girlfriend is crying out loud for assistance...I convinced her to switch to Ubuntu...but now it is difficult to me to give her assistance as I used to do when I used Windows. 
I love Linux...but I think developers should try to add an application to do that. I have a lot of hours reading posts...and when finally find a solution, it is not possible to me to implement it because I'm not able to configure the router, because I'm not the owner.
Well, thank you for reading. If it sounds a little tough, please excuse me. My english skills maybe are note good enough.

---

### Post by Johann-1.0 on 2010-08-21
Please, vote for solution number 3 in this post. Tell others to vote too.
[http://brainstorm.ubuntu.com/idea/20116/](http://brainstorm.ubuntu.com/idea/20116/)

---

### Post by Johann-1.0 on 2010-08-21
[[IMG]http://brainstorm.ubuntu.com/idea/20116/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20116/)

---

### Post by mgmiller on 2010-08-21
I should mention this one again.  I use it to remote assist between Ubuntu machines and Ubuntu and Windows machines behind NATed routers and it is trivially easy for the person requesting help to use.  It is also very easy for the person offering the help to set up, but does require a knowledge of your router to open a port in it so you can give assistance.  For the person requesting, because it is a reverse connection, there is no set up at all.

The attached thumbnail image shows the interface that both parties see.  It doesn't get much easier then this.

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by Johann-1.0 on 2010-08-22
I used Teamviewer...No router configuration, no specific knowledge, etc...just connect and is ready. Why not to have a similar tool for Linux?
If it could be easier, why do it harder?

---

