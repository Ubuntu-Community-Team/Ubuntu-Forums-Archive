---
title: "How do I fix constant crashing in Ubuntu?"
date: 2009-01-23
forum: General Help
---

### Post by PsychedelicWonders on 2009-01-23
I love ubuntu because of how much you can customze it and how fast it is. 

But this is BS and really pissing me off. 

It crashes all of the time.

WAY more than windows ever did.  

This is a brand new computer with a quad core. There should be no reason for it crashing. 

Now it won't even load the kernal. 

Just says:

Something about bios version
Initializing...

And it's stuck.
 
So how can I fix tv computer to load right now?

And how can I fix it from crashing daily?

---

### Post by cb951303 on 2009-01-23
what kind of crash? what's the error?
are you sure it isn't faulty hardware?

---

### Post by markharding557 on 2009-01-23
given it stalls at the bios stage it's something to do with your bios or computer rarther than windows or ubuntu.
something not plugged in correctly can cause this

---

### Post by PsychedelicWonders on 2009-01-26
> **markharding557 said:**
> given it stalls at the bios stage it's something to do with your bios or computer rarther than windows or ubuntu.
something not plugged in correctly can cause this

After I read this, I went to every cable and jiggled it to make sure it was in good and tightened down anything.

It seemed to work and started right up... so i thought there wasnt an issue...

but then after a few more restarts, it gave me the same error and I know everything was connected.

What else could it be?

---

### Post by wirelessmonkey on 2009-01-26
It could be a huge number of things, but if it's not getting past the BIOS, it's not an ubuntu error. It would be tremendously helpful to know the exact error message(s) you're getting.

---

### Post by PsychedelicWonders on 2009-01-26
> **wirelessmonkey said:**
> It could be a huge number of things, but if it's not getting past the BIOS, it's not an ubuntu error. It would be tremendously helpful to know the exact error message(s) you're getting.


It just says:

Something about bios version
Initializing...

And it's stuck.

---

### Post by Post Monkeh on 2009-01-26
is it a brand name pc or did you build it yourself?

if you can i'd open it up, remove your memorychips, & any pci/e cards you have & put them back in again, making sure they're secure. if it worked after you jiggled the cables, most likely something is loose

---

### Post by PsychedelicWonders on 2009-01-26
this is a self build.

never had any issues before and having moved anything... but I will do as you say and see if it helps.

---

### Post by PsychedelicWonders on 2009-01-27
I didnt get a chance to take the computer apart last night and put it back together.

But there are just a bunch of serious problems.

First of all I have a dual monitor setup and right now I have the Ubuntu Helios screensaver.

After X amount of minutes the computer just freezes when both monitors are running the screen saver.

Why is it doing this?

it really has only happened from me switching to the helios screen saver and having these 2 monitors.

Something so easy should not be so difficult.

Also:

the computer would not get past this bios screen 8 out of 10 times.

I will for sure tonight take it apart and see if that does anything... but the computer hasnt given me a problem up until now and hasnt been moved... so I honestly dont think its going to do anything... but ill try.

---

### Post by MartyBuntu on 2009-01-27
Sounds like it could be a RAM problem.

If you can successfully get past the POST, run MEMTEST.

---

### Post by PsychedelicWonders on 2009-01-27
> **MartyBuntu said:**
> Sounds like it could be a RAM problem.

If you can successfully get past the POST, run MEMTEST.


As in the RAM is bad?  Or not enough?

I currently have 2g... I can go up to 8 total and planned on getting more memory as soon as I can... but damn 2 shouldnt make it crash should it?

What is POST?

and just run MEMTEST in the terminal?

---

### Post by clueless on 2009-01-27
Something similar happened to me with a self built computer and it turned out to be overheating... You could check the temperatures too..

---

### Post by PsychedelicWonders on 2009-01-27
> **clueless said:**
> Something similar happened to me with a self built computer and it turned out to be overheating... You could check the temperatures too..


Hmm.  how can i check the temp?

I dont have gauges?

