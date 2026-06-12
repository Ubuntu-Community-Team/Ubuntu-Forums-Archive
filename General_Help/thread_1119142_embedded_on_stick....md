---
title: "embedded on stick..."
date: 2009-04-07
forum: General Help
---

### Post by LeeCrites on 2009-04-07
I'm sure this is in the wrong forum, but I'm not really sure where to put it, so I figured "general questions" was as good a place to start as any.

I have just today (literally) started loading ubuntu on my dell laptop -- apparently it is the only version that works on it. So I might just be porting all of my stuff to ubuntu, and using it from now on. At least it is working, which is a REALLY good thing!

While surfing around a while ago, I stumbled on [www.damnsmalllinux.org](www.damnsmalllinux.org) (DSL for short), which has some interesting points. One was that there was a version you could load onto a flash drive. I installed it on a 256Meg stick, and, sure enough it worked. Well... it worked as well as it could, given all of the limitations it has placed on itself.

The problem is this: in order to meet their #1 goal (under 50meg), they sacrificed a TON of stuff. Stuff that I'd like to have. They have their goals, and adding the stuff I'd want/need runs counter to them, so I'm sort of stuck.

Here's what I'd like to have (in a perfect world):
* A live version that I could burn on a (mini???) CD/DVD (and/or copy to a flash drive).
* The autoboot "stuff" on said CD/DVD (and/or flash drive) so windoze will recognize it and start up the embedded system. The DSL project uses some embedded windoze stuff to help make that happen.
* A way to customize stuff for each individual CD/DVD copy.
* Question: Is it possible to have a flash drive autoboot? I've never tried, so I don't know.

In a nutshell, we have some security issues that we are trying to address. Compliance with HIPAA requires we be able to make a positive ID on who is doing what to the patient records (which is totally stupid, since anyone can walk up to the patient record, take it out, and write whatever they want on whatever page they want).

But... this option opens up a way that we could give each employee a business card sized CD/DVD and/or flash drive that could have the specific information for them on it. And, given the fact that we'd have a complete linux system on it, we could add our own functions and such.

Since it appears that I'm moving to ubuntu, this is the logical place for me to start looking for this solution. Any clues how this could be pulled off?

Thanks muchly,

Lee

---

### Post by mb_webguy on 2009-04-07
I'm a bit confused about your goal.  You're talking about booting Linux from a disk or flash drive, but then you say:> The autoboot "stuff" on said CD/DVD (and/or flash drive) so **windoze** will recognize it and start up the embedded system. The DSL project uses some embedded windoze stuff to help make that happen.Linux is not Windows.  It is not an application that runs on Windows.  It has nothing to do with Windows at all, except that it does the same basic job as Windows.

If you have a server that provides the patient records and logs activity, then you could have a customized LiveCD or LiveUSB, or even an actual USB pendrive Linux installation, for each user.  They'd then have to boot the computer from that disc or USB drive, which would allow them to access the server.

This is a pretty bass-ackward way of doing things, though.

The best way to do what you seem to want to do is to set up a server that has a separate account for each user.  (Linux was designed as a multi-user system, after all.)  Then all of your workstations could have a very basic Linux installation -- which could even be booted from a CD -- which would allow them to remotely log in to their account on the server.  You could set all of the accounts to automatically log out after a period of inactivity, requiring users to log in to view the patient records, and prevent one person from using another person's account that was left open.

This would allow a greater degree of control over user accounts, as well as access to the patient records.  It's a heck of a lot easier to administrate, as well.

---

### Post by LeeCrites on 2009-04-07
I guess I neglected to mention that I've been working as a systems analyst since 1975, so I really do have a clue. I also know what I don't know, and have found that it is virtually always better to ask for help than to attempt to solve everything on your own.

> **mb_webguy said:**
> If you have a server that provides the patient records and logs activity, then you could have a customized LiveCD or LiveUSB, or even an actual USB pendrive Linux installation, for each user.  They'd then have to boot the computer from that disc or USB drive, which would allow them to access the server.

So the 50 - 75 people who access the patient record during the day, all day long, 24 hours a day, should each REBOOT the computer??? I should explain to Dr Schmoe that he needs to stand there for several minutes while a nurse logs off and they reboot the computer so he can log in and do some work...

Probably not.

> **mb_webguy said:**
> This is a pretty bass-ackward way of doing things, though.

To say the least. I know your comment was hyperbole, so I used it as a springboard to describe more of the problem I'm working with.

> **mb_webguy said:**
> The best way to do what you seem to want to do is to set up a server...

That would be wonderful, and, yes, I know how to pull that off, and yes, I have already attempted to do so. The problem is that I don't have computers everywhere that everyone can get to like suggested. Most of the workstations are little more than smart-monitors.

