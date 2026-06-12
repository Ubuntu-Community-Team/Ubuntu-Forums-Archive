---
title: "AvantGo and GnomePilot"
date: 2005-08-02
forum: Desktop Environments
---

### Post by kdupuy9 on 2005-08-02
I'm Running Ubuntu 5.04 and am syncing a Zire 31 with GNOME. Everything is running smoothly, except for AvantGo. I enabled the MAL conduit and synced. After the sync, I checked AG to see the updated pages. But I was greeted with a page asking for my AG Password. I entered it and it asked me to sync to get my content, so I did, but it only greeted me once again with the login screen on AG. COuld someone help me or refer to something that might? any help would be greatly apprecated.

---

### Post by drt on 2005-08-13
This sounds like a very similar problem to one I have.

I too followed all the instructions only to find AvantGo on my Palm keep asking me to login.

I got round that by doing a sync with AvantGo via a GPRS mobile phone link.

I then decided to use Malsync on the command line so I could see what was going on.

I was amazed that the error which was being given - and I would imagine it is the same error you are getting but can't see as Gnome-Pilot doesn't tell you.  The error was "Invalid login: please check your username and password and try again".

I know the login details are correct, as the very same details successfully connected to AvantGo over the GPRS link.

Something must be wrong with how Malsync is set on Ubuntu.

One thing which confused me was that Synaptic says that the installed version is 2.2.0-1, but "malsync -v" returns 2.0.0.

I am going to remove the Synaptic package and compile from scratch the latest version of Malsync from Tom W's page and see if that cures the problem.

I'll let you know if it does - meanwhile, has anyone else seen this problem?!

My system details are:  Ubuntu Hoary Hedgehog on AMD 64, Palm Tungsten T3.

---

### Post by drt on 2005-08-13
Bad news:  installed a new Malsync package from Debian, again version 2.2.0-1.

"Malsync -v" still reports version 2.0.0 and still doesn't work.

I just don't understand this.

Looks like I'll have to revert to Windows to try to get this to work... :-(

---

### Post by drt on 2005-08-13
Final word from me on this subject:

In desperation, I tried uninstalling my newly downloaded AvantGo version 5.7 build 42 application from my Palm, and installed version 5.2 available from Tom W's Malsync page.

But, guess what?  That still threw up the "Invalid Login" error.

I give up!

---

### Post by drt on 2005-08-16
Excecpt I didn't give up - I kept trying to find a solution, and (if you'll excuse the multiple replies to the same post) I thought I would post it here for the benefit of others who might have been having the same problem as I.

I solved the problem by looking at it from a different angle. I decided to leave Malsync, and go instead for a PPP connection from my Palm to my computer, and to allow AvantGo to access the internet directly for updates, instead of trying to work via a conduit.

I followed the instructions at [http://atulchitnis.net/writings/palm-ppp.php](http://atulchitnis.net/writings/palm-ppp.php) and with a minor tweak to my firewall, all is working fine!

Proof, I guess, that there is always a solution, just not necessarily the one you thought it would be!

---

### Post by LostAndFound on 2006-09-26
To 'drt' - thanks a lot. Your persistence and follow-up is much appreciated. 

I have the same problem using jpilot and with the SyncMal plugin on Ubuntu 6.06. 

On another computer with SuSE (i386 architecture)  SyncMal has been working OK for some time, and the settings appear to be the same as with Ubuntu. However my Ubuntu is AMD 64 architecture, so perhaps 64 bit is the issue - I note that you also have AMD 64 

Atul Chitnis's instructions and solution are an excellent workaround, and are clear and easy to follow.

---

### Post by DJ_Peng on 2007-04-25
Thanks, drt, I've been looking for this. Now I have one less reason to go into Windows,

---

### Post by AbredPeytr on 2007-07-13
I'm also having trouble getting Avantgo to sync.  I recently installed feisty fawn 64 bit on my AMD64 and was pleased that I didn't have to do anything to get my Palm TX to sync my contacts and calendar. 

I've tried installing malsync 2.2.02, but it gives me the following error: Dependency is not satisfiable: libpisock8. I've tried using the Synaptic Package Manager to install it, but it only finds libpisock9, which is installed. Anyone else had this problem and solved it?

Thanks for the help.

---

### Post by ederic on 2008-02-16
It worked. Will try it also using bluetooth. :)

---

