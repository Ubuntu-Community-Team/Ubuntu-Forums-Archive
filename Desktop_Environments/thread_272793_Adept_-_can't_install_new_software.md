---
title: "Adept - can't install new software"
date: 2006-10-07
forum: Desktop Environments
---

### Post by hodad on 2006-10-07
Just](*,)  left using Suse Linux because I couldn't get YaST to install new software packages on the PC. I tried for about a year(!).  Always "unresolved conflicts", and I haven't a clue how to deal with them...

On a friend's suggestion, I just installed Ubuntu, and, well, you guessed it, I can't install software.   The Adept screen looked friendly enough, but just about the time I thought I might be getting close, I get the following message:

"The APT database could not be opened, this may be caused by incorrect configuration...  Try  running apt-setup or apt -get update...", and I'm kicked out of Adept](*,) .  

Needless to say, I tried both commands from the shell, and all I get is "no such command". Now Adept cannot be accessed.  I suppose I could just wipe the hard drive again and reinstall Ubuntu, but I'm tired of doing that (3 times already today).

Is it possible to load new software in Linux, or must you just be satisfied with what is installed automatically when you buy an off the shelf new set of CD's?  

I don't have a lot of time to deal with futzing with computers;I'd go with an Apple if I had the money, but, unfortunately, I don't.  Also, being over 50 is another problem I suppose...

Anyway, sorry to vent, but if anyone can help me out I would be very thankful!
](*,)

---

### Post by lemonsCC on 2006-10-07
try
```
sudo apt-get update
```

then
```
sudo apt-get upgrade
```

you had a space in one of the commands..this could be the problem.

---

### Post by lemonsCC on 2006-10-07
Double Post....

[http://ubuntuforums.org/showthread.php?t=272794]("http://ubuntuforums.org/showthread.php?t=272794")

---

### Post by hodad on 2006-10-07
Thanks for the help. I did try that already and get:

E: Type '/home/dave/Desktop' is not known on line 1 in source list /etc/apt/sources.list
dave@dave-desktop:/$ ls

each time I try both commands. I tried changing to the root directory from home directory and repeating; same message.  I assume the command is trying to look out on the Ubuntu website, but can't get there, and to make matters worse, I'm locked out of getting any updates because Adept doesn't work (!X$<??)

---

### Post by rogier.de.groot on 2006-10-07
Could you please post the contents of your /etc/apt/sources.lst file?

---

### Post by hodad on 2006-10-07
THanks for the response- problem solved:

I went to Ubuntu, downloaded an image file for my AMD-64 machine (my firend had given me the standard PC version) and installed it.  THe simple fact of re-installing it solved the "apt" problem apparently, plus the new version is a better match for my hardware.

 Leads to a  new question, however:

1.  Whenever I installed previous Suse Linux, it would first set up a "root" account, which would subsequently be used for any administrative or system functions.  On Ubuntu, installation just asked for my name, and didn't set up a root account.  Does this mean I have root priveleges? Is this a safe way to operate? How can I create a safe "root" account?

---

### Post by GreenHawkIA on 2006-10-07
Ubuntu does give you the option of a root account, but it uses something much safer as an alternative called sudo or superuser do.  That is why each of the commands listed above has sudo in front of it.  You stay logged in under your account, but use sudo to perform tasks that would normally require root.  Therefore you must put in your password and consciously decide to do something before it happens - unlike Windows, programs just can't install themselves without your input.  For more info, this page on the wiki is very helpful:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
It contains lots of helpful information on how to use sudo, and root if you want.
One quick note...I am more than happy to help, as are many on the forums with the basics of Ubuntu (welcome aboard!).  But the resources already here are fantastic, and sometimes do a better job than we could.  Search on the forums, on the wiki, and in the [docs]("https://docs.gwos.org") before asking.  It will make you self-sustaining as a user, and you'll end up like me - just starting to turn around and help those that follow.

---

