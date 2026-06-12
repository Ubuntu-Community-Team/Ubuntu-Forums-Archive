---
title: "Firefox not working after update"
date: 2009-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfyking2 on 2009-01-18
Ok, so here's my problem.  O just updated my system, there was like 238 updates O.O  And I think one of them was updating the linux version, I dunno.  So after the update, I restart the computer, click on the little firefox icon, and it's taking like, 30 seconds to load.  And then it just closes.  Why is it doing this, and how can I fix it?  I'm running ubuntu 8.04 hardy on a dell.  

P.S. I'm writing this on IEs4linux.  And my internet connection is fine.

---

### Post by wolfyking2 on 2009-01-19
Ok, now Add/Remove is doing the same thing :mad:

---

### Post by wolfyking2 on 2009-01-19
C'mon people! (sorry, but I really need my Firefox, ies4linux is so laggy and crashes alot)

---

### Post by llamakc on 2009-01-19
Run the command "firefox" from a Terminal, and post the output back here.

```

firefox

```Also, are you positive that you do not have a running instance of Firefox on one of the other Desktops? 

What's the output of 

```

ps aux | grep firefox

```

---

### Post by wolfyking2 on 2009-01-19
output of the firs code: Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

the second one, the output is: 6378  0.0  0.1   2060   692 pts/0    R+   14:26   0:00 grep firefox

---

### Post by llamakc on 2009-01-19
Update again please.

```

sudo aptitude update && sudo aptitude safe-upgrade

```

---

### Post by wolfyking2 on 2009-01-19
It won't let me, said I needed to use dpkg --configure -a I did it and it didn't work.

---

### Post by llamakc on 2009-01-19
> **wolfyking2 said:**
> It won't let me, said I needed to use dpkg --configure -a I did it and it didn't work.
 
Please be more descriptive by cut/pasting exactly what it says. Did you remember to run it as:

```

sudo dpkg --configure -a

```

---

### Post by wolfyking2 on 2009-01-19
Yes I did exactly what you said and it didn't work.

---

### Post by llamakc on 2009-01-19
I want to help, but you need to provide the message that is spit out. "It doesn't work" is not enough information.

So, when you type `sudo dpkg --configure -a` what is the output?

---

### Post by wolfyking2 on 2009-01-19
Well, it says all these options like 'type dpkg --dpkg to lear more information.  Type dpkg --help for some help'  That thing.

---

### Post by llamakc on 2009-01-19
> **wolfyking2 said:**
> Well, it says all these options like 'type dpkg --dpkg to lear more information.  Type dpkg --help for some help'  That thing.

"That thing" is not helpful. I have asked that you cut/paste the output from the Terminal. Include what you actually type and what is returned by the system. If you want help you must be specific. 

I'm unsubscribing from the thread but hopefully someone else can help you.

Good luck.

---

### Post by gbrainin on 2009-01-20
Wow, the reward for trying to help you is being called an ugly little dick?  Tell you what, why don't we skip all the back and forth and get straight to the part where you give up, blame Linux, this board, your parents, your school, and everyone else but you for your problem, and run away.  It'll save us all a lot of time.

P.S. There is a single command which has solved this exact problem for someone else.  But you don't want to know that.

---

### Post by wolfyking2 on 2009-01-20
Thanks man...thanks alot...


P.S. if you read his posts, he wasn't trying to help me at all, just creating more problems...

---

### Post by llamakc on 2009-01-20
> **wolfyking2 said:**
> Thanks man...thanks alot...


P.S. if you read his posts, he wasn't trying to help me at all, just creating more problems...

By asking you to be specific? Is being specific going to be problematic for you?

---

### Post by wolfyking2 on 2009-01-20
No...you were kinda yelling at me to be more specific.  How much more specific can I be?  The replies I wrote were what happened, nothing else

---

### Post by llamakc on 2009-01-20
> **wolfyking2 said:**
> No...you were kinda yelling at me to be more specific.  How much more specific can I be?  The replies I wrote were what happened, nothing else

Perhaps you didn't understand what I meant. 

Do you know how to cut/paste in Ubuntu?

And what was gbrainin referring to with "ugly little ****"? 

Your problem is still solvable but you'll need to follow directions when it comes to those of use attempting to help, for free, you fix the issue.

---

### Post by wolfyking2 on 2009-01-20
I know how to cut/paste...and I know what you're talking about, but that's what I mean!  Nothing came up to copy and paste!  No errors came up!

---

### Post by llamakc on 2009-01-20
> **wolfyking2 said:**
> I know how to cut/paste...and I know what you're talking about, but that's what I mean!  Nothing came up to copy and paste!  No errors came up!

I wasn't asking for errors. I asked, and am asking, for you to share what it is you ARE doing instead of being vague like you have been here:

> 
		Well, it says all these options like 'type dpkg --dpkg to lear more information.  Type dpkg --help for some help'  That thing.

and here:

> 
It won't let me, said I needed to use dpkg --configure -a I did it and it didn't work.

