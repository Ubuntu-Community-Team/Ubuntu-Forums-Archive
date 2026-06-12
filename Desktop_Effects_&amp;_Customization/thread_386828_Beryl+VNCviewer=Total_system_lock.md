---
title: "Beryl+VNCviewer=Total system lock?"
date: 2007-03-17
forum: Desktop Effects &amp; Customization
---

### Post by kvonb on 2007-03-17
I've noticed that when I use vncviewer to access my server and I have Beryl running, the whole system freezes after a little while.

Mainly when I drop a menu box on the remote machine to change file ownership etc'.  I use vncviewer in windowed mode, NOT fullscreen.

This never happens unless I have Beryl selected as the Window Manager.

The mouse still moves, but nothing else, no switching to VTs, no ctrl-alt-backspace, no ctrl-alt-del, nothing.

This has only been happening since Beryl went to v0.99999something or other, v0.4 and earlier seemed ok.

Any ideas?

I am using nvidia driver 9755, but this happened on the previous one too, I just upgraded to see if it was fixed.

---

### Post by jinx099 on 2007-03-17
hmmm, I use vnc + beryl and I dont have your issue, but I have noticed that it is much jerkier with beryl.  I also have the newest nvidia driver BTW.  Have you tried alternate vncviewer programs, like xtightvncviewer?  How long does it take to get the lock?  Have you updated to the .0.2 or whatever version of beryl?

---

### Post by kvonb on 2007-03-18
Yes, I updated to 0.2 a day or so ago hoping that would cure it, but no luck.

If it works for you then I expect it's a problem elsewhere on my system :(.

It seems to take a few minutes to lock, I logon then run a terminal to stop apache, then edit a config file.  Then I run a root nautilus and try to change ownership permissions of a few files, that's when it locks, when I am in those prefs menus.

Maybe it's a server side thing, but surely that wouldn't lock the client computer, would it?

I'll try it a few times today, see if I can pin it down.

---

### Post by AusIV4 on 2007-03-18
I use reverse VNC with my girlfriend's computer - that is to say I start listening on my computer, then she runs a script to give access to my computer. I have this script turn off beryl and replace it with KWin, then when I disconnect from her computer, beryl loads back up. Beryl running on my computer isn't a problem, but if it's running on hers, the windows don't refresh properly.

---

### Post by kvonb on 2007-03-20
I installed xvnc4viewer through Synaptic, and it has been running perfectly for well over an hour now :).

It also seems to work faster than the standard xvncviewer too.

---

### Post by djl_ottawa on 2007-03-20
I just installed Beryl and I have the same issue. I connect to my Ubuntu PC at home using my Windows Machine at work. 

Now When I connect it lasts maybe a couple of seconds and then it freezes. Ever since I did the command from terminal sudo beryl-management (or manage I forget which) 

Is there a way to force so that if your connecting on VNC that it turns off beryl?

---

### Post by kvonb on 2007-03-21
> **djl_ottawa said:**
> I just installed Beryl and I have the same issue. I connect to my Ubuntu PC at home using my Windows Machine at work. 

Now When I connect it lasts maybe a couple of seconds and then it freezes. Ever since I did the command from terminal sudo beryl-management (or manage I forget which) 

Is there a way to force so that if your connecting on VNC that it turns off beryl?

Did you try using xvnc4viewer instead?  Just search in Synaptic for "xvnc4viewer" and install it.

Otherwise you could kill Beryl from a script like so:

!/bin/sh
killall beryl
vncviewer 192.168.0.1:5900
beryl &
emerald --replace &

Copy that lot into a new text file and make it executable, try executing it and see what happens :)

---

### Post by djl_ottawa on 2007-03-21
My problem is. At work I am on windows.

Is there a way to setup a script so that if a VNC user connects it stops Beryl? The script you wrote out, where if I can would I put that?

I also noticed in the remote desktop session section for Login Session that I can put either Same as Local or Plain. Now if I choose plain, will that stop Beryl?

---

### Post by kvonb on 2007-03-21
> **djl_ottawa said:**
> My problem is. At work I am on windows.

Is there a way to setup a script so that if a VNC user connects it stops Beryl? The script you wrote out, where if I can would I put that?

I also noticed in the remote desktop session section for Login Session that I can put either Same as Local or Plain. Now if I choose plain, will that stop Beryl?

If you are using the "remote desktop" feature from the system menu, then I believe you are out of luck on that one.

There will be a fabbo complicated way of doing it but I certainly don't know it :).

As an easy but still cumbersome way of doing it would be to ssh into your server first, then kill the Beryl process, then connect via vnc.

That involves installing the openssh server (search for and install openssh through synaptic).

WARNING  This is a security risk, as is leaving remote desktop running on your system.  I would recommend setting the ssh port to something high, don't leave it on the default port.  Also make sure that ALL the accounts on your system have strong passwords.  In the ssh config file you can (I think!), set it to accept connections from selected IPs, so that helps.

Like I said earlier, it is a bit cumbersome, you would have to ssh  (using "putty" on the Windows system), login, then kill Beryl, then vnc into it.

Or you could just leave Beryl off when you leave the house :).

If you need instructions on how-to install and setup ssh, let me know and I can help you with that.

---

### Post by relovett on 2007-04-04
I see the same exact thing with beryl from feisty. Its mostly noticable when the remote machine (in my case a Mac mini) displays something like a progress bar. Every now and then I can detect sluggishness with the overal UI and can then kill the vnc window before it begins to lock things up. I'll try xvnc4viewer to see if it makes a difference.

---

### Post by drdrewdown on 2007-05-24
> **relovett said:**
> I see the same exact thing with beryl from feisty. Its mostly noticable when the remote machine (in my case a Mac mini) displays something like a progress bar. Every now and then I can detect sluggishness with the overal UI and can then kill the vnc window before it begins to lock things up. I'll try xvnc4viewer to see if it makes a difference.

did xvnc4viewer make any difference?  anyone else have any ideas about this problem?  complete lock up sucks ;D

thx

---

### Post by kiddyfurby on 2007-05-25
i use freenx for remoting my desktop
if i need to use vnc (vino to be exact), I simply ssh and kill beryl
then vnc will work

---

### Post by frigaut on 2007-07-03
Hi,

I had the same issue: vncviewer would freeze the WM (beryl) after a while (a few mn), although I did not always had this problem (kind of intermitent). Using xvnc4viewer instead seems to make things better. 
Thanks for the tip.

---

### Post by ikt on 2008-05-05
I have this issue, I disabled the extra visual effects/compiz and it's working ok.

Is there a bug report?

---

