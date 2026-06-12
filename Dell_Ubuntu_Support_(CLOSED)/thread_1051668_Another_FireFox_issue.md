---
title: "Another FireFox issue"
date: 2009-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Andydg on 2009-01-26
Just to start off I did read the thread just below this one but it was solved when it was figured out the problem was due to low hdd space...I checked and I definitely don't have that issue.

This is a Dell Mini-9 with Ubuntu Hardy, if you need more specs please just let me know what you need and I'll find it.

This afternoon I saw the update exclamation thing up in the corner...I hesitantly updated since last time I did that I lost all setting, bookmarks, and add-ons in FireFox, but I figured since I never went back and bothered to get refill my bookmarks and add-ons are so easy to find why not upgrade.  

I should officially have any and all decision making privileges removed!

FireFox just plain won't open anymore.  I click on the button on the taskbar to open it and is says "web browser is starting" and the little circle is circling but after ~30 seconds it disappears...

Without having an internet browser I'm probably going to have some trouble copying and pasting the outputs from any commands I type in...but I can try to figure something out there.

Thanks a lot for reading all of this and sorry if I seem angry anywhere...I'm just extremely frustrated.  I'll probably be checking back tomorrow morning before I head to class.  Thanks again!

---

### Post by sirebral on 2009-01-27
Can you go into your system monitor and see if there is another firefox process running?

---

### Post by Andydg on 2009-01-27
I did and there's not a FireFox process running.

Thanks for the reply!

---

### Post by sirebral on 2009-01-27
type 

firefox

in your terminal and report the errors.

---

### Post by Andydg on 2009-01-27
Nothing came up...it just brought me straight down to another line.  I'm pretty new to this...does that mean no errors?

---

### Post by sirebral on 2009-01-27
no...
It means that firefox is not starting.  Hrm....

You might try a restart?  

You might try re installing Fire Fox from Synaptic.  I hate even saying that.

What version of Ubuntu?

---

### Post by Andydg on 2009-01-27
I've already restarted a few times and I tried re installing through that Synaptic thing and all seemed to go well until I tried to start it up.  I've also restarted since I tried to re install.

Straight out of the System Monitor I'm running
Ubuntu
Release 8.04 (hardy)
Kernel Linux 2.6.24-19-lpia (not sure if that's an I or l on the netbook)
GNOME 2.22.3

---

### Post by sirebral on 2009-01-27
alright we have the same system.

I am not the best when it comes to these problems but I offer as much help as I can.  I have not read this, but this query might help: [http://kb.mozillazine.org/Firefox_:_Issues:_Firefox_Won%27t_Startup](http://kb.mozillazine.org/Firefox_:_Issues:_Firefox_Won%27t_Startup)

---

### Post by Andydg on 2009-01-27
Thanks for the link...I checked it out it looked like it only applied if I had Google Desktop installed or if I had installed it using sudo.

Thanks though I really appreciate it...I'm off to bed I'll check back in the morning.

---

### Post by skroops on 2009-01-27
when you reinstalled firefox did you completely remove it?

Try choosing a complete remove of firefox, then apply.  Then install and apply.

If that doesnt work, you may want to try moving your firefox profile, to see if maybe one of your add-ons is conflicting.  I think it's in .mozilla/web browser

Sorry if neither of those help, but if they dont, you may just want to consider installing the seamonkey-browser package and just removing firefox.  It should have the same functionality as firefox (it's based on firefox).  I know that's an ugly solution but it should work.

---

### Post by Andydg on 2009-01-27
Damn neither of those worked either...something about this computer really hates Firefox...

Thanks for the reply

---

### Post by skroops on 2009-01-27
So did you try seamonkey-browser?  [IMG]http://www.softpedia.com/screenshots/SeaMonkey_1.png[/IMG]

  
It's just like firefox, compatible with firefox extensions, etc.  just sudo apt-get install seamonkey-browser

---

### Post by Andydg on 2009-01-27
Ok cool thanks...SeaMonkey works!  So now atleast I have a browser for that computer.

---

### Post by ugm6hr on 2009-01-28
If you prefer Seamonkey, that's fine.  But if you don't need the Email / html editing etc, and just want the plain old "Web Browser" back:

[http://ubuntuforums.org/showthread.php?p=6628108#post6628108](http://ubuntuforums.org/showthread.php?p=6628108#post6628108)

Read through and check posts 8-10 for a likely reason why things aren't working (and the solution).

---

### Post by Andydg on 2009-01-28
Oh wow...that link worked!  Thank you so much...I owe you one!  How did that get changed to web browser instead of Firefox because I didn't do that myself...was it the update?  Thanks again!

---

### Post by ugm6hr on 2009-01-28
> **Andydg said:**
> was it the update? 

Unfortunately, yes.

I think if you first used Firefox after the first update, the most recent update messed everything up.

In trying to "fix" their original error, Dell created a raft of new ones. Thanks again!

---

### Post by Andydg on 2009-01-28
OK this sucks...I thought I had it fixed, but now whenever I close FireFox and try to open it back up it won't work.  So I checked to see about that folder renaming thing and now it's making a new folder everytime I fix it, close it, then reopen.  That sucks but what also sucks is when it does launch it treats it like its a fresh install asking me if I want to import bookmarks and settings from some old Netscape  6.1 or something.  

I think this computer is broken or something because I've never experienced a machine doing something like this.

---

### Post by ugm6hr on 2009-01-29
> **Andydg said:**
> I think this computer is broken or something because I've never experienced a machine doing something like this.

This is a software issue.

Post output from:
```
ls -l ~/.mozilla
```

---

### Post by Andydg on 2009-01-29
Here ya go

```
andy@andy:~$ ls -l ~/.mozilla
total 32
-rw-r--r-- 1 andy andy 1042 2009-01-28 16:25 appreg
drwx------ 4 andy andy 4096 2009-01-27 13:30 default
drwx------ 3 andy andy 4096 2008-12-25 02:36 extensions
lrwxrwxrwx 1 andy andy   27 2009-01-28 16:00 firefox -> /home/andy/.mozilla/firefox
drwx------ 4 andy andy 4096 2009-01-11 14:12 firefox1.bak
drwx------ 3 andy andy 4096 2009-01-28 11:02 firefox.bak
-rw-r--r-- 1 andy andy  536 2009-01-28 16:26 mozver.dat
-rw------- 1 andy andy  777 2009-01-28 16:25 pluginreg.dat
drwx------ 3 andy andy 4096 2009-01-28 16:06 web browser
andy@andy:~$ 

```

Hope I did the tags right...

---

### Post by ugm6hr on 2009-01-29
Wow. What a mess.

You have a shortcut that leads to itself (firefox), a couple of firefox backups (firefox.bak and firefox1.bak) in addition to where I *presume* your profile is in "web browser"

You also have a couple of folders I don't - but I suspect they are not the problem.

Your options: 
1. Just delete all of those folders and start again.  
2. Look through those folders for the profile you want to keep, delete the rest, and then rename it to "firefox"  Then create a shortcut from "web browser" to firefox.

---

### Post by Andydg on 2009-01-30
Ok...I just did that...and it WORKS!  Thank you!

---

