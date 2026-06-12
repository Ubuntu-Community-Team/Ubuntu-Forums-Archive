---
title: "CTRL-ALT-Backspace doesn't restart X-server?!"
date: 2009-06-09
forum: General Help
---

### Post by JohnE1 on 2009-06-09
Ubuntu 9.04 Jaunty Jackalope

In other Linux distributions, including older versions of Debian, I could always free up a "stuck" X-server by restarting it with CTRL-ALT-Backspace.

Why doesn't it work in Jaunty Jackalope?

Is there a way to re-enable these keys to restart X-server?

John

---

### Post by Jabz.biz on 2009-06-09
They have disabled this in jaunty. I hate it as well. Do a google search...there are many ways to switch it on again.

---

### Post by dcstar on 2009-06-09
> **Jabz.biz said:**
> They have disabled this in jaunty. I hate it as well. Do a google search...there are many ways to switch it on again.

Including simply looking at the Jaunty Release Notes.

---

### Post by l-x-l on 2009-06-09
The new way to restart X is Righ-Alt button+K+SysRq.

---

### Post by jmszr on 2009-06-09
JohnE1,

This thread has the fix: [http://ubuntuforums.org/showthread.php?t=1134427](http://ubuntuforums.org/showthread.php?t=1134427) . Post#2

---

### Post by JohnE1 on 2009-06-10
> **l-x-l said:**
> The new way to restart X is Righ-Alt button+K+SysRq.

Thank you for that simple answer!  Much appreciated.

John

---

### Post by sabmo on 2009-06-10
Right-Alt + Print Screen + k

---

### Post by dsauter on 2009-12-27
For anyone who did a google search and came here, this is another way:

[http://sathyasays.com/2009/11/08/enable-xserver-shortcut-ctrlaltbackspace-in-ubuntu-9-10-karmic-koala/]("http://sathyasays.com/2009/11/08/enable-xserver-shortcut-ctrlaltbackspace-in-ubuntu-9-10-karmic-koala/")

> In Karmic the restart Xserver shortcut is disabled by default. Enable it thus:

1. In the menu, go to System->Preferences->Keyboard (not Keyboard Shortcuts)

2. Go to Layouts tab, click Layout options

3. Expand “Key sequence to kill  the X server”. Check “Ctrl+Alt+Backspace”

4. You’re Done.

By the way, why do people always tell you to do a google search?  I came to this thread from a Google search!:lolflag:

---

### Post by bluemushroom on 2010-03-06
Thanks dsauter for the info, the older method for killing X was/IS the best, in my opinion. Heck I can't even use the new method as it requires another key combination to create the "SysRq" plus I doubt it does what it should with the keyboard layout that I have (RO).
And on the other hand who mistakedly presses Ctrl Alt and backspace at the same time?
Newer users should at least learn some failsafe things...

Ctrl + Alt + Backspace ftw.

---

### Post by SaintDanBert on 2010-03-19
> **JohnE1 said:**
> Thank you for that simple answer!  Much appreciated.

John

On my laptop, SysRQ is a special key shift with PrtSc.
Pressing the chord listed launched a storm of gnome-screenprnt commands.
Pressing a chord with the special key shift did not restart the desktop.

~~~ 0;-Dan

---

### Post by Austin25 on 2010-03-19
I am a person with a very Linux-nonfriendly laptop who is constantly restarting, so just restarting the X-server would be much faster, so thank you very much: I did not know Ctrl+Alt+Backspce = restart X

---

### Post by JohnE1 on 2010-03-20
> **sabmo said:**
> Right-Alt + Print Screen + k

I've been having trouble with X-server locking up (no on-screen response to the keyboard or mouse).

Ctrl + Alt + Backspace doesn't work once X-server is locked up.

I've only found 2 key combinations that get any response from the system when X-server is locked up:

1. Ctrl + Alt + SysRq + K

This key combination kills X server, but does not restart it; I'm simply left staring at a blank screen.

2. Ctrl + Alt + SysRq + B

This key combination reboots the machine.

---

### Post by SaintDanBert on 2010-03-22
> **JohnE1 said:**
> 
...
I've only found 2 key combinations that get any response from the system when X-server is locked up:

1. Ctrl + Alt + SysRq + K

This key combination kills X server, but does not restart it; I'm simply left staring at a blank screen.
...


If you have a shell prompt once X stops, simply restart the desktop
```

user@host:/path/ $ startx

```

You may need to press CTRL-C or ENTER to wake shell things.
You may need to use CTRL-ALT-F2, ... to reach a console shell.

~~~ 0;-Dan

---

### Post by JohnE1 on 2010-03-22
All I get is a blank screen, no shell prompt. If I had a shell prompt I could look at `top` and `ps` output and maybe get some idea of what's going on, zombied, etc.

I've tried Ctrl + Alt + Backspace at that point, and no response.

Just noticed your last 2 lines about getting to a virtual console, and no response to Ctrl + Alt + F2 thru F6.

I've tried everything I can think of to resolve this problem. For some reason, those of us with genuine Intel motherboards with Intel graphic chips have issues with X-server under Ubuntu, such as not being able to run Compiz. You'd have thought that having Intel would give you the most compatibility, but not the case. :(

The other odd thing about this, I've only ever had this problem with Ubuntu, never experienced anything like this with Red Hat based distros or any othe distro, but to be fair, I've never used any other distro on this particular PC (Dell Optiplex GX260). When I can get a backup device, then I might try Mint and see if I fair any better.

Thanks for trying to help!

---

### Post by SaintDanBert on 2010-03-23
> **JohnE1 said:**
> 
...
I've tried everything I can think of to resolve this problem. For some reason, those of us with genuine Intel motherboards with Intel graphic chips have issues with X-server under Ubuntu, such as not being able to run Compiz. You'd have thought that having Intel would give you the most compatibility, but not the case. :(


My laptop has a Lenovo motherboard but it has Intel graphics. I'm not having this problem at the level that you have.  Then, too, I don't use 3D effects because Compiz does not play well with "tablet-pc" features.

> **JohnE1 said:**
> 
...
I've never used any other distro on this particular PC (Dell Optiplex GX260). When I can get a backup device, then I might try Mint and see if I fair any better.


Linux Mint starts with Ubuntu Something and adds brass and polish.
For example, Mint-7 starts with Ubuntu Jaunty (v9.04). Now maybe they
add something that resolves your issues. In general Mint's additions are for things that make the out-of-box experience better. (For example,
Mint provides codecs.) You might get video and xorg tweaks as well.

~~~ 8d;-Dan

---

### Post by JohnE1 on 2010-03-24
> **SaintDanBert said:**
> My laptop has a Lenovo motherboard but it has Intel graphics. I'm not having this problem at the level that you have.  Then, too, I don't use 3D effects because Compiz does not play well with "tablet-pc" features.

When researching Compiz on these forums and launchpad, is when I discovered the known issues with Intel graphics. I gave up on running Compiz, for the most part. Periodically, I try some new solution posted on here, but so far none have worked.

> Linux Mint starts with Ubuntu Something and adds brass and polish.
For example, Mint-7 starts with Ubuntu Jaunty (v9.04). Now maybe they
add something that resolves your issues. In general Mint's additions are for things that make the out-of-box experience better. (For example,
Mint provides codecs.) You might get video and xorg tweaks as well.

~~~ 8d;-Dan

Thanks for the info on Mint. The biggest draw to Ubuntu, for me, is the CUPS and HPLIP support. I had to abandon CentOS because it was so far behind in both versions, and as such, printing support was primitive compared to what I have now. This is the closest distro to providing all the GUI features people are used to in Windows, that I've found so far.

I've been using Linux since 2002 and I'm glad to see it gaining momentum. Most people don't realize that Linux is (probably) running their cell phone and is everywhere in their lives these days. Check out the info in the link below:

[B][40-Fast-Facts-on-Linux]("http://www.baselinemag.com/c/a/Intelligence/40-Fast-Facts-on-Linux-727574/?kc=EWKNLLIN03092010STR5")
[http://www.baselinemag.com/c/a/Intelligence/40-Fast-Facts-on-Linux-727574/?kc=EWKNLLIN03092010STR5]("http://www.baselinemag.com/c/a/Intelligence/40-Fast-Facts-on-Linux-727574/?kc=EWKNLLIN03092010STR5")[/B]

---

