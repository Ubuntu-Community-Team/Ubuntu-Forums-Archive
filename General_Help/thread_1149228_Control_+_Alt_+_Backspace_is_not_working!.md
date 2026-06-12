---
title: "Control + Alt + Backspace is not working!"
date: 2009-05-05
forum: General Help
---

### Post by yousillygoose on 2009-05-05
Quick question! The title says it all! I can't restart x with the key binding.  Any idea?

---

### Post by paradigm2 on 2009-05-05
> **yousillygoose said:**
> Quick question! The title says it all! I can't restart x with the key binding.  Any idea?

They changed the key combination.

Try: 

(Alt Gr) + SYSREQ + K


Note: Alt Gr is also known as RIGHT ALT.

---

### Post by yousillygoose on 2009-05-05
What is SYSREQ?

---

### Post by Brandel Valico on 2009-05-05
If your running Jaunty then they shut it off. This is apparently an upstream thing not just a Ubuntu one. There is a simple terminal command to turn it back on

> Ctrl-Alt-Backspace disabled by default in Xorg

The Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. Users who do want this function can enable it in their xorg.conf, or by running the command dontzap --disable.  

so open a terminal and run dontzap --disable and the combo will work again

---

### Post by paradigm2 on 2009-05-05
> **yousillygoose said:**
> What is SYSREQ?

Probably also the "Print Screen" key...

---

### Post by yousillygoose on 2009-05-05
Yup! Printscreen works!

I also added that line to my xorg so that I can just control-alt-backspace!  Thanks!
Rob

---

### Post by ingeon on 2009-05-06
Any chance of getting it back in 9.10.

I don`t get why they disabled it completely.
> "The decision to disable ctrl+alt+backspace was made by the xorg developers, and affects any distribution that uses xserver 1.6.0+."[http://www.lockergnome.com/linux/2009/04/14/no-ctrl-alt-backspace-for-you-in-ubuntu/]("http://www.lockergnome.com/linux/2009/04/14/no-ctrl-alt-backspace-for-you-in-ubuntu/")

Can`t they rather use the combination twice within 2 seconds 
or three times within 5 seconds or even :-k CTRL-ALT-SPACE-BACKSPACE to kill the X server.

It`s always been great to kill and restart X when one messes around and it hangs
(without having to download or enter commands, especially in LIVE mode).
Most laptops like our HP`s use the **delete key with FN functions for 'sys rq'** and does not work.

There are various reasons for its usefulness, and here are examples
> **PryGuy said:**
> Well, Feisty never freeses in my case... Well, *very* rarely. If so I CTRL+ALT+BACKSPACE it! ;)
> **Xiborg said:**
> Hi

I have a similar problem. After shutdown the screen turns black, but the mouse cursor is still there and responsive.
I used CTRL-ALT-BACKSPACE to restart X-Server which leads me back to the login screen. From there shutdown works.

regards
Xiborg

I also liked the idea of a taskmanager combination idea like windows nt based ctrl-alt-delete concept.

---

### Post by xdevnull on 2009-05-06
AAARRRGGGHHHH!!!!!

Does that some my opinion up?

By the way, when I run dontzap - guess what I get...

> bg@slim:~$ sudo dontzap --disable
[sudo] password for bg: 
sudo: dontzap: command not found
bg@slim:~$ dontzap --disable
The program 'dontzap' is currently not installed.  You can install it by typing:
sudo apt-get install dontzap
bash: dontzap: command not found


---

### Post by rbc on 2009-05-06
Do as it suggested
sudo apt-get install dontzap. Then when it finishes run the other command, sudo dontzap --disable

---

### Post by BDNiner on 2009-05-12
after running
```

sudo dontzap --disable

```
nothing happens. 
```

(Alt Gr) + SYSREQ + K

``` 
works but it is kinda awkward

---

### Post by coldReactive on 2009-05-12
Yeah, running
```
(Alt Gr) + SYSREQ + K
```

freezes my system on a black screen with a frozen mouse cursor and I have to do a hard shutdown by holding the power button.

