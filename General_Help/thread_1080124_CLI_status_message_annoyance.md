---
title: "CLI status message annoyance"
date: 2009-02-25
forum: General Help
---

### Post by doktor_apokalypse on 2009-02-25
Okay, I'm not sure what these messages are technically called, but they are really bugging the bejeezus out of me.  I use the virtual terminals and screen extensively; I'm becoming a total geek for the CLI.  I just love it.  But I'm having an issue with messages, like the following:

* Stopping anac(h)ronistic cron daemon
* Starting anac(h)ronistic cron daemon


[some message about the noise floor on my wireless card]

etc., etc., etc..


It's like, I'm just pecking away at some Perl code in nano and, hey, here's some info about your usb hdd's bad sectors right in the middle of everything.  And it seems like the system knows when I don't want to be bothered with this junk and the random-system-info fairy starts really acting up (let's not bring Occam's Razor into this, I've *seen* the damn thing).

I'm sure there's a way to send this to a null device or dump it to a text file instead of the terminal, but I don't even know what the things are called, so that's really nipped my research in the bud.  I know I can use xterm or whatever to circumvent this, but I really would rather use my tty(X).  Any tips would be appreciated. ](*,)

---

### Post by KeyserSoze93 on 2009-02-25
You could try pressing Alt + SysRq + 0 (all at once. SysRq shares a key with PrintScrn)

From here:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

The numbers 0 to 9 set the console log level.

That might help.

---

### Post by doktor_apokalypse on 2009-02-25
Okay, I tried the Magic SysRq business, alas, no luck. :-s This only makes varying-degrees-of-more messages, never less.  On the positive side, I learned something new (I was not, hitherto, savvy to the SysRq key's function), and now I have reason to believe that I'm dealing with the "console log", so at least that's a lead. =D> Bravo and thanks.

---

### Post by unutbu on 2009-02-25
Press Ctrl-Alt-F2. The messages you are seeing are printed to the first virtual terminal. Ctrl-Alt-F2 will take you to the second virtual terminal, which should be free of such noise.

---

### Post by doktor_apokalypse on 2009-02-25
> **unutbu said:**
> Press Ctrl-Alt-F2. The messages you are seeing are printed to the first virtual terminal. Ctrl-Alt-F2 will take you to the second virtual terminal, which should be free of such noise.



I [s]knew[/s] suspected this reply would come and I should have addressed this in my first post: 
the messages appear in every terminal, 1-6, whichever I happen to be using at the time.  

Seriously.  I wish I was just making that up.  

Also, I tried editing /etc/syslog.conf and just commenting everything out.  That appears to be the wrong approach, so back to square one.  C'est la vie.


EDIT: If it helps, I am on Intrepid, AMD64.

---

### Post by brian_p on 2009-02-25
> **doktor_apokalypse said:**
> 

Also, I tried editing /etc/syslog.conf and just commenting everything out.  That appears to be the wrong approach, so back to square one.  C'est la vie.

What does

```
cat /proc/sys/kernel/printk
```

say?

Alter for the present session with:

```
sudo echo "4 4 1 7" > /proc/sys/kernel/printk
```

Alter permanently with:

```
sudo editor /etc/sysctl.conf
```

---

### Post by doktor_apokalypse on 2009-02-25
@brian_p:

```
cat /proc/sys/kernel/printk
```

yields 

```

4	4	1	7

```

already.

so ... ugh, this is frustrating. ](*,)  thanks, though.


EDIT: I tried updating printk with several different values, including 4 1 1 7, 1 1 1 7 and 0 0 0 0 as well as some others.  this had no effect on my system's blasted verbosity.

---

### Post by brian_p on 2009-02-25
> **doktor_apokalypse said:**
> 

so ... ugh, this is frustrating. ](*,)  thanks, though.

The idea was for you to alter the levels to suit your needs. On this machine:

```
brian@laptop:~$ cat /proc/sys/kernel/printk
7       4       1       7
```

---

### Post by doktor_apokalypse on 2009-02-25
> **brian_p said:**
> The idea was for you to alter the levels to suit your needs. 

After a moment's reflection I did realize your intention, alas, nothing seems to change.

---

### Post by doktor_apokalypse on 2009-02-25
Okay, I was a little too hasty to decide nothing was changing. :redface:
After some slightly-more detailed testing (unplugging, replugging usb, which *was* giving me like 15 lines of info), using
```
sirius@dogstar:-$ sudo su 
[sudo] password for sirius: 
root@dogstar:/home/sirius# echo "1 1 1 1" > /proc/sys/kernel/printk

```

*does* clear up a lot, if not all, of the verbosity from printk, so thanks brian_p, that really did work.  I think the only msg I'm getting now is from the anacron daemon, but none of the other junk.


EDIT: I just noticed that I used the word "alas" [s]3[/s] 4 times in this thread.  Must be stuck in my neuro-semantic processor. :)

---

### Post by doktor_apokalypse on 2009-02-27
I've been tweaking this for a couple days now, and so far I've managed to cut out quite a few messages. There's still a couple of messages I'm getting including some from anacron, but there's *just this one* that continues to be a royal pestilence, a plague of monstrous proportion and is becoming *the bane of my very existence*.  You may think I'm blowing this out of proportion, but I guarantee you, gentlemen, I  am  not. 



The anacron daemon, which I haven't really tried to fix yet, is not the cause of my grief as it only  occurs when I stop / start external power. I know when that's going to happen, I know what's responsible for it and it's not bothering me much; I will deal with it later.

Rather, the alert about 'noise floor calibration' on my 802.11 interface, which I mentioned briefly before, is a cosmic PITA.  I am at wit's end with this guy.  Here's a sample:

```

[32258.160519] ath5k phy0: noise floor calibration timeoout (2412 MHz)

```

This bugger pops up quite frequently (over 9000 times) to say 'hi, I know you're working, but I was feeling kind of lonely...' 'hi, I know you're working, but I was feeling kind of lonely...' 'hey, how come you never return my calls?'. 

I'm not sure which process is creating this message; I don't think it's printk; since I edited that setting, I haven't been recieving scores of messages about USB and some others, but then again, I don't know that much about it.  If anybody could point me in the right direction that would be fantastic.  I'm just not sure where to look for solutions.

---

### Post by Denestria on 2009-02-27
Maybe the comments for this bug report will help you get rid of the problem instead of just the message.

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423)

---

