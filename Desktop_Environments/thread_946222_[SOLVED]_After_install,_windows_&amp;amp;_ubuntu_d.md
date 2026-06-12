---
title: "[SOLVED] After install, windows &amp;amp; ubuntu do not load"
date: 2008-10-13
forum: Desktop Environments
---

### Post by trymedo on 2008-10-13
Hi all,

Im a very new windows convert, looking to run Ubuntu full time but I currently have Adobe CS3 installed so I'd like a dual boot for now if possible.

Basically, I tried installing a dual boot, and after the install, I got told it had completed successfuly and that I needed to reboot. When I did so, the system tells me there is no bootable devices installed. It seems the partitions are there, but I have a feeling one has been edited or corrupted. Now when I reboot, it just says GRUB on the screen and nothing else happens. 

Does anybody have any idea what is wrong? Sorry for being vague, Im a complete newbie just wanting to leave the microsoft path.

Thanks everyone.

---

### Post by trymedo on 2008-10-13
Anyone have any suggestions of where I can find help? Like I said, Im very new to all this. Any info is very much appreciated.

---

### Post by Black Razor on 2008-10-13
I had a similar situation happen when I first started using Linux.  However, if your going to resolve this issue then we are first going to have to resolve a **[SIZE="4"]bigger[/SIZE]** problem.

First, let me welcome you to the community.  It's always nice to have yet another convert to the dark side of the force.  :p

It will help you to learn something very critical about Linux, before anyone could offer an educated guess or solution.

Now, before I scare you away like so many sour old Linux pros did me at first, let me just say this.  Stop. Take a deep breath.  You should congratulate yourself for even taking the plunge to Linux in the first place (I am of course assuming you are a linux newbie.  I could be wrong)  It takes an intelligent open minded individual to come from windows to Linux.


Linux IS NOT WINDOWS...ok, let me repeat that.  Linux IS NOT WINDOWS.  Ok, I stress this not yelling at you but to drive the point home. In the world of Linux you can't just post "I have this problem, and I dont know what to do".  Why you might ask?

Your going to have to get used to the idea of thinking things through just a wee bit more in terms of the information you provide so that we can help you.  Let me provide an example.


PROBLEM: I installed Linux and now I can't boot windows.

ERRORS IN ABOVE PROBLEM

#1.NO mention of which version of windows.

#2 NO hardware configurations (ie what types of components by manufacturer and model, at the very least RAM, CPU Speed, etc

#3 NO mention of which version of Ubuntu or Linux you are using.

#4 NO detailed information about how you installed your "distro" (particular distribution or version of Linux your using, sometimes called a "flavor")  

...By which I mean did you just use the automatic installer that may have been included with your distro or did you manually configure anything? 

#5  NO mention if you received any errors during installation or how you obtained your copy of your distro's installer.  Did you order a disc?  Did you download an ISO and burn it?  If you DL an ISO, did you verify the integrity of the disk? (thats a process known as MD5 Sum Checking)


Now, I will tell you what comes to mind immediately with the little bit of info you gave me.

It sounds like the Master Boot Record (MBR) is corrupt.  This could be for several reasons.  You could have installed GRUB on a different partition than the Windows Boot Manager.  If your at least getting GRUB to show up, then this isnt the case.  You could try downloading an ISO for a windows recovery disc for your appropriate Windows version, and then booting from the CD and running recovery which would fix the windows MBR.


I can't really think of anything else of the top of my head without more information to go on.  If you post some more information I or some other Linux geek might be able to help you resolve this issue.

Also, one other VERY IMPORTANT thing.  I noticed that you posted and then bumped your thread about 2 hours later.  DONT DO THAT.  It's considered VERY rude in the Linux world and will piss off a lot of people.  You are going to have to make a mental shift in understanding that in the Windows world when you buy software, your really purchasing tech support. 

Linux is free, usually created, updated, and maintained by computer enthusiasts who give their minds to your for FREE. These are the same people who usually get paid a couple hundred bucks per hour for their consultation. Don't be an a$$ and expect immediate response when you didn't pay a dime for anything.  

You should also get into the habit of spending some time searching the forums for anyone who might have already dealt with your issue before you start a new post. Your issue sounds to me like something that likely has been addressed before.

You shouldn't feel bad or anything, just about every newb does it, including myself when I started.  Just don't do it, ok?

Oh, and a bit more good praise.  Your thread was titled dead on, which helps attract people to the problem.  MANY Linux users on the forums are lurkers, who kinda cherry pick which posts they respond to.  It always helps to name things as specific as possible, and to put them in the right Board.  In this case, you would have likely had a better response rate in the Installation & Upgrades board, rather than Desktop Environment.  Again, no worries.  

