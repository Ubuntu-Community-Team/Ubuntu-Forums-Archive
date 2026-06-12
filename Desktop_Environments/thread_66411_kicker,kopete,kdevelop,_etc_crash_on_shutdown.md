---
title: "kicker,kopete,kdevelop, etc crash on shutdown"
date: 2005-09-17
forum: Desktop Environments
---

### Post by Jaristr on 2005-09-17
Hi.
Does this happen to any one else? Many programs crash and give error reports when you try to shutdown kubuntu?
Usually you can just click "ok" and the system shutdowns but sometimes I have to turn it off from the power switch.

---

### Post by Jaristr on 2005-10-01
No one else has this problem? Or any idea how to fix this?

Thank you...

---

### Post by Knome_fan on 2005-10-01
Hm, no I'm not having this problem.

Could you perhaps post specific error messages you get?
Did you try to start startkde from an xterm, so that you may be able to see what exactly is going on?

---

### Post by Takis on 2005-10-01
[QUOTE=Jaristr]Usually you can just click "ok" and the system shutdowns but sometimes I have to turn it off from the power switch.[/QUOTE]
You mean the entire shutdown sequence is halted? There would have to be a major error for that to happen. How long do you wait before whacking the power button?

---

### Post by Jaristr on 2005-10-03
[QUOTE=Knome_fan]Hm, no I'm not having this problem.
Could you perhaps post specific error messages you get?
Did you try to start startkde from an xterm, so that you may be able to see what exactly is going on?[/QUOTE]

I don't know how to take a screen shot at that point but I'll try to write down the error messages.

---

### Post by Jaristr on 2005-10-03
[QUOTE=Takis]You mean the entire shutdown sequence is halted? There would have to be a major error for that to happen. How long do you wait before whacking the power button?[/QUOTE]

