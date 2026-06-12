---
title: "Updating Ubuntu on new Dell Mini 10v"
date: 2009-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Montala on 2009-08-31
Hi,
 
I am due to receive a new Dell Mini 10v in a couple of days time, which will come with its own version of Ubuntu 8.04 pre-installed on a 16 GB SSD.
 
I know that a lot of users promptly update to 9.04 but as there have been reported problems with track pads, web-cam microphone/speakers etc, I would like to stick with the 'official' Dell offerings, initially at least.
 
My previous of Unix is virtually none, as I am more used to dealing with Windows, but what I would like to do is to download and install any official machine specific Dell upgrades, if any do in fact exist, but am not sure quite how to go about this.... or even where to find them!
 
I would also like to make a copy of the existing SSD drive, just in case I do manage to mess things up, which I gather I can do by using the 'dd' command, and backing up to an external USB hard drive.
 
Any other hints or tips for a 'new boy' will be much appreciated!
 
Thanks :)

---

### Post by LMZKJ on 2009-08-31
As I understand it, Dell is currently working to update the 8.04 installation that has been shipping out.  If you keep an eye on their downloads available for your new mini, you will probably see the update appear with instructions on how to perform the update.

You may choose to DD to an external hard drive, but it may be just as easy to download the install files from Dell if you are not concerned with any of your private data.  This installation could probably be stored on a thumb drive and reinstalled if necessary.

Good luck with the new machine.  I have a Lenovo mini running Mint/XP in dual boot and I can't remember the last time that Windows got booted up.

---

### Post by snowpine on 2009-08-31
There is an "Update Manager" (under System->Administration) that will check for and apply any Dell updates. I think you will be automatically prompted to install these updates when you first turn on the computer. It is a pretty seamless process, nothing to worry about. Welcome to the forums! :)

---

### Post by Montala on 2009-08-31
> **snowpine said:**
> There is an "Update Manager" (under System->Administration) that will check for and apply any Dell updates. I think you will be automatically prompted to install these updates when you first turn on the computer. It is a pretty seamless process, nothing to worry about. Welcome to the forums! :)
Thanks for the welcome... and to the previous poster for his reply also!
 
What you say does indeed sound quite encouraging... just as long as Dell's "Update Manager" is actually clever enough to realise that I am running Unix rather than Windows! :)

---

### Post by snowpine on 2009-08-31
> **Montala said:**
> Thanks for the welcome... and to the previous poster for his reply also!
 
What you say does indeed sound quite encouraging... just as long as Dell's "Update Manager" is actually clever enough to realise that I am running Unix rather than Windows! :)

It is the same as Ubuntu's Update Manager, except that it points to the Dell "repository" (software library) instead of the main Ubuntu repository.

---

### Post by fjgaude on 2009-08-31
I have a mini 10 and it is wonderful. Have no fear Dell and Ubuntu is wonderful... there will be two versions of the GUI interface, one for those who wish not to know anything about the OS and the standard Ubuntu interface. You can change back and forth and find out which you like best.

The Update Manager only works with Linux, in this case Dell Ubuntu. No issues here.

Have fun leaning a better way from that of Windows.

---

### Post by Montala on 2009-08-31
Thanks... this is now starting to sound quite encouraging, and hopefully not as daunting as I had at first feared... roll on Wednesday morning... the date I have just been advised it should be delivered! :)

---

### Post by fjgaude on 2009-08-31
Hey, if you have any issues you know where to seek help, eh?

---

### Post by Montala on 2009-08-31
> **fjgaude said:**
> Hey, if you have any issues you know where to seek help, eh?
Absolutely... I have indeed been made to feel very welcome already! :)
 
Just one quick question if I may though, does the Mini 10v come with any sort of recovery CD as I would like to have a nice easy way to put mine back to its 'factory state' at any time, so that I will not then be quite so afraid of messing things up!
 
Preservation of user data is not really important initially... just my peace of mind really!
 
I know that 'LMZKJ' mentioned the Install Files, but at this stage I am not really sure where I would find these anyway... I do realise that I am getting a bit ahead of myself here, but I do like to plan ahead!

---

### Post by snowpine on 2009-08-31
> **Montala said:**
> Absolutely... I have indeed been made to feel very welcome already! :)
 
Just one quick question if I may though, does the Mini 10v come with any sort of recovery CD as I would like to have a nice easy way to put mine back to its 'factory state' at any time, so that I will not then be quite so afraid of messing things up!
 
Preservation of user data is not really important initially... just my peace of mind really!
 
I know that 'LMZKJ' mentioned the Install Files, but at this stage I am not really sure where I would find these anyway... I do realise that I am getting a bit ahead of myself here, but I do like to plan ahead!

I am not sure if it does or not (I bought mine used) but the recovery DVD is easily available to download from the 'web. (I know, I had to use it once! :))

---

### Post by fjgaude on 2009-08-31
It comes with a DVD with full recovery, but you have to have a USB DVD reader to use that DVD. You can download the ISO of 8.04 Dell from their sight. Then put the ISO onto a USB flash drive, if you have another computer to do such. The three USB ports all work fine on my little box.

The whole install is huge, like a little over 2GB, that's why it's a DVD and not a CD. Dell does things in their own way to make life easy for most folks.

I'd relax and sit back and enjoy all the new things coming your way.

---

### Post by Montala on 2009-08-31
> **fjgaude said:**
> It comes with a DVD with full recovery, but you have to have a USB DVD reader to use that DVD. You can download the ISO of 8.04 Dell from their sight. Then put the ISO onto a USB flash drive, if you have another computer to do such. The three USB ports all work fine on my little box.
 