---

### Post by xdevnull on 2009-05-19
This is broken and someone should submit a bug report to Xorg (I guess that's me).  alt+prtScr+K doesn't work on laptops that have a Fn key that makes Fn+K=2.  In fact when I tried it I got so many "Save desktop screenshot" windows I ended up having to power-cycle!

---

### Post by crlinux on 2009-05-19
Try this:
press and hold ctrl + alt
press and release SysReq then K

---

### Post by ingeon on 2009-07-27
To accomodate the newbies they have disabled ctrl-alt-backspace.
Can they at least include the dontzap in the vanilla edition for Karmic Koala for the normal linux users that always want to --disable it, it`s not restricted it is?

---

### Post by moster on 2009-07-27
Whoever think of this his salary should be shrink by 20% for few months.

When I (and not only I) came to ubuntu ctrl-alt-backspace was not "problem". And if it was to someone, disabling it make new problem to someone else then. Ubuntu has far more greater problems then this utterly stupid one to "solve".

Salary from this guy should go to guy who think of "100 papercuts."

---

### Post by DaithiF on 2009-07-27
theres no need to install dontzap to give you back your ctrl+alt+backspace, just add the flag to your xorg.conf file:

```
Section "ServerFlags"
    Option "DontZap" "false"
EndSection
```

Users who know about & want this feature surely know enough to figure out how to enable it for themselves.  

New users on the other hand are certainly not going to know about the feature, or know enough to disable it, and I'm sure an inadvertent restart of X losing any work they have in progress is likely to be a very discouraging experience for them.  So it seems like a very sensible decision to default this to off in jaunty, and I'm sure it'll stay that way in karmic.

my 2 cents :)

---

### Post by raronson on 2009-07-27
Alternatively, if you're having problems with X that you'd traditionally fix by using Ctl-Alt-Delete, you could always do the following:

1. Press Ctl-Alt-F1.  This will take you to tty1 (and if you're curious, tty7 is where your graphical environment is; you can switch back using Clt-Alt-F7)

2. Login using your user/pass

3. then 
```

sudo /etc/init.d/gdm restart

```This will essentially have the same effect as a Ctl-Alt-Delete.

---

### Post by moster on 2009-07-27
Funny, I did not read one post of someone "Hey, I press control-alt-backspace and all went black", but I read 100 posts "What the hell happend with control-alt-backspace?"

I know you guys just want to help...

---

### Post by raronson on 2009-07-27
So... two Ctl-Alt-Delete sequences within two seconds does the trick.  When I did it, I had to click on the desktop after the sequence to bring up the dialogue.  Nice to know.  Weird, but nice to know.

---

### Post by moster on 2009-07-27
@rorason
At my ubuntu 9.4 when I press once Ctrl-Alt-Del it show window Shutdown-Restart-Suspend-...
Pressing twice do nothing.

In clean 9.4 in virtualbox, once and twice do nothing. I made several attempts. Trough virtualbox menu and manually. Nothing.

Strange behaviour. I give up for now, I will deal with it when I needed it actually to not tire myself too much with someone joke.

---

### Post by raronson on 2009-07-27
I'm testing Karmic not sure why it's different (maybe I need to do a clean install instead of continuing to work with the upgrade).  I don't use the feature that much anyway.  It's just kind of a curiosity, and I don't see why X devs changed to begin with.  Pressing Ctl-Alt-Delete isn't really something that I've found to happen by accident.  Ah well, change noted.

---

### Post by DaithiF on 2009-07-27
Just to be clear though, theres a difference between 
Ctrl + Alt + Backspace
and
Ctrl + Alt + Delete

Ctrl + Alt + Backspace was a kind of instantaneous kill-switch for X, it is disabled in Jaunty unless you make the changes described earlier in this thread.

Ctrl + Alt + Delete is the traditional "I'd like to shutdown | restart | suspend | hibernate my computer" command that pops up a dialog asking what you want to do.  Thats still there in Jaunty at least, and I'd be surprised if that was changing in Karmic.

---

