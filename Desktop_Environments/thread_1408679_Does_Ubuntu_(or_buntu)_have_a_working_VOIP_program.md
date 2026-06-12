---
title: "Does Ubuntu (or *buntu) have a working VOIP program?"
date: 2010-02-16
forum: Desktop Environments
---

### Post by VanillaMozilla on 2010-02-16
And if not, should this be reported as a major bug?

I've spent days on Ekiga, and I can't get it working.  It works about half the time with the Diamondcard echo number, and now it works rarely with the [email]500@ekiga.net[/email].  There is a new version that may or may not work, but I couldn't get it installed from the PPA (apparently libraries haven't been upgraded).  For now it's not worth the trouble.

I've tried a couple of others.  Empathy is supposed to be the replacement for Ekiga, but it doesn't do SIP out of the box.  Pidgin, likewise, I think.  I tried Twinkle, with similar symptoms to Ekiga.  I've tinkered with a couple of others, but some of them can barely even start up and terminate, much less make a phone call.

This is the pits.  Can anyone tell me there's something that actually works?

---

### Post by Megafag on 2010-02-16
> **VanillaMozilla said:**
> And if not, should this be reported as a major bug?

I've spent days on Ekiga, and I can't get it working.  It works about half the time with the Diamondcard echo number, and now it works rarely with the [email]500@ekiga.net[/email].  There is a new version that may or may not work, but I couldn't get it installed from the PPA (apparently libraries haven't been upgraded).  For now it's not worth the trouble.

I've tried a couple of others.  Empathy is supposed to be the replacement for Ekiga, but it doesn't do SIP out of the box.  Pidgin, likewise, I think.  I tried Twinkle, with similar symptoms to Ekiga.  I've tinkered with a couple of others, but some of them can barely even start up and terminate, much less make a phone call.

This is the pits.  Can anyone tell me there's something that actually works?

Crunchbang linux comes prepacked with skype, which leads m to think that there is a linux version. but that is probably of little help to you....

---

### Post by cbwcjw on 2010-02-16
There IS a linux version of skype, that is also in .deb and .rpm format.

---

### Post by weblordpepe on 2010-02-16
the linux version of skype was found to data-mine the users /home folder and do all sorts of stuff its not meant to be doing. if you watch it through strace you can see it.

i removed skype for linux and used proper voip. you can either use ekiga or twinkle or something else SIP, and just sign up for a free SIP provider on the net.

---

### Post by VanillaMozilla on 2010-02-17
weblordpepe, please reread my original post.  I have the accounts and one of them actually works occasionally.  But it's no good if you just ring someone's phone repeatedly but can't get a voice connection.

Did you actually get Ekiga or Twinkle to work reliably?

---

### Post by iBurger on 2010-02-17
Empathy and gtalk? I have few friends using gtalk, but empathy seems to support voice out-of-the-box, I think.

---

### Post by VanillaMozilla on 2010-02-17
Gtalk on Linux?  Empathy out of the box?  Are you sure?

I was sort of hoping for something that you had tried and knew worked.  Something that you could actually install from the Ubuntu Software Center, answer a few simple questions, maybe open an account, and then make phone calls.  Reliably.  Something that you don't have to spend three days fixing or file bug reports on.

Does anyone know of such a program?  Does Ubuntu actually have a working VOIP program?

---

### Post by juan.villa on 2010-02-17
> **VanillaMozilla said:**
> And if not, should this be reported as a major bug?

I've spent days on Ekiga, and I can't get it working.  It works about half the time with the Diamondcard echo number, and now it works rarely with the [EMAIL="500@ekiga.net"]500@ekiga.net[/EMAIL].  There is a new version that may or may not work, but I couldn't get it installed from the PPA (apparently libraries haven't been upgraded).  For now it's not worth the trouble.

I've tried a couple of others.  Empathy is supposed to be the replacement for Ekiga, but it doesn't do SIP out of the box.  Pidgin, likewise, I think.  I tried Twinkle, with similar symptoms to Ekiga.  I've tinkered with a couple of others, but some of them can barely even start up and terminate, much less make a phone call.

This is the pits.  Can anyone tell me there's something that actually works?

I run a few Asterisk servers and I've also had a few issues with Ekiga and Ubuntu. Some of the issues are due to the Pulse plugin, bugs, and ubuntu mixed together. I recently stumbled upon a project called "sip-communicator" ([http://sip-communicator.org](http://sip-communicator.org)) that actually works quite well. Let me know how it goes for you.

---

### Post by DZ* on 2010-02-18
I use Pidgin to video chat with my wife every day (over XMPP/gmail.com) and it works very well. It worked "out of the box". She has mini 10v with Karmic and I have Fedora 12 with a USB Quickcam.

Unfortunately, nothing else that I tried worked. Skype works with the mini 10v builtin webcam, but it doesn't recognize the Quickcam on my laptop (tried it unsuccessfully with Ubuntu booted from a USB too). Emphathy gives scratchy sound and the video freezes. Ekiga starts a call, then the video window dies out in a few seconds.

BTW, does anyone know if Pidgin video chat would work when the person on the other end uses google's video chat program for Windows?