So, let's try again.

Open a Terminal, and enter the following:

```

sudo dpkg --configure -a

```

Regardless of what the output is, CUT/PASTE it back here, please.

Oh, and you wouldn't happened to know what gbrainin meant by "Wow, the reward for trying to help you is being called an ugly little REDACTED?" Would you?

---

### Post by wolfyking2 on 2009-01-20
no...I don't 

here's the output:Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

---

### Post by llamakc on 2009-01-20
> **wolfyking2 said:**
> no...I don't 

here's the output:Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

Please wrap your cut/paste output in the [ code ] tags. It makes it easier for everyone here to fully get what the system is reporting apart from your own words.

Next, try running this from the Terminal. (It also completes installing packages)

```

sudo apt-get -f install

```

When it is finished, please cut/paste ALL of its output back here for us.

Also, have you tried restarting Firefox yet?

---

### Post by gbrainin on 2009-01-21
> **llamakc]Oh, and you wouldn't happened to know what gbrainin meant by "Wow, the reward for trying to help you is being called an ugly little REDACTED?" Would you?[/quote]

[QUOTE=wolfyking2 said:**
> no...I don't

Let me try to be a bit less subtle, then:

Nobody on this website is getting paid to answer your questions.  Nobody on this website is your friend, or your relative, or otherwise obligated to answer your questions.  Nevertheless, people take time to answer others' questions.  The appropriate attitude to take toward this is polite gratitude for the resource.  That means:

[LIST]
[*]If you don't get an answer, politely restate your request, don't act as if you're entitled to an answer.  Because you're not.
[*]When someone makes a suggestion, try to follow it.  If you don't understand, say so.
[*]Give people the benefit of the doubt.  Maybe you're the one who doesn't understand.
[*]Whether or not your problem is resolved, your feedback should be no worse than "thanks for trying."
[/LIST]

Instead of the above, you became increasingly antagonistic toward the person who was trying to help you, and when he gave up because you refused to either do what he requested or give any indication that you were unable to do so, you attacked him, your computer, and your parents (because obviously the problem must be anyone but you).

llamakc was not, as you incorrectly describe, "just creating more problems," he was trying to diagnose yours.  That means trying some things and seeing what happens.  The fact that what you wanted to happen didn't isn't enough detail.  The details of exactly what happens INSTEAD, which is what he was trying to get you to report back, are what helps in the diagnosis.

Yet you refused to give him the tools he needed to help you, then blamed him for not helping.

In short, you were acting like a spoiled brat, and that's why even though I found a likely answer to your problem, I'm not inclined to give it to you.

---

### Post by wolfyking2 on 2009-01-21
Didn't know about that wrap thing, sorry.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by ugm6hr on 2009-01-21
> **wolfyking2 said:**
> no...I don't 

here's the output:Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

OK.  We are going in circles here.

Can I ask what kind of Dell you have?

And can I ask that you copy and paste *everything* from the commands, **including** what you have typed in for these commands (again).

```
df
sudo dpkg --configure -a
```

It might also help to know what version of Ubuntu you are using.

---

### Post by wolfyking2 on 2009-01-22
Ok, here's what I got

user@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19030328  13351420   4719832  74% /
varrun                  257024       100    256924   1% /var/run
varlock                 257024         0    257024   0% /var/lock
udev                    257024        48    256976   1% /dev
devshm                  257024        12    257012   1% /dev/shm
lrm                     257024     39792    217232  16% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      19030328  13351420   4719832  74% /home/user/.gvfs
/dev/scd0               640226    640226         0 100% /media/cdrom0
user@ubuntu:~$ sudo dpkg --configure -a


And I'm running Ubuntu Hardy 8.04

---

### Post by ugm6hr on 2009-01-22
OK.  The dpkg command completes, with no output; this means all downloaded packages have completed installing.  The df confirms you have HD space available.

Now ensure all necessary downloads are done, and everything is fully updated.

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

Again - post everything that is output.  If possible - use the # button to quote code.

---

### Post by wolfyking2 on 2009-01-23
Uhh..none of those worked >.< they all failed, or nothing came up.

---

### Post by ugm6hr on 2009-01-23
> **wolfyking2 said:**
> Uhh..none of those worked >.< they all failed, or nothing came up.

Absolutely nothing?  Please copy & paste what you have typed in for us to check what is happening (you should do this for every command).  The dpkg command generally returns nothing if everything is configured.  But apt-get ALWAYS at least searches your repository, even if there is nothing to update.

How is Firefox behaving now?

Another command for you:
```
cat /etc/apt/sources.list
```

---

### Post by wolfyking2 on 2009-01-24
K, sorry


Heres what I got:

user@ubuntu:~$ cat /etc/apt/sources.list
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
user@ubuntu:~$

---

### Post by ugm6hr on 2009-01-24
> **ugm6hr said:**
> ```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```


Again - **post everything that is output**, including what you typed.  **If possible - use the # icon to quote code**.

And if those all work OK, let us know what happens when you launch firefox.

---

