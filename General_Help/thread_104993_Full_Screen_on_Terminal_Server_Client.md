---
title: "Full Screen on Terminal Server Client"
date: 2005-12-17
forum: General Help
---

### Post by filipenetto on 2005-12-17
Hi guys ... how do you do ?

So, I'm having this problem: I connect to my Terminal Server (Windows Server 2003) using the Terminal Server Client. But, in full screen mode, I don't know how to exit the window.

IE: on a workstation with Windows, I connect to the Terminal Server and, when I pass the cursor in the top of the screen, a bar with "Minimize", "Restore" and "Close" appear, but, this not happen on Linux.

So, maybe have a command to exit the full screen mode. Somebody know this command ?

Tks ! :)

---

### Post by matva on 2005-12-17
lol i have the same exact question. had to do a reboot just to get out lol.

---

### Post by filipenetto on 2005-12-17
Yeah, this is my problem too. Sometimes, I don't wan't to quit my session, but I have to do this to back to the Linux desktop.

You don't find the solution matva ?

---

### Post by RikoW on 2005-12-19
Hi,

I run grdesktop now but I think it was the same in the terminal server client - should be at least if it  uses rdesktop underneath!

you can switch the running session between full screen und window mode by hitting ALT-CTRL-ENTER/RETURN in the session at the same time.

see *man rdesktop* for details.

Very useful indeed! :)

Cheers,

           Riko

---

### Post by DiscoKiller on 2005-12-21
Sorry, my solution was to boot into the recovery mode and cp my backup config file to the existing one, cant rememer the command sorry.

---

### Post by filipenetto on 2005-12-21
Ok, 

The command suggested by RikoW (Ctrl + Alt + Enter) was work. 

Thank you !

---

### Post by waster on 2005-12-23
you can also ssh back to the source box (reverse tunnel if necessary!) and then kill the process. Or wait for a power cut.

---

### Post by whi8esauce on 2008-05-18
> **RikoW said:**
> Hi,

I run grdesktop now but I think it was the same in the terminal server client - should be at least if it  uses rdesktop underneath!

you can switch the running session between full screen und window mode by hitting ALT-CTRL-ENTER/RETURN in the session at the same time.

see *man rdesktop* for details.

Very useful indeed! :)

Cheers,

           Riko
this works for me! thanks you made my day!

---

### Post by lib99 on 2008-05-27
I find the Terminal Server Client (tsclient 0.150) to be unstable when using CTRL+ALT+ENTER on a 1 week old fresh 8.04 installation. Essentially I am finding that the screen is trying to change but will not. Any one else experiencing this?

[To quit the session so as not to reboot (another person's earlier post), you can click Start then either Disconnect or Log Off. Use RDPv5. Another idea is to open the full screen RDP session on one desktop workspace and switch between them.] 

Dell Inspiron 9400/E1705
2.0 GHz Intel Duo Core
2GB Ram
256MB NVidia Card

---

### Post by sikslk on 2008-07-14
Hi all...

Sorry, complete noob here looking at using ubuntu in the workplace.

Similar problem as in this thread, have tried both tsclient 0.150 and Remotedesktop Client 0.23 but both have the full screen problem.

I have tried the ctrl+alt+enter and it brings up the ubuntu background for a second before returning to the ts screen.  

only solution is to log entirely off as the above user suggested.  any other versions to try?

---

### Post by duggaman57 on 2008-07-17
> **sikslk said:**
> Hi all...

Sorry, complete noob here looking at using ubuntu in the workplace.

Similar problem as in this thread, have tried both tsclient 0.150 and Remotedesktop Client 0.23 but both have the full screen problem.

I have tried the ctrl+alt+enter and it brings up the ubuntu background for a second before returning to the ts screen.  

only solution is to log entirely off as the above user suggested.  any other versions to try?


I'm having the same problem to. I refuse to just power off my machine..lol. Any other ideas anyone?

---

### Post by lib99 on 2008-07-17
> **duggaman57 said:**
> I'm having the same problem to. I refuse to just power off my machine..lol. Any other ideas anyone?
Can you try Start->Disconnect? (on the session OS...Windows) That will break the terminal session but your remote windows system will still be operating. At least this way you don't need to reboot anything.

I've been using the tsclient either in nested window (not full screen) and can then easily move back and forth. Or, when I need full screen, I just use the windows disconnect I mention above. Its my workaround to a probably bug with the tsclient.

---

### Post by sikslk on 2008-07-17
an update on my work around, i run a cmd as a shortcut to make it a neat window sitting in between the menu bars so all the ubuntu menus are free to be used at the same time.

```
rdesktop -D -g 1440x850+0+0 -K -u [name] [server]
```

only work around i have so far. Seems to work ok... thought this would be simple to implement in a gui.

---