Another problem is that I have to have a solution that FORCES someone to keep THEIR work separate. So one nurse does not log data on another nurses account, etc. We thought of doing the "standard" login deal, where you log in, do your work, then log off. But we know from past experience that someone will log onto each workstation, and everyone will just filter through them, doing work under whatever name happened to be logged on at the time.

When we saw this DSL option, which actually does have an embedded option that loads on a flash drive that runs a (VERY SMALL) linux system WITHIN the windoze environment, we started thinking about how we could exploit that. Each person has their own stick, which they carry about with them. There are other aspects of the security system that ensures they will actually be carrying it around with them...

The problem is that DSL isn't really robust enough for our needs. So I'd LOVE to have a COMPLETE linux system to deal with. We could, then, put some of our security code on the stick, and it would interact with the main server (which, BTW, might not even be on-site), and the user wouldn't even have to know what was going on.

Furthermore, the doctors and nurses that go to multiple facilities could keep the one stick, and we could make it capable of recognizing which system it was on, and respond accordingly.

Once this possibility opened up, the security issues that it allowed us to sidestep just started making this more and more attractive. Furthermore, having the ability to have some of the unsecured functions on the stick makes it possible that we could have things they could work on away from the hospital.

So... there's more details. I hope it's enough.

Thanks muchly,

Lee

---

### Post by Insightfill on 2009-04-08
Honestly, the requirement that people don't share each others' sessions is a tough part of the scenario.  It's a social engineering problem rather than a technical one, and you need some way to make it easier or more practical to 'do the right thing' rather than work around your system.

Would VNC be a better option?  Have a single server somewhere running whatever Linux version you want, with everything in place.

Simple VBS script running on the machine checks the USB drive once per second looking for a VNC configuration file.  If VNC is not running, it launches it with the .vnc file.  If VNC is running, it does nothing.  If the drive or file is missing, then VNC is killed.  This also reduces your USB drive requirement, since all the thumb drive needs is a vnc file, and the host PC supplies VNC and VBS.

Don't rely on the 'vino-server' remote desktop feature in Ubuntu, as that lets people log directly onto the 'session 0 desktop'.   Use one of the other variants of VNC server, which lets each user get their own desktop.

(USB drives don't autorun well in Windows XP without quite a bit of hacking, which is why I suggested the VBS option.)

The scenario then would be that User A walks up to machine, pops in the USB drive, and within a second VNC launches.  They do their stuff and when they pull out the drive, VNC is killed (but their desktop is saved exactly where they left off).  Next user pops in their drive and VNC launches again with THEIR credentials.

Depending on the desktop that the Linux server is running, you'll probably have to carefully spec it for RAM and CPU; a lighter desktop like XFCE may be more appropriate.  Luckily RAM is staggeringly cheap right now, and dual, triple and quad core CPUs are getting more common.  Check out some LTSP articles on how to further reduce requirements (removing all 'cute' screensavers, for example).

Thoughts?

I wrote something similar for backups to a USB drive once using simple DOS batch files and VBS.  Pop in the USB drive and all recently modified doc and jpg files are copied to the temp directory, zipped, and dropped onto the thumb drive with the zip renamed to a date-time stamp.  If the drive is removed and replaced, all files changed since the last backup are also backed up.  If the drive reports full, then all backups are deleted and a full backup to thumb drive is done.

---

### Post by Insightfill on 2009-04-08
BTW: booting from a jump drive can be problematic - the BIOS on some of the older machines didn't always support it.  If you have such a mix of machines, you'll also find that the wide variety in BIOSes make it tricky, too.

To encourage people to use their own logins, try 'the carrot' rather than the stick; once per day catch a random person on the way in our out of the restroom (a place that everyone goes!) and confirm that they have their drive.  That day's winner gets a Starbucks gift card, or free cafeteria lunch or whatever.  Cost is $5/day.  After a couple of weeks, drop the frequency to less and less often until it's habit.

---

### Post by LeeCrites on 2009-04-10
Thanks "Insightful" -- your VNC suggestion has something there for me to chew on.

Part of the "problem" was they didn't want to have to have something specific running/installed on the PC that involved networking. But I can see how we might get around that.

I have noticed that SD-Cards and flash drives don't really autoboot very well. I have one Dell that executes the autoboot.inf (which I was, just by sheer dumb luck, initially testing on), but none of the others did.

I thought of putting it on a mini-CD or mini-DVD, both of which worked, but the time involved was troubling.

During my brief love affair with this idea, I was thinking of all of the security stuff we could hammer out if we had a full linux embedded system running. My initial message was sent during that brief period. The more I tinker with it, the more I realize that: 1) I can make it happen, and 2) it will be dog slow to boot up, or dog slow to run, or both.