EDIT: Ok, I was able to video-chat with a Windows gmail contact using Emphathy 2.28.2 on Fedora 12. Didn't succeed with Pidgin though.

---

### Post by jpl888 on 2010-02-18
You could also try Qutecom. In my experience it isn't perfect (the odd time it will crash on startup) but it works much better than Ekiga for me.

---

### Post by weblordpepe on 2010-02-18
> **VanillaMozilla said:**
> weblordpepe, please reread my original post.  I have the accounts and one of them actually works occasionally.  But it's no good if you just ring someone's phone repeatedly but can't get a voice connection.

Did you actually get Ekiga or Twinkle to work reliably?Hi there. Yeah I did. I got both of them to work. I used Twinkle cos it had more features. It worked out of the box with my existing voip provider.

---

### Post by kapetr on 2010-02-19
I can recommend twinkle or linphone.
And as service what ever except Ekiga.

Ekida SW client and Ekiga service are total broken :-/

---

### Post by VanillaMozilla on 2010-02-19
Thanks for the replies so far. :D I don't know what to blame--the applications or Ubuntu.  But most of these are pretty rough, as your comments indicate.

I have now installed SIP Communicator, and it's outstanding -- meaning that it can actually be used to make phone calls, unlike anything else I've tried so far.  I especially like the development team.  It's still pretty rough though.  I'll write a progress report as I get more information.

EDIT:  I still have a couple of minor problems, and it appears to be pretty good.  It's not as rough as I thought at first.  I'll post progress reports as I have time.

Some of these programs might work if I just find the right magic to get them configured.  Some of them seem to require another protocol besides SIP.  This is taking some work to set up.  Ekiga has another version that's supposed to magically fix the problems, but I had no success installing it.  EDIT:  The updated program didn't work at all on my computer.


OK, I'm thinking of a bug report to Ubuntu to get on the stick.  This is too much work for one casual user.  Most of these programs seem to have too many bugs to report.

---

### Post by DZ* on 2010-02-19
> **jpl888 said:**
> You could also try Qutecom. In my experience it isn't perfect (the odd time it will crash on startup) but it works much better than Ekiga for me.

It segfaults on my Karmic every time I run it...

---

### Post by VanillaMozilla on 2010-02-19
OK, I got Twinkle working too, I think.  DiamondCard echo works.  I'll write a progress report later.  One problem for Ubuntu is that it's KDE instead of Gnome, but that is really not a problem for users.

---

### Post by jpl888 on 2010-02-19
> **DZ* said:**
> It segfaults on my Karmic every time I run it...

Well I've been using it for 7 minutes without and issue see the screenshot. I guess I'm just lucky.

---

### Post by jpl888 on 2010-02-19
Ignore what I said about Qutecom. It's all relative and Qutecom is definitely better than Ekiga but I just tried SIP Communicator and as per vanillamozilla's post it just works. I happen to think it's the nicest looking VOIP app I've seen for Linux and setup is as easy as typing your sip user followed by the sip host name and password and your in. Why can't other apps be as easy as that to setup?

I wonder when the bods will stick it in the repositories? It's far too good at the moment to leave out.

---

### Post by VanillaMozilla on 2010-02-19
Well, I didn't say SIP Communicator is flawless.  On my computer it leaves out the first several seconds of echo tests.  It's also slow to start, slow to hang up, slow to register, and sometimes it takes two attempts to start the program.  I also had some difficulty with installation.  It is still quite new, and only in the alpha phase.

However, aside from that, so far it does just work.  It's one to keep an eye on, and maybe try if your current program has problems.  The project appears to have high-power developers and to be well-funded.

---

### Post by jpl888 on 2010-02-19
That wouldn't be my experience. On my machine it takes about 2 seconds to register and so far it has left flawless voice messages on my mobile. When you bear in mind that I'm trying to use VOIP through a mobile broadband connection it's pretty good. I haven't really spoken to anyone with it yet though. I will try someone tomorrow.

Your experience sounds like the experience I had with Qutecom which was just about bearable. It surprised me initially how well SIP Communicator seems to work obviously only time will really tell.

---

### Post by jpl888 on 2010-02-20
Ok so I just rang my step father with SIP Communicator, he is a little hard of hearing but we managed to have a conversation and he didn't ask me to repeat a thing.

On bringing my laptop out of suspend SIP Communicator didn't crash although it did take a few seconds to register with the SIP provider and start responding to helm.

I think whatever way they have implemented the jitter buffer is really good because jitter has always been the biggest problem with any other soft phone I have tried.

Pings are varying between 93 and 297 milliseconds.

---

### Post by jpl888 on 2010-02-20
Another call to my partner on a mobile and she said it is very clear.

I'll keep using it for the next week and report back.

---

### Post by Boondoklife on 2010-02-20
I use skype all day to talk with family and have not had an issue with video or audio. I even got it working with my bluetooth headset and some scripts. 

While I wish it was possible to integrate it more into ubuntu (right now it is just an eye sore), at least everything works and with out a hassel for me.