Also, once your issue is resolved it's usually an expected courtesy to edit your thread title so it says "[RESOLVED]"

Let me know if my suggestion about the MBR resolved the issue.  Once again, welcome to the dark side.

---

### Post by trymedo on 2008-10-13
Hi, 

Thank you so much for the useful info. I'll definatley bare all the points in mind when posting again :)

sorry for bumping the post, I wasnt sure if I was in the right place or not and Im panicking a little bit...

Ok, so where to start... let me try and desribe (as best I can) my system spec, what I was trying to achieve and what actually happened...

Im running a dell dimension 9200 desktop pc, with windows xp preinstalled. I have 2 gb of ram, 2.6gh quad core processor. I'm not entirely sure what graphics card it has at this moment in time (Im at work and the pc is at home) but if its any help at all, Im pretty sure its a relatively new nVidea geForce graphics card.

I downloaded the iso for Ubuntu liveCD last week, I think it's Ubuntu 8.04.

----------------------------------------------------

I think my first big mistake was thinking I knew enough to simply jump in the deep end. Turns out, I know very little indeed and now wish I'd read more about it all first. Anyway, thats neither here nor there. What I intended to do, was install a dual boot. This would allow me to run Ubuntu most of the time, but when I needed to work on my flash projects, I could boot into Windows and run Adobe CS3 like Im used to.

When Ubuntu liveCD booted up, I first tried it out without installing and everything seemed to work fine so far.
After playing with it non-stop for about 4 days, I decided I already liked it enough to take the big plunge. So, I backed up all my work onto my external HDD, and the rebooted my system. When the liveCD started again, I chose "Install Ubuntu".

I dont think I set anything up manually, I pretty much defaulted through any screens I could because I dont know enough about disk partitioning and the like to mess with anything. 

So then Ubuntu installed - no errors here. It asked me to enter name, password etc. set up the date and time... all these things I was used to from installing windows in the past. After Id done all this, Ubuntu tells me everything is fine I need to reboot my system. 


This is where the trouble began... before the PC had actually shut down, I saw some error messages pop up very briefly. they vanished again before I could read them properly but it was a few lines saying something about things that could not be loaded/installed maybe. Before I could write any notes about this down, my machine reset itself. 

now, whenever I boot up, all I see is GRUB and nothing else. 

Hope this explains things better and thanks so much for trying to help me :)

*edit*

Ps sorry, I forgot to mention that...

A friend of mine said that fixing the MBR could solve it, so I tried runing the windows recovery console and typing fixmbr. it said it had been fixed but still no progress on the booting front. I think I also tried a fixboot to no avail.
I apologise for being such a n00b. I really dont know what Im talking about but I'm trying my best to learn (I just think Im doing it the wrong way round) :)

---

### Post by Black Razor on 2008-10-13
OK,

First off, No problem.  Linux is a community, and in a community you help each other.  The thanks is still appreciated though, and verbally thanking someone for their help is always a nice thing to do and will kinda earn you brownie points in the community.  Remember, humility is a virtue.

On that note, the Ubuntu forums use a Thanks counter, which is kinda like a reputation.  If you really wanna show someone thanks, use this feature to help their reputation on the boards.

You can read more about it and all the most common FAQ for using Ubuntu forums by  [clicking here]("http://ubuntuforums.org/showthread.php?t=726219")  This will take you to a tutorial post by one of our dedicated forum admins, LaRoza.  It will explain a bunch of things to you that will help you fit in better and make the most of your time on the boards.

Now on to frying bigger fish.  I am sorry to tell you that I got that "sick to my stomach/hairs on my back standing/cringing" feeling when you said chose the "Install Ubuntu" option.  I could be mistaken, and god do I hope so, but you may have given the Ubuntu installer permission to use the entire disk for Ubuntu, instead of what you wanted which was to dual-boot.

Now, don't panick just yet. What I would suggest you do is boot the LiveCD and then click on Places in the menu bar on the top of screen.  Once there click Home and then the Up navigation arrow.  The goal here is to get to the " / " folder.  Once you are there click "media".  If your windows partition is still there, I belive it should show up there as "partition_1" or something like that.  

See, Ubuntu is unique among Linux in that starting with 8.04 (Codename Hardy Heron) the Windows NTFS file architecture is supported natively.  What that means is that you don't have to fudge around with a bunch of things to see your Windows partitions anymore, like back in the old days and still in some distros of Linux.  