Yes, it never gets to the console part where texts start to flow but it just shows black screen and does nothing (according to HD's sounds). I think I waited fairly long, maybe I left it there a while but nothing happened, sorry I don't remember because it rarely completely locks. 
And it propably doesn't lockup it just waits for some input because of the of the errors I suppose, but I can't see them because graphics usually go pretty wild.

---

### Post by getaceres on 2005-10-03
I have the same problem. Some applications crash sometimes at log off. If they remain on screen enough time and I don't push the close button in the crash message, when I click in it I get to a black screen and the system is not halted. I have to reset it.

---

### Post by Jaristr on 2005-10-04
[QUOTE=getaceres]I have the same problem. Some applications crash sometimes at log off. If they remain on screen enough time and I don't push the close button in the crash message, when I click in it I get to a black screen and the system is not halted. I have to reset it.[/QUOTE] 

That's exactly the same problem, you have to be quick enough with the close buttons or it will be too late. 



Well I tried starting KDE with startkde command but it gave couple errors among other messages in command line and did not start. Something about not being able to connect and no initkde.

---

### Post by Knome_fan on 2005-10-04
[QUOTE=Jaristr]That's exactly the same problem, you have to be quick enough with the close buttons or it will be too late. 
Well I tried starting KDE with startkde command but it gave couple errors among other messages in command line and did not start. Something about not being able to connect and no initkde.[/QUOTE]

My bad.
I didn't mean starting it from the command line (that is for example Ctrl+Alt+F1), but to choose safe mode (I'm not sure what it's called exactly) from the session menu in kdm. This should give you a terminal and you should be able to start kde from within this terminal.

---

### Post by Buze on 2005-10-04
hello !
i'm a newbie @ kubuntu and linux, but wanted to say that I have the same problem.
maybe a vote would determine how frequent this crash is (i mean estimate if it is a sporadic event or not, for a given distribution).
I've search a bit about this problem and i did not find anything.
So, what's up ?
Buze

---

### Post by scokar on 2005-10-05
This happens to me. I suspect its due to using kaffeine (standalone or embedded in konqueror).  KDE 3.4.2

---

### Post by Brando569 on 2005-10-05
i have this problem too but only with kopete, i just click ok and everythings fine

---

### Post by getaceres on 2005-10-05
[QUOTE=Brando569]i have this problem too but only with kopete, i just click ok and everythings fine[/QUOTE]
The problem is not the crashes (well, it is too, but anyway you are closing them). The problem is:
1. You can't push shutdown button and go away because youre system may not shutdown if an application crashes. I thought it only happened in Windows, but as a see it happens too in Linux, at least with KDE.
2. If you don't click ok fast enough you can't close the x session, so you have to reset the system. This is always a bad thing.

---

### Post by Jaristr on 2005-10-07
OK what I started kde in safemode with the startkde command and then I selected restart from the logout menu and here are couple interesting lines from the console output:
(I don't know how to copy the text from the safemode console so I typed it in here)

X Error: BadWindow (invalid Window parameter) 3
 Major opcode:   7
 Minor opcode:   0
 Resource id:    0x1a00007
X Error: BadWindow (invalid Window parameter) 3
 Major opcode:   6
 Minor opcode:   0
 Resource id:    0x1a00007
X Error: BadWindow (invalid Window parameter) 3
 Major opcode:   7
 Minor opcode:   0
 Resource id:    0x1a00008
X Error: BadWindow (invalid Window parameter) 3
 Major opcode:   6
 Minor opcode:   0
 Resource id:    0x1a00008
kicker: crashHandler called
OGDict::hashKeyString: Invalid null key
OGDict::hashKeyString: Invalid null key
libkopete: WARNING: [virtual Kopete::PluginManager::~PluginManager()} Desctructing plugin manager without going the shutdown process! BackTrace is:
libkopete:
KCrash: Application 'kicker' crashing...
startkde: Shutting down...
klauncher: Exiting on signal 1
kicker: sighandler called
DCOP aborting while waiting for answer from 'kicker'
kicker: sighandler called
Session management error: Coul not open network socket
DCOPServer::DCOPReply for unkown connection.
DCOPServer::DCOPReplyDelayed for unknown connection.
kicker: ERROR: : couldn't create slave : Could not connect to klauncher
ICE default IO Error handler doing an exit(), pdi = 7675, errno = 0
startkde: Running shutdown scripts...

plus few uninteresting lines

---

### Post by Jaristr on 2005-10-20
Any one know if these issues have been fixed in some newer version of kubuntu?

Thanks.

---

### Post by kubuntuser on 2005-11-18
[http://ubuntuforums.org/archive/index.php/t-68760.html](http://ubuntuforums.org/archive/index.php/t-68760.html)

"hanover.fiste 09-24-2005, 07:35 AM

Did you add any of the optional menus from the panels menu? If so, this is a known issue in the main line tree, and has been fixed. But the fix didn't make it into 3.4.2. Should be in 3.5."

---

### Post by madtinkerer on 2005-12-29
I had the same problem in kde 3.5.  I seemed to have fixed it by booting into a console and running rm .DCOP* and then rebooting.

---

### Post by André on 2006-01-03
Hi,

i did the .DCOP step but no go. Kicker still crashes when i log out and gives me a message about klauncher :-(

Any ideas?

Greetings
André

---

### Post by arthur_kalm on 2006-01-15
[QUOTE=André]Hi,

i did the .DCOP step but no go. Kicker still crashes when i log out and gives me a message about klauncher :-(

Any ideas?

Greetings
André[/QUOTE]

I tried also tried the .DCOP step and kicker still crashes on log out. I also get the klauncher error sometimes as well.

This does not happen on my laptop however :(

---

### Post by getaceres on 2006-01-16
Deleting the .DCOP have solved the problem to me (I think so).

---

### Post by André on 2006-01-16
It came back for me. Even on my laptop.

I switched back to Ubuntu and it feels really good so far.

Will try Kubuntu again with the next release ;-)

Greetings
André

---

### Post by disraeli on 2006-03-10
[QUOTE=André]Hi,

i did the .DCOP step but no go. Kicker still crashes when i log out and gives me a message about klauncher :-(

Any ideas?

Greetings
André[/QUOTE]

i have exactly the same problem. kicker crash + klauncher message. will try to copy down the error message before it disappears; in fact, in my case i just get those error messages and even if i dont press anything, the system reboots normally

---

### Post by t.rei on 2006-05-03
same thing for me - I guess - I've never gotten to see the error message, so no chance in being fast enough to click. 
Screen goes all black on logout and no Keyboard gets through (tried to go to a blind console). Maybe I'll try connecting to the systems ssh-server next time, but this is what ruined my kde-try for me today. I really dislike resetting my system. !

---