I have it working on a dell 1420 and a hp tx2525, on both of them it is able to use the integrated camera just fine.

---

### Post by DZ* on 2010-02-20
What is a good place to get a SIP account apart from ekiga?

---

### Post by DZ* on 2010-02-20
> **Boondoklife said:**
> I use skype all day to talk with family and have not had an issue with video or audio

Pidgin works very well for me for video chat (linux to linux over XMPP/gmail.com). 

I had problems getting it to work with a Windows contact who is using google's browser video chat plugin with gmail. I had to specify v4l2 in the pidgin's video/audio plugin preferences and now that works as well.

---

### Post by jpl888 on 2010-02-20
I'd use Skype but I don't want programs mining my home directory for data.

---

### Post by VanillaMozilla on 2010-03-15
I promised an update.  All these programs have their quirks, but to date I only have one program that works completely.  The problems may or may not be my fault, but the problem is not lack of effort by me.  The only tasks I have attempted are (1) placing overseas computer-to-phone calls by Diamondcard.us and (2) echo tests by SIP.  I didn't try video or receiving calls.

All of these programs require a **trick to terminate the program.**  You have to Quit the program through the menu, rather than pressing the "x" in the corner.  Otherwise they will stay running, waiting for incoming calls.

Also, it may take a little longer than expected to initiate a call--maybe up to 20 seconds, I think.  Be patient before you give up on it.

As far as I can tell, you do NOT need special firewall rules to make calls (receiving calls is another matter, but I didn't try).  Calls went through the default Ubuntu firewall and through the router with no special setup.  And if STUN was used, it was set up automatically, so I didn't have to do anything.


**Twinkle**
Easy to install from the Ubuntu Software Center, and it appears to be reliable for me.  You have to install KDE, but this is not a problem.  It doesn't alter your desktop.  It always passes echo tests, and overseas calls have been successful, with good sound.  I could reach SIP echo sites on the Ekiga network, as well as Diamondcard's echo site.

It's a little tricky to set up.  You have to set up your accounts before you can start the program, but you can't access the setup directions until you start the program!  Fortunately, there are clear directions here:  [http://wiki.diamondcard.us/podwiki?page=TwinklePhone](http://wiki.diamondcard.us/podwiki?page=TwinklePhone) .  (You have to search for it under Twinkle.)

I also had a problem with corrupting the Ubuntu menu if I have it running in two accounts simultaneously, but I can't duplicate the problem.  Otherwise, no problem.


**Sip-Communicator**
This looks like a very nice program, which is easier to set up than Twinkle.  For me it works with Diamondcard echos but not with the Ekiga network.  I have two other problems that have not been solved yet.  First, it cuts off about 10 seconds of the beginning of your call, before you can get sound; and it takes about 10 seconds to hang up.  Second, with one of my computers I have to start it twice before I can get the UI.  Others in this thread have reported excellent results, and developers appear eager to make it work.

This program is rather new, and you can't get it from the Ubuntu repositories just yet.  I initially had a problem with installation, but the damage was easily repaired just by following instructions that Ubuntu popped up.  I could not reproduce the problem on either of two computers.


**Ekiga**
This is easy to set up, and instructions are clear.  If it works for you, just use it, but it still doesn't work for me.  (This comment refers to the program, but not necessarily the Ekiga network.)

I installed the latest, 3.2.6, direct from Gnome.  Most of the time I can't even get the program UI started.  But when I did get it started, it always passed echo tests.  It's a known bug that the version currently in the Ubuntu repository does not reliably send outgoing sound.  EDIT:  the UI hanging may be an ALSA problem.  It's described here:  [http://mail.gnome.org/archives/ekiga-list/2010-March/msg00006.html](http://mail.gnome.org/archives/ekiga-list/2010-March/msg00006.html) .

---

### Post by VanillaMozilla on 2010-03-15
> **DZ* said:**
> What is a good place to get a SIP account apart from ekiga?
You could try Ekiga.  My comments are about the program.  I know little about the network.  Also Diamondcard.us.  I don't know if they have a SIP server as such, but they have several types of services, and they seem good so far.

Also
[http://www.google.com/#hl=en&source=hp&q=sip+account&aq=f&aqi=&aql=&oq=&fp=f8bc9ba0718e9555](http://www.google.com/#hl=en&source=hp&q=sip+account&aq=f&aqi=&aql=&oq=&fp=f8bc9ba0718e9555)

[http://www.google.com/search?hl=en&q=sip+provider&revid=1657334352&ei=IvCeS-DHDo3yM-ikhK4M&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=8&ved=0CD4Q1QIoBw](http://www.google.com/search?hl=en&q=sip+provider&revid=1657334352&ei=IvCeS-DHDo3yM-ikhK4M&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=8&ved=0CD4Q1QIoBw)

---

### Post by Docaltmed on 2010-07-13
The best skype alternative I have found is nomado.eu. It will work with a variety of hardware IP phones, and is trouble-free and of excellent quality in combination with Qutecom. I'm using this combination for my company: 

[http://www.averyjenkins.com/?p=312](http://www.averyjenkins.com/?p=312)

very low cost and works great.

---

