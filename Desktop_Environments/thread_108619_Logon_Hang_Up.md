---
title: "Logon Hang Up"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Mike-97470 on 2005-12-26
Currently the only way I can get logged into Ubuntu is to use the "Fail Safe Gnome" (?) option that foregoes loading the session scripts.  If I try to logon using my "last" session or the default system session or the regular Gnome session, after I logon my system freezes on the Metacity Windows Manager screen with only the first desktop icon displayed.

I think it started doing this when I unchecked "save current session settings" in System/Preferences/Sessions/

The reason I was fooling with that is because a couple of days ago I ran Automatix and then configued Firestarter to automatically run without asking for my password again (I have a single user secure system)--
  I added the lines--
# No password needed to start firestarter firewall
mike ALL= NOPASSWD: /usr/sbin/firestarter

at the end of the file-- etc/sudoers

and added--
sudo firestarter --start-hidden 
to System/Preferences/Sessions Startup Programs replacing whatever Firestarter put there when the Automatix process set it up.  Firestarter now shows up on the upper taskbar.

After making those changes to always run Firestarter, I started getting an error message window saying I didn't have root privledges to use Firestarter.

Another thing that was happening in my session is that Skype (also installed by Automatix) was automatically launching after logon although it isn't a System/Preferences/Sessions Startup Progam.

All of this seems session related to me, but I don't have a clue of where to look to fix whatever got messedup.  Anyhelp will be appreciated, thanks,

---

### Post by sciurus on 2005-12-26
I would make a new account and try to configure things without using Automatrix.

---

### Post by Mike-97470 on 2006-01-15
Thanks, that is a solution, but a rather brute force one as everything would need to be configured all over again . . . 

So what I did to resolve this is to just keep playing with System/Preferences/Sessions until I got everything working again.  It was a little tricky, one of the tricky things is getting the Session settings saved.

Getting rid of the nasty login error message saying something about needing to be Root privedged to run Firestarter was a real nusance!  (Yes, I want the cute little icon up in the task bar so I can see if I've been attackked--it changes from blue to red when that happens.)

Originally I used sudo gedit to edit etc/sudoers--finally I used sudo visudo to do it, but the end result is the same (I think--both ways edit the file).  The session StartUp Program command that works is "sudo firestarter --start-hidden"  --  getting the session saved correctly is the tricky part.  When I did that, the error message disappeared.

(Also, the default StrartUp Programs seemed to be overriding the myusername StartUp Programs--that was tricky too.)

---

