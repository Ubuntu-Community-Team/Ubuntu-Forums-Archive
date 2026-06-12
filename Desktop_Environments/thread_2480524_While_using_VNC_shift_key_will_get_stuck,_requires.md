---
title: "While using VNC shift key will get stuck, requires reboot of server to clear"
date: 2022-11-01
forum: Desktop Environments
---

### Post by Pow_2k on 2022-11-01
Ubuntu 22.04.1 LTS, kernel Linux 5.15.0-52-generic, using the included GNOME Remote Desktop service to access the system via VNC protocol.

Every now and then when I'm connected to my Ubuntu machine via VNC I'll be typing quick and hit some key combination or otherwise confuse the system that causes the shift key function to stick.  This is not an accidental turn on of caps lock.  If I went to type a slash (/) I would instead get a question mark (?).  Turning on caps lock inverses the case but unfortunately that doesn't work for other keys. (typing / still produces ?)  This seems to be the OS getting confused.  Reconnecting doesn't fix it, restarting the remote desktop service then reconnecting doesn't clear it.  From what I remember (unable to confirm at the moment) this is even reflected when I get to the local input at the computer and not cleared by removing/reattaching the local keyboard.  The only way I've found to clear this is to reboot the host Ubuntu computer.  This has happened from multiple clients and been happening since upgrade to 22.04.1 I think.

Connecting via a ssh session still works normally, so I'm able to run commands there without issue to try and find a resolution.  Does anyone have any thoughts of other things I should look at to try and get this resolved without needing a reboot?  Finding root cause would be great, but in the interim a solution that would just reset the shift status so I could resume using my VNC session normally would be welcome.

---

### Post by Pow_2k on 2022-12-05
Resurfacing this to check again if anyone has any ideas as I've had to go down to my basement and reboot the server 3x today.  Can confirm the issue still exists at the local keyboard.  At least once today when it happened the keystroke series was "w" followed by "shift + e".  After the capital e the shift key was stuck virtually.  Now on kernel 5.15.0-56-generic.

---

### Post by ActionParsnip on 2022-12-06
What are you doing on the remote session that needs the whole desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by Pow_2k on 2022-12-13
> **ActionParsnip said:**
> What are you doing on the remote session that needs the whole desktop session? There may be a sleeker solution to what you want to achieve

Thanks for jumping in.  While the bulk of what I'm doing could be handled via X server, there are various tasks that I regularly perform that I would prefer to do via a desktop session.  That said, when faced with a problem like this where it is in a lab rather than production environment allowing more freedom to work on the issue, my preferred way to address it is in the order of:
1. Identify and fix the root cause
2. Find a solution to correct the problem after the fact, even if it needs to be done each time
3. Work around the problem entirely

With #1, for as many times as this has happened to me I don't have a way to reliably reproduce this issue so finding the root cause is currently a long shot.  Addressing the root cause is the preferred solution as if that can be done it can solve a potential issue for all users.  Since I don't have the ability to make much progress on #1, #2 then becomes preferred because at least I could get back to work while possibly in parallel collecting more data on the root cause.  #3 might work for me but it just leaves the problem out there to possibly impact other users.  This is why I'm hoping to find a way to "reset" the keyboard on the system as my question.

One update I do have is that I turned on the on-screen keyboard on the desktop and couldn't find a way to clear the issue with that.  If I remember correctly it acted identically to the local and remote keyboard, acting as if the shift key was held down.

---

### Post by ActionParsnip on 2022-12-13
What are the tasks you'd do on the desktop session? This is what I was asking for....

---

### Post by Pow_2k on 2022-12-15
> **ActionParsnip said:**
> What are the tasks you'd do on the desktop session? This is what I was asking for....

The bulk of the time web browsing.  Less often running VMs and other random tasks as they pop up.

---

### Post by ActionParsnip on 2022-12-15
You can add an SSH tunnel to the client and use it as a web proxy. The traffic will flow down the tunnel and make the Web client look like the remote system. Dead easy.

---

### Post by Pow_2k on 2022-12-15
Not sure I understand the setup you're describing.  If I'm remote or on my work VPN I am already using an SSH tunnel for the VNC port and am connecting through that.  I'm sure that's not what you're describing though.

Also, it seems like the combination of "shift" + "e" is what gets me hung up in the first place.  I've just reproduced it.  Not every time, but at least once intentionally.  So now maybe I can get to the bottom of what is causing the issue.

---

### Post by ActionParsnip on 2022-12-15
[https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel)

---

### Post by scootley on 2023-04-30
I have this same issue.  It is also described [here]("https://askubuntu.com/questions/1451742/keyboard-shift-get-stuck-when-entering-password-with-special-characters-via-vnc") on Ask Ubuntu.  No solution. Anyone report a bug on this yet?

---

### Post by scootley on 2023-05-01
[COLOR=#232629][FONT=-apple-system]If you can reproduce this, can you try running "xset q" to see if X reports that "Shift Lock" is on when it happens?[/FONT][/COLOR]

---

### Post by cybermass on 2024-03-13
I am having the same issue, using TeamViewer but I believe it uses the same protocol.

I ran the xset q command, shift lock is off, only num lock is turned on which is by my keyboard. I was able to disable the caps lock by using alt+caps lock however the shift lock is still effecting special character keys.

Here's a screenshot of the keyboard control output from the xset q command, hope this helps; [https://prnt.sc/-Vedv6p-TyH7](https://prnt.sc/-Vedv6p-TyH7)

---

### Post by Skaperen on 2024-03-17
try this on the client machine before making the VNC connection   Whisker Menu > Settings > Accessibility > Keyboard ... if "Use Stick Keys" is off, turn it on, if it is on, turn if off then back on.  with this mode on, using the keyboard in the usual way still works as before, but this mode also operates in a new way.  if you press a modifier key like Shift, Ctrl, Alt, that window key, then it gets held down for you so you can let the modifier key up before you press the key that is modified.

while this feature affects key downs, it may be using the part of keyboard code that is matching ups and downs.  so it might work better.  but it sends a modifier down after sending the data code for up (so the modify only affects one press).   if the problem still happens, you can work around it very simply.  when you see the ? when you wanted / then just backspace and press / again.  it would have saved the down state after it sent ? so now it should be good.

---

### Post by Skaperen on 2024-03-17
> **cybermass said:**
> 

Here's a screenshot of the keyboard control output from the xset q command, hope this helps; [https://prnt.sc/-Vedv6p-TyH7](https://prnt.sc/-Vedv6p-TyH7)

why is your Num Lock on?

---

