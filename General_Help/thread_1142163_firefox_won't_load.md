---
title: "firefox won't load"
date: 2009-04-28
forum: General Help
---

### Post by hortstu on 2009-04-28
I'm using intrpid ibex

I was doing some updates through the update manager while simultaneously using the internet.

Everything locked up.  I thought it might straighten itself out if I left it alone for a few minutes and let the updates finish but no such luck.  Finally I shut down and restarted.

After the restart I tried to start firefox and it did everything normally but then the tab at the bottom disappeared and firefox never started.

Then I tried running the update manager again but the firefox updates weren't there.

After that a "an error occurred" message popped up.

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct problem

E:_cache->() failed, please report.

Any help will be appreciated.  I have no idea what to do.

Thanks.

---

### Post by CMJ Tech on 2009-04-28
> **hortstu said:**
> 

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct problem

E:_cache->() failed, please report.



Thanks.

I believe you need to open up a terminal window and run the command 'dpkg --configure -a'
That should complete the install of the package that was interrupted.

---

### Post by Kareeser on 2009-04-28
CMJ: That works, but the firefox update DOES NOT COMPLETE.

hortstu, workaround:
```
sudo apt-get install firefox-3.5
```

Run with "/usr/bin/firefox-3.5"... that's the best I can offer until this is sorted out!

---

### Post by hortstu on 2009-04-28
Thanks.  I thought it might be that simple but didn't want to screw anything up.  I appreciate the encouragement as I'm still a little timid about the terminal.

---

### Post by hortstu on 2009-04-28
forgive my ignorance kareeser

> sudo apt-get install firefox-3.5
this goes in the terminal...

but this part goes where?

> "/usr/bin/firefox-3.5"

Thanks

---

### Post by Kareeser on 2009-04-28
By default, since firefox-3.5 is a beta, it won't run with the switch "firefox".

You'll have to type /usr/bin/firefox-3.5 to get firefox-3.5 to open up.

---

### Post by Linuxuntuub on 2009-04-28
Format time, lol.

---

### Post by Kareeser on 2009-04-28
While fun, I just formatted this laptop, too :(

I'm sure there's a way to completely annihilate firefox-3.0.10 and reinstall it from the repos... but for some reason, [whatever I've tried doesn't work](http://ubuntuforums.org/showthread.php?t=1142142).

---

### Post by hortstu on 2009-04-28
hopefully the next time I see this thread it will be from ubuntu.

---

### Post by Kareeser on 2009-04-28
Basically, what happened _should not have happened_. Something went wrong with the update, and the firefox install was botched.

Firefox-3.5 is the beta... which installs itself separately, which is why you should be able to use it.

---

### Post by Sef on 2009-04-28
> I believe you need to open up a terminal window and run the command 'dpkg --configure -a'


To open a terminal window:  Applications > Accessories > Teminal


This code is this:

```
sudo dpkg --configure -a
```

Copy and paste it in your terminal.

---

### Post by Kareeser on 2009-04-28
Mm. I'm an idiot. I've been uninstalling the wrong package.

Purging "firefox-3.0" and reinstalling that package seems to have helped. I've run across another problem, but I think it might be different from this one.

---

### Post by hortstu on 2009-04-28
ok I'm back...

sef,
I can't copy and paste anything.  I run a dual boot with windows and need to switch to windows in order to get online and seek your help.  I will try your suggestion when I get back over to linux... and thanks for assuming I don't know where the terminal is and helping me out with that... I'm really a quarter step beyond that...

kareeser,
I tried your suggestion but I got the same error message again.

I'm going back to try sef suggestion then I'll check back in.

---

### Post by Kareeser on 2009-04-29
Alright hortsu, here are the commands I used to restore firefox-3.0

```
sudo apt-get purge firefox-3.0
sudo apt-get install firefox-3.0
```

That SHOULD work.

If you get this error message:
"Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*."

Run:
```
sudo apt-get install --reinstall xulrunner-1.9 xulrunner-1.9.1
```

---

### Post by hortstu on 2009-04-29
Thanks for everyones help.  I'm back on linux.

"sudo dpkg --configure -a" worked for me.  This is my first real need for the terminal so I wasn't using "sudo" at first.

I guess this was a simple problem but I wouldn't have solved it without ubuntu forums and all you nice people.

Thanks again.

---

