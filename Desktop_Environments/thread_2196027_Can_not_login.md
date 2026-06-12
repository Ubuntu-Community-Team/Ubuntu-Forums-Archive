---
title: "Can not login"
date: 2013-12-27
forum: Desktop Environments
---

### Post by xendistar2 on 2013-12-27
I did a completely new install of Lubuntu on to a PC earlier to day, the setup went ok with no issues, I then moved on to updating the system and installing the other software packages I wanted, during all this I rebooted the PC several times and had no problem logging in. I installed ssh server and I was able to ssh into the PC, I then installed vnc server but was having difficulty getting it running. When I checked the history of installed packages I realised rather than installing tightvnc server which is the one I normally install I had installed something like x4vncserver. So I selected x4vncserver for complete removal and installed tightVNC server. I gave the PC a reboot just to be on the safe side. Once it has rebooted I tried to ssh into the PC but was unable to, I then tried logging into the PC from the PC itself and found I was unable to.

When I try and login I enter the password, click log-in the screen goes black and then comes back to the log-in screen again asking for my password. If I type a word that I know is not my password then a red box immediately pops up when I click on log-in. So that tell me it is not my users password that is the problem. I only have the one login on the PC so I cant login as another user other than guest but when I login as that there is very little I can open or run, I cant Sudo to anything as I don't have permission and I cant change permission as it wont accept my password.

Anybody any thoughts on what the problem could be and how to correct it?

---

### Post by steeldriver on 2013-12-27
it basically means that authentication is successful, but your user's desktop session fails to start for some reason - that can be

[LIST]
[*]disk (or home partition, if you have one) out of space 
[*]user's $HOME dir unwriteable for some other reason (ownership / permissions) 
[*]user's $HOME/.Xauthority and/or .ICEauthority unwriteable (owned by root - often happens if you try to startx with sudo) 
[*]something else in the user's session or profile that is killing it immediately (possibly a bad saved session?) 
[/LIST]

The root owned ~/.Xauthority is far the most common one - since it only needs to be writeable for X sessions, console login via one of the virtual terminals (Ctrl-Alt-F1 etc) should allow you to fix it.

Doesn't explain why the SSH server has become unresponsive though - so you may have deeper issues

---

### Post by xendistar2 on 2013-12-28
OK I have logged in via CTRL-Alt_f1 without a problem but I am now a little lost as to what to do, I tried renaming .Xauthority thinking it may create a new one when I log in but from the graphical login it just goes to a blackscreen and nothing else.

When I first logged in the permission of .Xauthority were set to *root root*, I compared this to .Xauthorty on my xubuntu PC and it is set as *myusername myusergroup* so I changed the permission to replicate this and when I try and login via the gui I get the same blackscreen as above.

Is there a way I can re run the X configuration or is their a better alternative?

---

### Post by steeldriver on 2013-12-28
well if I'm reading that right, it sounds like progress (having removed / reset ownership of ~/.Xauthority you are no longer being bounced back to the login screen, correct? just a completely black screen *after* login?)

since you *can* login as guest, I don't think there's anything fundamentally wrong - the problem must still be something in your main user's profile / saved session / cache / config files

---

### Post by xendistar2 on 2013-12-29
Ok progress is being made, I can now login to the a gui desktop. I renamed the openbox folder in .config and I can now login. I can also now login in via ssh I don't know what the connection was but I know both are now working. I have even got vnc working to a point but that will need a new thread.

Thanks for the help Steelrider

---

### Post by mörgæs on 2013-12-29
If the problem is solved please mark the thread so using 'thread tools'.

---