My most recent thought process has taken me down a path where I have a small PHP script at the start of every page that checks for a flash drive, and then looks for a config file we set up. If it does not find it, you get an error message and taken to a generic screen. If it finds it, it will read the config and go with that info. There are problems with that, but it's where I'm going for the moment.

In the final analysis, I'd still be interesting to have a full-blown linux system on an SD-Card or flash drive. I guess you could just copy the whole CD/DVD of the live system to it...

Thanks muchly,

Lee

---

### Post by soltanis on 2009-04-10
You want people to carry around USB sticks to authenticate themselves. Okay, that makes sense. Why don't you try this scheme then:

USB sticks can carry information like operating systems, but what you seem to be yearning for is an authentication mechanism. So instead of booting a linux workstation every time someone wants to get something done, you should have people carry around their authentication keys on those sticks.

For SSH, this would be an easy scheme; everyone carries around their private key on their thumbdrives, and when they want to log in, they type their username in, SSH reads the key off the drive and off they go to wonderland.

To present your users with a graphical interface, you can run an X Server accepting remote connections on your computer, and use SSH to forward X traffic from your server box (which has all the 50-75 user accounts/keys) onto the client box. Mocha X, or something like that, is a compliant X server that runs on Windows.

With this kind of scheme, you can easily run something like Firefox, which would be forwarded from your server, which in turn presents your users with whatever interface they need to do their jobs.

So to sum it up:

You have many workstations (W, running any operating system) and one server (S, running Linux or BSD).
Each workstation runs an X Server (I know that's confusing; an X Server is something that actually displays windows). To log in, a user walks up to a workstation, plugs in their USB drive, and runs a script that reads a private key off the drive, connects to the server, authenticates with the private key.
On the server, once the user has been logged in, execute a script that runs Firefox, forwarding it over the SSH connection to connect to the X Server running on the workstation.

End result: user on the workstation plugs in the magic USB key, authenticates and is greeted with a firefox interface to whatever job they need to do. You can tailor this on a per-user basis.

---

### Post by mazato on 2009-04-10
LeeCrites, it's very late for me now. I was about to leave but your thread caught my attention.
If you think about these points for a second you could come up with more ideas.
SSH, Virtualbox,OpenVPN,IPSEC
Now you mentioned DSL. I tried it before and I didn't like it that much either. Have  a look at Puppy Linux. It boots so fast from a USB drive that it might run faster from a CD.
If you consider to boot Puppy Linux from a USB drive you can have a partition encrypted where you can have persistent changes (updates, customization,etc, comes to mind) and if it gets lost, there is another layer of security.
I could write more but I gotta go to sleep. I'll come back tomorrow.
Good luck!

---

### Post by mb_webguy on 2009-04-10
> **LeeCrites said:**
> In the final analysis, I'd still be interesting to have a full-blown linux system on an SD-Card or flash drive. I guess you could just copy the whole CD/DVD of the live system to it...

Sorry if my first post came off as condescending.  It wasn't my intention.  I just couldn't tell from your post exactly what you were asking, and misinterpreted a few things you said.

As for a full installation of Linux on a flash drive...  That's easy.  All you need is to install the [Live USB Creator]("apt://usb-creator") in Ubuntu.  You can use any LiveCD, even a remastered one customized to your specific needs, and any flash drive large enough to hold it.  It's even persistent.

And remastering a LiveCD is rather easy if you use one of the [various remastering tools]("http://en.wikipedia.org/wiki/List_of_remastering_software") available.

Of course, as you said this doesn't really solve your problem as this would involve booting from the USB drive every time someone wanted to do something, which takes long enough that it would actually encourage people to use each other's accounts.  On the other hand, actually running Linux from a LiveUSB would be moderately swift using USB 2.0 (but be no faster than a LiveCD using USB 1.0).

I'm still not sure any sort of security key system is going to be a solution for your situation.  I've seen several such systems implemented in various ways, from USB keys to magnetic key cards.  None of them seemed to be any better than a simple password-based system, and some were considerably worse (as a physical object can be lost or stolen and used by another).  It's the same with biometrics.  It sounds great in theory, but tends to fall apart in practice -- if something requires a thumbprint to use, what happens if you sliced your thumb peeling a potato the night before, or burned it trying to take something out of the oven?  Voice recognition fails with the common cold or a sore throat.  Retina scans can fail due to certain medications or medical conditions.  And security keys are not intrinsic to the person, so there's no guarantee whatsoever that the key is being used by who it should be.  A password may be forgotten, but as long as some basic security protocols are followed (such as not telling the password to someone else), it does a very good job of ensuring the person using it is who they claim to be -- at least as good as any of the alternatives.

---