I have a fan sucking air in the case right underneath the 2 HDD's & a fan sucking out of the case on the back... should be pretty good for heat transfer?

---

### Post by clueless on 2009-01-27
I got my problem solved by adding a fan on the side of the tower, blowing directly on the motherboard and graphics card. I do not know much about these things but I think that you could get a basic reading from the computer's bios. You could try getting one reading when you are switching on the computer after it has been off for a long time and another one immediately after it froze and you had to restart it.

I am sure that there are better methods, maybe even specific applications, but I would not know any. In my case, I installed the fan, it worked and never thought about it again.

---

### Post by theozzlives on 2009-01-27
Could be video RAM. I remember a customer that his Windows 3.1 would lock up in Solitaire, sometimes right away... sometimes after hours. I took his box home and played Solitaire all day (I hate Solitaire), it turned out that the colors in the cards were accessing a bad spot in the video RAM. I replaced his video card and it worked fine,

---

### Post by Post Monkeh on 2009-01-27
it's definitely hardware related and nothing to do with your software.

i wouldn't have thought it was overheating if it was only switched on, it sounds more like something isn't seated properly or something is faulty.

try re-attaching everything first, then if your motherboard has onboard graphics enable them and take your graphics card out.

if that doesn't work and your  2 gig ram is 2 1 gig sticks rather than 1 2 gig stick then take one of them out, if that doesn't work then try the other one.  if it's a 2 gig stick then hopefully you can get a friend to lend you one.

tbh if it was the video card i wouldn't expect the pc to switch on at all, but it could be slightly loose and the vibrations of the fans could be shaking it. all it would have to do is lose one of its many connections and your system will probably poo itself.

---

### Post by PsychedelicWonders on 2009-01-27
> **theozzlives said:**
> Could be video RAM. I remember a customer that his Windows 3.1 would lock up in Solitaire, sometimes right away... sometimes after hours. I took his box home and played Solitaire all day (I hate Solitaire), it turned out that the colors in the cards were accessing a bad spot in the video RAM. I replaced his video card and it worked fine,


I will be sooo pissed if its the video card.

this is already my 2nd one from new egg.

How do I tell what the root of the problem is and if its witht he video card?

---

### Post by MysticGold04 on 2009-01-27
You could also try booting the Live CD and testing your memory that way, using the memory test option on the menu. I had a Windows system keep crashing, and that's how I found out it had bad memory after removing and reseating the memory sticks...

---

### Post by Therion on 2009-01-27
If you can't get your PC to fully load the BIOS, then you're not passing POST.  

POST = Pre Operational Self Test.

Not POST'ing means something is not right with your hardware.

The procedure for narrowing down what's causing a PC to fail POST is usually determined by POST codes, a beeping sound produced by the PC that indicates why POST is failing; it's a lot like Morse-code.  If you're not getting a POST-code beep, then you'll need to troubleshoot things the old fashioned way...

Strip the PC down to the absolute bare essentials.  If there's onboard video, remove the video card. If there is NO onboard video chipset, install the video card.  Remove all but one memory module.  You don't even need to connect a hard disk drive or optical drive.  All you're trying to do is pass POST.  Attempt to boot the system with this bare-essentials hardware profile.

If all goes well, enter the BIOS, use the factory "Failsafe Defaults" setting and then start adding hardware one component at a time and rebooting between each to make sure you can still pass POST.  Start by adding the other memory module.  If you pass POST add your video card, etc.

This is how you root-out your rogue hardware.

---

### Post by carolinason on 2009-01-27
POST == Power On Self Test

---

### Post by PsychedelicWonders on 2009-01-28
Ok I unplugged everything and opened it up.

I took out the video card and the memory and plugged them back in.

I forgot to do the 1 stick of memory thing.

It seemed to work fine and booted right up after I did this, but when I got to the Ubuntu log in, one of my monitors kept shutting off & on constantly until I restarted the comp.

Then it gave me the screwed up snowy Nvidia screen and was locked.