You do however still have to mount the partitions manually, which if its there, you should be able to just right click on the partition and choose Mount option.

BTW get in the habit of using both version numbers and codenames in Linux.

To be sure about what happened to your PC though I'm gonna have to do some research and get back to you.  I have also been awake for over 23 hours straight, so I am a little tired. I beg for your patience.

In the meantime, so that your not left with a big metal and plastic brick, you should be able to boot into Linux using the LiveCD. That will give you a usable PC.  

You may however have a non-optimal video resolution as you mentioned you have an nVidia card.  Good news though is that once we get this worked out, nVidia usually work pretty damn well with Linux, as opposed to ATI which tend to be a pain in the ***.

I am sorry I can't be of more help right now, but don't panick man.  I did the same thing my first time up to bat.  It's not uncommon, and since you said you backed up your important work, pat yourself on the back.  

I'll check back here later with some updated information.  I hope all is well and not what I suspect.

-BR

---

### Post by Black Razor on 2008-10-13
Also, before I forget.  Check out innotek Virtual Box in google.  It's IMO the best windows virtualizater out there.  You don't have to dual boot unless your doing something as system intense as video editing at the studio level with Adobe Premiere.  If your just using Flash, Photoshop, etc. I would just use VirtualBox and install windows to a virtual machine and then run your apps natively and enjoy the benefits of a fully Linux environment.

---

### Post by trymedo on 2008-10-13
Brilliant thanks! :)

I had a bad feeling I may have overwritten windows too but Im not too worried about that to be honest lol.
As all my important work is backed up, i dont even really mind if the only option is to format the drive and start from scratch - Just rather not right now if I can help it :S

Thanks for looking into it for me, I'll try to post some more detailed system specs on my system tonight if I get a chance, hopefully that will help. 

Also, I have been using the LiveCD to get online and check my emails etc. Its just a tad annoying because I have to keep setting up the email pop account and stuff because none of my settings get saved on the LiveCD version.

again, many thanks for your help on this. I'll definately make sure you get your thanks points!

---

### Post by Black Razor on 2008-10-13
No prob.  

I'm gonna catch some sleep now, before I forget save [this link]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html") to your bookmarks.  Its a great guide to getting VirtualBox installed once we get this worked out.

FYI, don't thank people unless you personally feel the information was helpful to you.  I know it sounds like it makes sense, but its kinda a personal thing for you to show your gratitude.  Don't give me them just because I mentioned it.  (Although I don't have any yet, lol)  Also, you can thank a person for each post in a thread, so if for example you have a conversation in a thread and someone responds say 5 times, and like two of them were really helpful, you can thank them for each of the two posts that helped you.   Again, not telling you what to do, just passing info.

-BR

---

### Post by trymedo on 2008-10-13
I wouldnt thank you just for the sake of it, Im genuinley grateful for the info you've given me, its a load off my mind just knowing that somebody out there is trying to help! - Id be hopeless trying to sort this by myself. 
I'll check out the link in the meantime. cheers!

---

### Post by trymedo on 2008-10-14
A friend of mine has the exact same PC (only with Vista instead of XP) and he's going to send me as much info on the spec as he can find that may prove usefull. 

***************************

Ok, here's the info he sent me...

Dell Dimension 9200 Desktop PC
------------------------------
Ram: - 2gb
Processor: - Intel® Core&#8482;2 Quad CPU Q6600 @ 2.40GHz 2.39 GHz
Graphics: - NVIDIA GeForce 8800 GTX

- I was kind of expecting more info than that but then again, what do i know? Hope this is enough for now :)

***************************

In the meantime, is it worth me giving this "Alternate CD" a try? I've downloaded and burned it to disk but I'll hold off on actually using it for now... I dont know whether it should make any difference, I just saw it mentioned on a couple of forums that mentioned similar problems after installing. 

I'm kind of convinced after going through the motions again last night that I have in fact given Ubuntu full drive access and wiped Windows off in the process :-k Nevermind, Im on the road to a happier computing experience Im sure :)

---

### Post by brianfreytag on 2008-10-14
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This should definitely help you in your problems.

What happened was the boot loader was not loaded correctly, so you need to repair the MBR (Master Boot Record).

This guide is GREAT.  It's saved me several times.  Windows and Ubuntu don't play along more often than not, but like you, I still need Windows for several tasks, so I've used this guide quite a lot.

---

### Post by trymedo on 2008-10-15
Hi, 

Thanks for the link, I'll check it out but as I mentioned earlier in the thread, I have already tried a couple of routes at fixing the MBR to no avail. Thinking back, I do get the feeling I have actually overwritten the windows partition completely by accident. 

