---
title: "Accidentally pressed CTRL-ALT-BACKSPACE"
date: 2009-04-16
forum: General Help
---

### Post by flyingmonkiesiscool on 2009-04-16
Oh god... I accidentally pressed control alt backspace, the computer just like died. Turned it on, AND IT SHOWED ME THE COMMAND LINE! I'm so scared. How do I turn X.Org back on again? Please.

---

### Post by blazemore on 2009-04-16
Okay relax, reboot it might work again.

Try logging in from the command line, and running
```
sudo reboot now
```
Enter your password and it will reboot.

Just out of interest, how did you *accidently* hit Ctrl+alt+backspace?

---

### Post by flyingmonkiesiscool on 2009-04-16
I just tried that, but I get the following things:
Boot from (hd0,0) ext3 [lots of numbers here]
Starting up ...
Loading, please wait...
usplash: Setting mode 1152x864 filed
usplash: Using mode 1024x768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/[more numbers]) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/[more numbers]
kinit: No resume image, doing normal boot...
Ubuntu 8.10 Inspiron-Laptop tty1
Inspiron-Laptop login:_

I think I broke it... :(

---

### Post by abn91c on 2009-04-16
> **flyingmonkiesiscool said:**
> I just tried that, but I get the following things:
Boot from (hd0,0) ext3 [lots of numbers here]
Starting up ...
Loading, please wait...
usplash: Setting mode 1152x864 filed
usplash: Using mode 1024x768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/[more numbers]) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/[more numbers]
kinit: No resume image, doing normal boot...
Ubuntu 8.10 Inspiron-Laptop tty1
Inspiron-Laptop login:_

I think I broke it... :(
if it is a [COLOR="Red"]initramfs[/COLOR] prompt type```
exit
```

---

### Post by Therion on 2009-04-16
> **flyingmonkiesiscool said:**
> 
Inspiron-Laptop login:  **[COLOR="Red"]<---**[/color] Enter username and and password.
Then type in: **startx**

Report back with findings.

---

### Post by flyingmonkiesiscool on 2009-04-16
That didn't work either, it just logged me out.

I don't have much experience with Ubuntu or Linux in general, I don't know what intramfs is. I was logged on while I accidentally killed X.

---

### Post by Daisuke_Aramaki on 2009-04-16
if i am right startx requires an xinit script, which i am not sure the op might have. Don't panic. Once your are in your tty login, login with your username and password. and then do this to stop and start your gdm, you will get to the login screen.

```
sudo /etc/init.d/gdm stop
```

then again


```
sudo /etc/init.d/gdm start
```

you should be in your gdm login. then business as usual.

---

### Post by flyingmonkiesiscool on 2009-04-16
Startx told me:

Data incomplete in file: "/etc/X11/xorg.conf"
     InputDevice section "Synaptics Touchpad" must have a driver line
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error

---

### Post by Peasantoid on 2009-04-16
Methinks you borked your xorg.conf. I recommend keeping it backed up for precisely this purpose.

Post it up so we can pinpoint any errors.

---

### Post by flyingmonkiesiscool on 2009-04-16
You're right, I messed it up. Then, I used vim, which I find quite a scary program to delete the stuff I wrote. Then, I turned it off and turned it on and WOW! Thanks guys, it's alive and well now!

I tried following a tutorial to make Ubuntu recognize Synaptics multitouch. Won't do that again anytime soon. :D

By the way, I accidentally hit it because I typed CTRL-BKSP to delete a word and accidentally added Alt. I hope they do get rid of that by default.

---

### Post by hikaricore on 2009-04-16
> **flyingmonkiesiscool said:**
> By the way, I accidentally hit it because I typed CTRL-BKSP to delete a word and accidentally added Alt. I hope they do get rid of that by default.

Not going to happen.  This key combination is very hard to press by accident.
Your thread while possibly real seems a lot like a troll, in the future be a bit more calm and descriptive.

---

### Post by Bios Element on 2009-04-16
I'm sorry if I'm mistaken but I gotta say, This seems like a troll-ish post to me.

I've yet to see a post where someone accidentally hit CTRL-ALT-BACKSPACE until this one. The biggest argument for it was that users hit it by accident and yet there wasn't a single post until now. Not only that, but CTRL-ALT-BACKSPACE doesn't bork a system. Someone else will but CTRL-ALT-BACKSPACE just kills x and it should come back seconds later. Since it IS already being disabled by default upstream with no discussion about it. Just some food for thought.

---

### Post by Therion on 2009-04-16
I'd just like to add that next time you bork your system by editing, oh I don't know... Say a configuration file for instance; feel free to MENTION that fact up front.  

Just a handy little troubleshooting tip to keep tucked away in the back of your mind.  :)

---

### Post by hikaricore on 2009-04-16
Hopefully the [1,168 to 160 landslide vote]("http://ubuntuforums.org/showthread.php?t=1040988") made the devs reconsider disabling such a useful key combo.

---

### Post by flyingmonkiesiscool on 2009-04-16
Yeah, sorry. It was my uninformed editing of the config file that messed it up. CTRL-ALT-BKSP just restarted x server, which actually did the effect.

I was following this tutorial: [http://techdigger.wordpress.com/2009/04/02/multitouch-on-synaptics-trackpad-on-linux/]("http://techdigger.wordpress.com/2009/04/02/multitouch-on-synaptics-trackpad-on-linux/") and that's what messed it up.

I wasn't trolling, I was just freaked out because I was left without a GUI. I just found out about the debate about CTRL-ALT-BKSP disabled by default when I was looking up how to solve this problem.

Oh, and I actually pressed CTRL-ALT-BKSP because I wanted to see the config editing take effect. I said I pressed it by accident to look less stupid :D. It didn't work.

---

### Post by hikaricore on 2009-04-16
Lying for any reason on a help forum for any reason simply complicates things, please do not do it again.
However since you fessed up it helps your case a little bit, just be aware others may not accept your admitance and may ignore your posts in the future.

---

