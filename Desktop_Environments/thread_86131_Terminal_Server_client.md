---
title: "Terminal Server client"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Ventajou on 2005-11-04
Hi,

I am using the Terminal Server Client to connect to a Windows 2003 server at work as well as my Hoary server at home, both using VNC. It works very well but  when I am done and I close the window, a dialog box pops up stating that an error has occured and apparently giving me a log of the connection...

Is there a way to close the VNC connection without generating that message? Or simply a way to disable it? I could not find anything in the properties...

Help!

---

### Post by ZeusABJ on 2007-09-20
Wow, this was posted back in 2005 and got no responses. I was just about to make a post with the same exact question. Surely someone here knows the answer to this. Please post a response because if two people want the answer surely there are others who would like this explained. Anyone?

---

### Post by marquee moon on 2007-09-29
yes, I also have the same error message when logging onto windows server 2003. It doesnt bother me to much though becuase everything still works just fine.

---

### Post by ZeusABJ on 2007-10-15
> **marquee moon said:**
> yes, I also have the same error message when logging onto windows server 2003. It doesnt bother me to much though becuase everything still works just fine.

Well it works yes, but the issue is it displays an error message where there is no error! Also it tries to reconnect after 30 seconds and its just irritating. Also it would be FANTASTIC if there were some easy way to get out of full screen mode (like the bar that slides down from the top of the remote desktop client in Windows). I mean (like you) I can certainly live with Terminal Services the way it is, but I'd just like to if there's any way around these minor annoyances. Thats all I want here. Still it looks like nobody is going to respond with a solution. However (optimist that I am) I'll send out one final call for assistance, then I suppose I'll just drop the issue.

**[COLOR="DarkRed"]*How about it? Can anyone PLEASE help us with tis issue? Even a simple "no you can't fix it" would at least provide closure...*[/COLOR]**

---

### Post by lankford on 2007-10-26
Just press F8 and it will pop up a menu that you can:
toggle full screen
exit
send CTRL or ALT
send F8
send CTRL-ALT-DEL
refresh
Create a new connection
Options
Connect Info

---

### Post by lankford on 2007-10-26
OOPS, Misread what was asked, sorry, I though the question was how to exit fullscreen...

---

### Post by kvasimongo on 2007-10-29
[http://ubuntuforums.org/showthread.php?p=3659984#post3659984](http://ubuntuforums.org/showthread.php?p=3659984#post3659984)

---

### Post by ralph_walden on 2007-11-07
> **lankford said:**
> Just press F8 and it will pop up a menu that you can:
toggle full screen
exit
send CTRL or ALT
send F8
send CTRL-ALT-DEL
refresh
Create a new connection
Options
Connect Info

I know this post may have been from a while back.

I don't seem to get any menu when pressing F8 from the fullscreen terminal.  Do you need some key modifier with it?

Ralph Walden

---

### Post by minutezero on 2007-11-07
AHA! I finally got it.  The link above ([http://ubuntuforums.org/showthread.php?p=3659984#post3659984]("http://ubuntuforums.org/showthread.php?p=3659984#post3659984")) helped me.  I set the protocol to RDPv5, but then I also checked the details of the error, and mine said "WARNING: Remote desktop does not support colour depth 24; falling back to 16".

So under the Display tab I set it to 16bit and finally the disconnect errors are gone!  The combination of the two (RDPv5 and 16bit colour depth) worked.

Hopefully this helps someone else with the same issue.

mZ

---

### Post by lankford on 2007-11-08
> **ralph_walden said:**
> I know this post may have been from a while back.

I don't seem to get any menu when pressing F8 from the fullscreen terminal.  Do you need some key modifier with it?

Ralph Walden

Sorry, this only works in VNC connections, the RDP

---

### Post by ZeusABJ on 2007-11-23
> **minutezero said:**
> AHA! I finally got it.  The link above ([http://ubuntuforums.org/showthread.php?p=3659984#post3659984]("http://ubuntuforums.org/showthread.php?p=3659984#post3659984")) helped me.  I set the protocol to RDPv5, but then I also checked the details of the error, and mine said "WARNING: Remote desktop does not support colour depth 24; falling back to 16".

So under the Display tab I set it to 16bit and finally the disconnect errors are gone!  The combination of the two (RDPv5 and 16bit colour depth) worked.

Hopefully this helps someone else with the same issue.

mZ

HAH! Absolutely right! You've got it! Thanks so much for the help on this guys. REALLY appreciate it!

---

### Post by kevindontenville on 2008-01-24
Nope, this doesn't work for me. 16 bit and rdpv5 are on and I still get the error, reconnecting in 30 seconds dialogue.

Doesn't seem to happen on puppy, debs, etc etc so its an Ubuntu specific I think. My error suggests autoselected keyboard map en-gb.  Looked under local resources - keyboard - use the following keyboard language - and selected en-gb and the error stopped. 

I think this is a bug in the client config not picking up on the autoselected language, protocol, screen etc. It autoselects it appropriately but doesnt pass this through for some reason. Anyone else had similar?

I'm using Gutsy fully patched and it's still here!

K

---

### Post by chenel on 2008-01-25
Selecting the proper keyboard map doesn't fix it for me.  Nor do any of the other suggestions in this thread...  I wouldn't mind the error so much, what's irritating is the auto-reconnect.  Sometimes I log in locally (which kicks off the remote session) but then because it auto-reconnects the machine is locked again after 30s and I have to log in again -- so I log in locally again, then after 30s it auto-connects again, etc. ....  It's very frustrating when you want to use the machine locally and forgot to close the remote session.

I would appreciate a solution as well.

---

### Post by chenel on 2008-01-25
I found [another thread]("http://ubuntuforums.org/showthread.php?t=559169") that suggests using gnome-rdp instead for this reason.  It's in the repos.

---