Does any know if there is there a fool-proof way of finding out if your windows partition is still on the drive?

---

### Post by trymedo on 2008-10-15
Just out of curiosity, I was told this thread is in the wrong place... is there any way to move it to the correct one? cheers

---

### Post by brianfreytag on 2008-10-15
> **trymedo said:**
> Just out of curiosity, I was told this thread is in the wrong place... is there any way to move it to the correct one? cheers

If you're not able to do it yourself, you can IM a moderator and ask them (nicely) to move it to the proper location.

---

### Post by caljohnsmith on 2008-10-15
How about booting your Live CD, opening a terminal (applications > accessories > terminal), and posting the output of the following:
```
sudo fdisk -lu
```
That will tell us what your HDD setup is right now.

---

### Post by trymedo on 2008-10-15
Hi all,

I have managed to get Ubuntu running on my system now! with a little help from a mate :) I'm still not entirely sure what Id done the first time round, but I ended up removing everything and starting from scratch. I used the "Ubuntu 8.(04?) alternative cd" and installed just Ubuntu. This still caused some problems as when I rebooted after installation I got the following message on screen:

[INDENT]GRUB  Loading stage1.5.
GRUB Loading, please wait...

Error 2

[/INDENT]This was actually really easilly solved by following a guide found [here]("https://answers.launchpad.net/ubuntu/+source/grub/+question/7137") about reseting the IDE harddrive setting from (Auto) to DMA. I couldnt find the exact settings mentioned but luckily for a n00b like me there was only one other option under my HDD BIOS configurations, this was turning off the RAID setting. It warned me that all data on the drive would be lost, and since that didnt matter to me at the time I went for it.
Expecting to have to go through the whole installation process again, I was relieved to just see the Ubuntu logo appear and the OS booted up instantly! None of the installation had been affected, but now it booted up :)

Now I want to learn how to make sure all my drivers are correct and up to date. There seems to be a warning about my graphics driver being a "proprietry driver" so I'm off to look that up.

Thanks for everyones help! - I'm really excited about seeing what this OS has to offer. Already it seems like this is the thing my PC has been missing all this time!


Tom

---

### Post by Black Razor on 2008-10-16
Hey.  Sorry it took so long for me to get back to you.  I'm a full time college student and this is midterms week, so time is limited. 

I am glad you got it working.  In the future I would recommend when you install a new operating system and your willing to give the entire drive to the OS that you use DBAN (Darik's Boot and Nuke) to wipe your drive completely of all data previously on it.  In fact I would do it anyhow and then reinstall Unbuntu. 

Yes, I know a lot of people think thats overkill, but I'm a military veteran whose job was IT field.  I am just always overkill and like to make sure there are no remnants of a previous operating system whenever I install a fresh operating system.  That way when I get problems I know its not something left over, which CAN happen.


The Alternate Install is usually for people who get hang ups during install for various reasons, whether it be not enough system memory to handle the GUI installer or whatever.  Basically the Alternate Installer is a text based installer, thats all.

Now on to your video driver.  Like I believe I said before, NVIDIA plays nicely with Ubuntu so your all set.  Just install the proprietary driver for it.  It's ok.  What Ubuntu is trying to tell you is that there is hardware on your machine that requires drivers which are not open source.  ie. proprietary as in not open source...get it?

If you have any more questions about your new operating system just ask, but make sure you start a new thread for each issue so you can get the best response rate, ok?

Also, if you start a new thread feel free to always send me a message inside the forums system to let me know and I will be glad to check it out.  Also, read that FAQ I linked to earlier in this thread.  It will help you.

Oh, and one other thing.  Be sure to mark this thread resolved, ok?

Best of luck!

-BR

---

### Post by trymedo on 2008-10-16
Hi, 

no worries, I understand - I was at college once. Its just Im an arty farty type not an IT type although I am learning (slowly but surely)

I'll probably try DBAN when I have a bit of spare time. Im in the middle of moving house at the moment though so not sure if I'll get a chance. It's not top of my priorities at the moment, getting the PC up and running is though because I need to check emails for work and stuff.

Yeah my graphics card seems to be playing nicely with Ubuntu. The compix fusion doesnt seem to have any problems showing off the crazy effects :) - loving the 3d desktop cube interface!

lastly, this is thread is already marked as [solved] now is it not? - if its not showing up then maybe Iv done that wrong too :S lol doh!

Thanks for the help, now that I have the hardest part sorted I should be ok for a little while. I'm going to spend time looking through some getting started guides now I think :) - and getting used to the Ubuntu OS in general.

---

