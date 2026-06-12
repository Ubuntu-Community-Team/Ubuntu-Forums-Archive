---
title: "Cannot log on error message...need help ASAP!"
date: 2008-12-17
forum: General Help
---

### Post by NoL618 on 2008-12-17
I am selling my laptop and trying to erase all of my info, like user name, etc.  
When I updated my info in the users and groups tab, i thought I was doing everything right.  I made it so that you didnt have to log it when you turned the comp on...

I restarted and now its still asking for a user name and password and giving me this error message:

"your home directory is listed as: '/home/user1' bit it does not appear to exist.  So you want to log in with the / root directory as you home directory?  it is unlikely anything will work unless you use a failsafe session."

I click yes...

Then is says " users $HOME/.dmrc file is being ignored. This prevents the default session and languages from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory myst be owned by user and nor writable by other users."

I click ok....

Then it says; "your session ony lasted less than 10 seconds.  If  you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space.  Try logging in with one of the failsafe sessions to see if you can fix this problem.  

I have no idea what is going on....and why this is happeneing....It needs to ship ASAP and I cannot fix this!

HELP!
Thanks

---

### Post by kanikilu on 2008-12-17
Maybe someone else can help you with the specific problem you are having, but I was just thinking, if you are selling the computer, it would probably be safest to do a "secure wipe" of the disk.

If you have the time, I would recommend downloading an [Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html") (UBCD) ISO and making a CD. Then boot up the computer and use one of the drive wiping tools such as *Darik's Boot and Nuke*.

Doing this will ensure that any personal/confidential information (credit card numbers, passwords, etc) is permanently removed and irrecoverable by whoever ends up with the computer next.

Also, you won't have to spend time trying to troubleshoot a computer you are getting rid of anyways.

And...if the machine has to have an OS on it when you ship, just install a fresh copy of Ubuntu, that takes all of, what, about 30-45 minutes, these days?

---

### Post by NoL618 on 2008-12-17
So i download that nuke and boot thing onto a cd and it will take out everything? even the OS?  
I can install ubuntu back on it with my live cd?

Also, i cannot log on still....will i be able to erase everything with the nuke an boot even if I cant log on?

---

### Post by adult swim on 2008-12-17
nuke and boot will completly wipe the drive and its going to take a long time!  if you are giving away your laptop, your best bet  is to do that and then reinstall ubuntu

---

### Post by jenkinbr on 2008-12-17
> **NoL618 said:**
> So i download that nuke and boot thing onto a cd and it will take out everything? even the OS?  
I can install ubuntu back on it with my live cd?

Also, i cannot log on still....will i be able to erase everything with the nuke an boot even if I cant log on?
Yes - You don't need to log in on most live cd's. If you do, it's usually root with a password of root

---

### Post by NoL618 on 2008-12-17
about how long does it take? to wipe out the drive?

also, i dont have an issue with the live cd, rather I cannot log onto the laptop.

---

### Post by jenkinbr on 2008-12-17
> **NoL618 said:**
> about how long does it take? to wipe out the drive?

also, i dont have an issue with the live cd, rather I cannot log onto the laptop.
That will depend on the drive you have along with other hardware - I would probably give it 4 - 6 hours.

---

### Post by kanikilu on 2008-12-17
Boot and nuke has several options, and depending on the size of the drive and how many passes you want it to make, it can indeed take a long time.

You just have to make a choice between time and security. A 1-pass wipe should be relatively quick but not as secure. A 5-or-more pass wipe is overkill in my opinion and can take all day (or longer!). A 3-pass is the one I usually use, it takes several hours, but you can rest pretty well knowing the data is well and truly unrecoverable by anyone but the NSA :P

---

### Post by NoL618 on 2008-12-17
i just tried the boot and nuke as well as just booting from the live cd....

i cannot get past the log in screen!!! it will not let me log on!

please help....

Thanks

---

### Post by kanikilu on 2008-12-17
What login screen are you referring to? Did you make a UBCD and boot off it? Neither UBCD or the Ubuntu live CD should be asking you to login. Are you sure you are actually booting off the CD and not in fact booting off the hard drive?

On some computers you have to go into the BIOS setup and move the CD/DVD drive up in the boot order to take precedence over the hard drive. The exact steps to do this vary, so I can't really give you specific instructions. I know on Dell computers and I think IBM/Lenovo, if you press F12 as soon as you start the computer, it should bring up a temporary boot device menu where you can select your CD/DVD drive.

Once you actually do boot off the UBCD, you can refer to this tutorial on how to use DBAN:

[http://www.ultimatebootcd.com/dban.html](http://www.ultimatebootcd.com/dban.html)
> i cannot get past the log in screen**!!!** it will not let me log on**!**

...no need to yell, we can all hear you just fine :P

---

### Post by NoL618 on 2008-12-18
lol...sorry about that....more of a stress then yelling!

anyway, once i have completed the boot and nuke, do I install from the live cd, or from the cd that came with the computer?  its a dell mini that was originally installed with ubuntu.  

:KS

---