Finally I got it to load up by running a Recovery mode, I was going to "fix the issues" in recovery mode, then it tried to install something and asked me to continue & I knew i wasnt connected to the internet to download and install what ever it wanted, so I just canceled and normal booted.

Now everything was fine, until the morning when I woke up with my computer frozen again with the two screen savers still on the monitors.

I have 2 19" dell monitors and I also have the Ubuntu Helios screensaver that plays on both screens simultaniously.

I want to always have my monitors on & active playing both of these screen savers because the way my loft is set up, its like "art" for me and everyone to enjoy.

something with these screen savers seems to be making my comp crash...

here is the video card I have, it should be plenty for any application I am trying to do....


[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121095](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121095)


> **Post Monkeh said:**
> it's definitely hardware related and nothing to do with your software.

i wouldn't have thought it was overheating if it was only switched on, it sounds more like something isn't seated properly or something is faulty.

try re-attaching everything first, then if your motherboard has onboard graphics enable them and take your graphics card out.

if that doesn't work and your  2 gig ram is 2 1 gig sticks rather than 1 2 gig stick then take one of them out, if that doesn't work then try the other one.  if it's a 2 gig stick then hopefully you can get a friend to lend you one.

tbh if it was the video card i wouldn't expect the pc to switch on at all, but it could be slightly loose and the vibrations of the fans could be shaking it. all it would have to do is lose one of its many connections and your system will probably poo itself.

---

### Post by Therion on 2009-01-28
Well you're booting up fully, and that tells us nothing is fried on the motherboard, so there's a huge hurdle crossed.  

Your issues now are starting to sound video card, or video *driver*, related.  I'd bet money it's the latter.

I'd purge out your existing nVidia drivers and reinstall them using the latest 180 series.  I've had nothing but good luck with the that series of drivers from nVidia on my system.

---

### Post by PsychedelicWonders on 2009-01-28
> **Therion said:**
> Well you're booting up fully, and that tells us nothing is fried on the motherboard, so there's a huge hurdle crossed.  

Your issues now are starting to sound video card, or video *driver*, related.  I'd bet money it's the latter.

I'd purge out your existing nVidia drivers and reinstall them using the latest 180 series.  I've had nothing but good luck with the that series of drivers from nVidia on my system.

yes it seems I am having a multitude of issues... all related to the video card.

And the video card works when it works and it rocks... so hopefully it is just a driver.

its worked perfectly up until about 2 weeks ago.  and nothing else has been changed/removed from the computer itself as far as hardware.  the computer itself wasnt even moved to incite a video card bumping loose.

How do I "purge" out exsiting nVidia drivers and then reinstall the 180 series?

thanks.

---

### Post by Therion on 2009-01-28
You should look over this thread:

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180)

It should answer all your questions.

---

### Post by PsychedelicWonders on 2009-01-28
> **Therion said:**
> You should look over this thread:

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180)

It should answer all your questions.

Wow thats a long thread... is the entire, CORRECT walk-thru the first post on the 1st page?

Or have there been better, new updates later in the 40 pages?

---

### Post by Therion on 2009-01-28
The first page covers everything.  The download link is there and the basic install procedures are there.  That's what you need.

---

### Post by PsychedelicWonders on 2009-01-28
thanks, my computer wont have internet access for about a week, so when it does I will run this walk thru and post back with my results.

thank you.

---

### Post by PsychedelicWonders on 2009-02-06
**IF **I can get Ubuntu to boot up, I get the following screen...

(I pulled back my 3-D ring to show you, no background or sky dome populates and I dont understand why?)

My internet wont be active until monday, so I still wont be able to run any code until then.

Therion, do you think the walk thru you provided will fix this issue also?

---

### Post by PsychedelicWonders on 2009-02-09
I've had a serious issue with getting past POST lately and I don't understand why. 

There was never an issue before, the computer was not moved. 

The ONLY thing That changed recently was that I added I 2nd monitor.

I was told somethng wasn't seated right. So I took it apart and removed and reconncted most of the computer. 

Twice. 

How can I find out what the real issue is?

---