The whole install is huge, like a little over 2GB, that's why it's a DVD and not a CD. Dell does things in their own way to make life easy for most folks.
 
I'd relax and sit back and enjoy all the new things coming your way.
Thanks... I thought that might be the case, so I have already ordered a Dell USB DVD reader kit, just so that I will be prepared for any such eventuality!
 
It was included in one of their frequent two day sales, with 20% off and free delivery, and is one of those things which often come in handy anyway!
 
I will now follow your final suggestion, and await delivery just as patiently as I can! :)

---

### Post by Greyed on 2009-09-01
As pointed out the Mini comes with the standard package tools that all Debian based Linux distros use pointed to repositories specific for the Mini.  When packages are update in those repositories you're prompted to update them on your machine.  

IE, if you're used to how Debian/Ubuntu does things, it is the exact same process, just a different repository.  If you're used to the Windows method of having to maintain all the programs on your machine individually, you're in for a treat at how simple it is to update a properly maintained system.  ;)

As for recovery, yes, it ships with a recovery DVD.  And as pointed out since the Mini has no built in optical drive you'll need an external one.  Almost all of your personal files are going to be stored in your home directory (/home/[username]  In my case, /home/grey) so it's easy to copy those off elsewhere and do a reinstall if needed.

I, too, have stuck with the 8.04 install even though I know I would be able to handle switching to UNR 9.04.  My decision is mainly based on wanting things to just work on this box.  I've used Linux in some form or another for over a decade.  I love tinkering with it.  Heck, even this install I took a few hours to get it working just so.  However I am happy with the versions of software that are on there, all the minor warts I've sanded off and I'm content with just riding LTS at this point.  I want one box on which I can just forget about software and hardware issues and it makes sense that the box which would be the most difficult to recover (I have no external optical drive) should be that machine.  :)

I say relax, get the machine in your hands, and see what it does before worrying about upgrades, sidegrades, recovery options and what not.

---

### Post by karamu on 2009-09-01
I have a Mini 10v and as noted, it comes with a restore DVD. Rather than buy a USB optical drive, what I did (using my desktop machine) was to rip the DVD to ISO then use Unetbootin to create a bootbale USB key.

I installed 9.04 and yes, there were some issues, specifically I couldn't get my headset to work so no Skype...... also my MP3 player didn't mount.

I have since installed the alpha 4 of Karmic and everything works fine- no probs with Skype or my MP3 player! Unfortunately as it is a pre release it is pretty buggy- lots of programs hanging.... I am hoping all will be well once it is released properly in October.

Good call though- it is a nice little machine and I am very happy with it!

---

### Post by Montala on 2009-09-02
> **Greyed said:**
> I, too, have stuck with the 8.04 install even though I know I would be able to handle switching to UNR 9.04. My decision is mainly based on wanting things to just work on this box. I've used Linux in some form or another for over a decade. I love tinkering with it. Heck, even this install I took a few hours to get it working just so. However I am happy with the versions of software that are on there, all the minor warts I've sanded off and I'm content with just riding LTS at this point. I want one box on which I can just forget about software and hardware issues and it makes sense that the box which would be the most difficult to recover (I have no external optical drive) should be that machine. :)
Thanks again for your reply.
 
My Mini has now arrived, but as I have got rather a lot on today I am going to leave it to 'charge up' first, and will get stuck in tomorrow.
 
I know that you have also taken delivery of a new 10v within the last week, so I wonder if you would mind answering a few quick questions for me please?
 
Firstly, the label on the bottom of mine says Mini 10 rather than 10v... is this OK?
 
The box contained a piece of paper about setting up the screen resolution to 1024 x 576... but I thought the new ones (which mine is) were now 1024 x 600?
 
Finally, (and this one is Ubuntu related!) I am looking for an MSN Messenger type program, and have already read how you updated Pidgin, which looks easy enough.
 
However I have also found another similar program called 'Emesene' which appeard to have recently been updated, and wondered if this might be a better alternative.
 
Have you, or anyone else for that matter tried 'Emesene', and if so what do they think of it?
 
Sorry for all the questions! :D

---

### Post by Greyed on 2009-09-02
> **Montala said:**
> Firstly, the label on the bottom of mine says Mini 10 rather than 10v... is this OK?

Hey, if it is a 10 then you got a free upgrade.  :D  But seriously, mine says 10 as well.  Probably just a stock sticker.

 > The box contained a piece of paper about setting up the screen resolution to 1024 x 576... but I thought the new ones (which mine is) were now 1024 x 600?

I'd be more concerned that the paper was for setting the resolution in Windows.  :O
 
> Have you, or anyone else for that matter tried 'Emesene', and if so what do they think of it?

I haven't as Pidgin is MSN, AIM, Yahoo! Chat, Google chat, ICQ and about a dozen others.  Since I have no two friends on the same chat network I could either try to find several Linux chat clients and run all simultaneously or just stick with one that does them all.  :D

---

### Post by Montala on 2009-09-02
> **Greyed said:**
> I haven't as Pidgin is MSN, AIM, Yahoo! Chat, Google chat, ICQ and about a dozen others. Since I have no two friends on the same chat network I could either try to find several Linux chat clients and run all simultaneously or just stick with one that does them all. :D
Right, so Pidgin it is then! :)
 
I read the link on your blog re updating to the latest version as it were but wasn't sure whether the two command lines were typed in together, i.e. just a copy & paste job into a terminal, or whether they had to be entered separately... if that makes sense?
 
Thanks again for your time... much appreciated!

---

