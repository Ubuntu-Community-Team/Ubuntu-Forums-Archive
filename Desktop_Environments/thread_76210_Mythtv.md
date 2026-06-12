---
title: "Mythtv"
date: 2005-10-14
forum: Desktop Environments
---

### Post by the_tiger on 2005-10-14
I am liking Breezy alot but have never managed to install mythtv properly on ubuntu. Could someone please provide a walkthrough on how they have managed to install, configure and start it running.

Am I right in thinking it is necessary to log in as mythtv and if so is there a password?

Additionaly what PVR software are people using. Zapping doesent seem to come with the recorder plugin installed, is this easy to configure?

---

### Post by the_tiger on 2005-10-14
Forgot to add, I get this error on installing using synaptic

E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured

---

### Post by chaumurky on 2005-10-14
[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

---

### Post by Chareos on 2005-10-16
How did you install mythtv on BREEZY ?

---

### Post by chaumurky on 2005-10-16
Yes. Breezy has MythTV version 0.18. Works well. Using the site I mentioned above it was quite painless. The main thing is that mysql has to be installed and setup first otherwise the MythTV install fails to create an account and database. Had me going at it for days before I realised that...

---

### Post by Joshua on 2005-10-18
You should know that in Breezy, MythTV will only install if you are using the i386 version.

Also, as far as logging in under the mythtv user.  You shouldn't have to do that just to use MythTV.  I usually use MythTV as my normal user "joshua".  I'm under the impression that the mythtv user is there so that you can set your computer up to automatically boot into that user and start the MythTV software (then you can use it to operate a TV like a cable box would).

I would be interrested, though, if someone could go into some detail about the various users involved in the MythTV installation process.  For instance, why does the abarbaccia.com site run mythtv-setup as sudo?  Can you set everything up to use your normal user, including the mysql database?

---

### Post by Sprint27c on 2005-10-21
[QUOTE=Joshua]You should know that in Breezy, MythTV will only install if you are using the i386 version....[/QUOTE]

This is not necessarily true.  I have MythTV working with i686, Breezy, and a PVR-150...even got lirc to work with a MCE USB blaster last night.

Still have to fix the IR channel changer for my Dish box though...that broke in the upgrade somehow...

MythTV is by no means for the faint of heart...MySql, IVTV, and lirc are really challenging...but once you get it going it is awesome.

---

### Post by Footer on 2005-10-21
[QUOTE=Sprint27c]Still have to fix the IR channel changer for my Dish box though...that broke in the upgrade somehow...[/QUOTE]

Which Dish box are you trying to get it to work with?

---

### Post by the_tiger on 2005-10-22
I have a simple winTV go card which works with the video4linux drivers (can just install tvtime and watch tv). Do I presume I dont need to install IvTv or any other modules?

---

### Post by Sprint27c on 2005-10-22
[QUOTE=Footer]Which Dish box are you trying to get it to work with?[/QUOTE]

The Dish 301...I now have it working great!  I had a 'Gap too short error (100000)' which I had a heck of a time finding a google solution to.  Turns out its an adjustment to the remote.conf file (changed gap size to 175000).

So now I have a Shuttle PC with Ubuntu Breezy (i686), a PVR-150 tuner card, a MCE USB IR Remote Control/Blaster, and an IR emitter attached to a Dish 301 box...and its all working very excellent!

It is possible to do folks...just VERY time consuming with lots of hair pulling.  I'm no Linux guru...just a very competent Google'r.

Now on to the next step...HDTV :-0

---

### Post by Footer on 2005-10-22
[QUOTE=Sprint27c]The Dish 301...I now have it working great!  I had a 'Gap too short error (100000)' which I had a heck of a time finding a google solution to.  Turns out its an adjustment to the remote.conf file (changed gap size to 175000).

So now I have a Shuttle PC with Ubuntu Breezy (i686), a PVR-150 tuner card, a MCE USB IR Remote Control/Blaster, and an IR emitter attached to a Dish 301 box...and its all working very excellent!

It is possible to do folks...just VERY time consuming with lots of hair pulling.  I'm no Linux guru...just a very competent Google'r.

Now on to the next step...HDTV :-0[/QUOTE]

Cool!!!  I admire your persistence.  I've been doing MythTV for awhile now.  Started with Fedora Core 2 using Wilson's guide.  Had DirecTV at the time and an HD receiver (can't remember the model) and it had a serial port but I never was able to get it working to change the channels.  And I didn't want to mess with an IR Blaster.

Now, we've switched to Dish, we have the 811 HD receiver (no IR only RF) and it doesn't have a serial port so I'm stuck.  I have the PVR-250 card and would like to get an HD card someday but I need a faster Myth box with more hard drive space first.  Up to this point, MythTV has more or less been an experiment rather than a full functioning PVR that we use daily. :(

I do agree with you Sprint27c, it is VERY time consuming but rewarding when you finally get to the finished product!

---

### Post by Sprint27c on 2005-10-22
[QUOTE=Footer]...And I didn't want to mess with an IR Blaster....Now, we've switched to Dish, we have the 811 HD receiver (no IR only RF) and it doesn't have a serial port so I'm stuck....[/QUOTE]

Instead of making the IR emitter I just bought one for about $10...it works great.

I did a quick Google search and it appears as though several people have the 811 changing channels with an IR changer.  It must have IR capability also (which I think it does so that it'll work with universal remotes).  Maybe give it a shot sometime...

---

### Post by Footer on 2005-10-22
[QUOTE=Sprint27c]I did a quick Google search and it appears as though several people have the 811 changing channels with an IR changer.  It must have IR capability also (which I think it does so that it'll work with universal remotes).  Maybe give it a shot sometime...[/QUOTE]

You're right!  I just checked the specs a little closer on the 811 and sure enough, it does have IR capability.  Maybe I'll give it a shot.  Thanks for the vote of confidence!!!

With Linux and Myth (and of course Google), NOTHING is impossible!

:)

---

### Post by Drain on 2005-10-22
[QUOTE=Sprint27c]This is not necessarily true.  I have MythTV working with i686, Breezy, and a PVR-150...even got lirc to work with a MCE USB blaster last night.
[/QUOTE]

I think what Joshua was trying to say was that Breezy's AMD64 repository has come conflicting packages for MythTV - some are 0.18.1, and some are 0.17.3. So it can be easier to do an x86 install of Breezy on an AMD64 machine, in order to have all-same-version MythTV packages. 

I hope that some people out there can get those AMD 64 packages updated so I  [don't have to compile the packages myself]("http://ubuntuforums.org/showthread.php?t=74660"). ;-)

---

### Post by Gundar on 2005-11-27
Good Day

Sprint is there anyway you can please post your lirc information as I am battling with the MCE USB remote and being a newbie, I need a little help here.

Cheers



Gund

---

