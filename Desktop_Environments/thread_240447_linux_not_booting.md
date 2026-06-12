---
title: "linux not booting"
date: 2006-08-20
forum: Desktop Environments
---

### Post by alexbOrsova on 2006-08-20
Hi. I've been trying to install Ubuntu 6.06(.1) LTS on my computer. I've had some experience with linux before though I would still consider myself a beginner. When the Ubuntu menu appears, I select the "Start or Install Ubuntu". When the progress bar loads about halfway, the system hangs. After a little bit of experimenting, I've discovered that if I press F6 and type in "live acpi=off nolapic", the progress bar loads all the way. However, the following message then appears on the screen: "

Uncompressing Linux...

invalid compressed format (err=1)

 -- System halted

". I've had this problem before while installing linux on this machine, and I've never solved it. What's going on here? How can I install Ubuntu? All help is appreciated.

---

### Post by meng on 2006-08-20
What sort of computer do you have?

---

### Post by randell6564 on 2006-08-20
> **alexbOrsova said:**
> Hi. I've been trying to install Ubuntu 6.06(.1) LTS on my computer. I've had some experience with linux before though I would still consider myself a beginner. When the Ubuntu menu appears, I select the "Start or Install Ubuntu". When the progress bar loads about halfway, the system hangs. After a little bit of experimenting, I've discovered that if I press F6 and type in "live acpi=off nolapic", the progress bar loads all the way. However, the following message then appears on the screen: "

Uncompressing Linux...

invalid compressed format (err=1)

 -- System halted

". I've had this problem before while installing linux on this machine, and I've never solved it. What's going on here? How can I install Ubuntu? All help is appreciated.

Is This an Iso image that you burned to a cd?  Seems to me that it's corrupted.  I would get another iso, burn it as slow as you can and try it again.  Also, try the alternative ubuntu cd.

---

### Post by alexbOrsova on 2006-08-20
Yes, this is an iso. I don't think it's corrupted because I've tried this with more than one downloaded and burned iso (6.06 and 6.06.1). I built my machine myself: ATI Radeon 9800 graphics card, 80gb Western Digital HD, not sure what motherboard (forgot ](*,), something with an a?) but it has an AC'97 built in sound card (pretty sure) and that's about it.

P.S. I'e gotten the same error with Kubuntu, foresight, and fedora core (5) linux.

---

### Post by alexbOrsova on 2006-08-21
So, anyone else have an idea? What if I took my hard drive out, put it in a different computer, installed linux and then put it back. Do you think that would work? Once again, all help is appreciated.

---

### Post by akshaysrinivasan on 2006-08-21
I Think you have a low memory configuration,may be you can install it from
the alternate cd in the non graphical mode or install edubuntu,which as far as i know require less memory for installation than the live cd.

---

### Post by alexbOrsova on 2006-08-21
I have 512 MB of RAM, more than the other computers I have installed Ubuntu on.

---

### Post by akshaysrinivasan on 2006-08-21
Then it must be a graphics card problem.So probably the non graphical installer is worth a try.Or have have you tried that too?

---

### Post by alexbOrsova on 2006-08-21
No, I haven't tried it. How do I use the non-graphical installer? Is it included in the desktop cd?

[edit]

Do you think I might have to get a different graphics card? I like my ATI Radeon 9800 :( .

---

### Post by alexbOrsova on 2006-08-21
I just tried installing in text mode from the alternate cd. I gives me the same error. I'm getting desperate here :shock: . Hasn't anyone ever experienced this problem before?

---

### Post by randell6564 on 2006-08-21
I've been googling this subject, trying to figure it out, and I'm finding a lot of references to the fact that it quite possibly is your hardware.

I use ATI graphics card as well.  I would not worry about that.  

Do some searching and I will continue as well.

---

### Post by randell6564 on 2006-08-21
Check out cyberticks post here [http://www.linuxquestions.org/questions/showthread.php?t=23718](http://www.linuxquestions.org/questions/showthread.php?t=23718)  I think it is relevent to your situation since you built your own box.

---

### Post by alexbOrsova on 2006-08-22
Guess what? :biggrin: :biggrin: :biggrin: From the menu of the alternate cd, I selected the install in text mode option, then I pressed F6 and added the following commands to the ones already there: "nolapic acpi=off" . And it works!!!!! Hopefully it's not a problem with my graphics card though because I want to keep it.

@randell6564

I read the link you posted. Apparently my graphics card isn't the ony hardware that can cause this problem. As I said above, hopefully it's not my graphics card.

---

### Post by mega on 2006-08-22
there are usually acpi options in your computer's bios you can play with, some let you turn it off

---

### Post by alexbOrsova on 2006-08-22
I've removed my ATI graphics card from my computer (using built ni graphics card) and tried the Ubuntu desktop cd. Same thing as before. This is because the installation in text mode from the alternate cd failed over and over (corrupt cd :cry: ). If this keeps up, I think I'm going to go nuts.

---

### Post by alexbOrsova on 2006-08-22
Alright, just tried the alternate cd and now it's a new error. "
Uncompressing linux...

crc error

 -- System halted

" I'd say it's a Cylindrical Redundancy Check (I think :-? ) error. My hard disk is perfectly fine, the windows xp installed on it works perfectly fine. So what's wrong now?

---

### Post by randell6564 on 2006-08-22
I believe that the crc error is pretty much the same as the first error.

At least from what I have been reading in google searches.

---

### Post by randell6564 on 2006-08-22
Can you please post a little more about your hardware?  Eg..Raid, Ide.

This I am quite sure is NOT a graphics issue!

---

### Post by alexbOrsova on 2006-08-22
Okay, I've got my computer opened up in front of me. I can see the motherboard is an AOpen. I've got three IDE cables coming out of it. On one, I've got my CD-Rom connected. On the other my hard disk (80gb western digital) on single setting. (floppy on the third). I've got an Intel Celeron D 3.06 ghz proccessor. And I also have no clue what raid is (don't ask).

---

### Post by alexbOrsova on 2006-08-22
Do you think the cd is corrupt?

---

### Post by randell6564 on 2006-08-22
> **alexbOrsova said:**
> Do you think the cd is corrupt?

I dont know friend!  But I DO know that you are understandably in a panic!

Every time that you post, you have done something to your box. That makes it a little difficult to keep up with you!

I need to go back and read your OP. (original post), to get back in play here!

I have never experienced any of the problems that you are having, though I have some of the very same hardware that you are sporting!  So lets just go slow and see if we can come up with a solution.

In the meantime, I dont suppose that you have another internet access point close by do you?  Something that can be used for now in order to get online and work towards a solution?

---

### Post by alexbOrsova on 2006-08-22
Yes, I do. I've got a winxp laptop that I've been posting from. Also, the only hardware change that I've made from when I first posted was switch from the ATI Radeon 9800 graphics card to the one built-in to my motherboard. Apparently the problem is still there, so it's not my graphics card (phew). As soon as someone posts in this thread, I know about it.

---

### Post by randell6564 on 2006-08-22
There is something to this fact that you have had the same trouble with other distrobutions on this same box!

You say that you have XP on the box in question?  Can you boot to XP and then go into the disk manager (forgot how to get there. been a long time since I used windows!), and post a screen shot of your HD? Partitions?

I want to see your Disk, and then go from there!

---

### Post by alexbOrsova on 2006-08-22
I used to have software for winxp so I could take screenshots, but not anymore. It doesn't matter anyway because I know what my hard disk looks like. Before I tried installing ubuntu from the alternate cd in text mode, I'm pretty sure my hard disk looked like this:

C: NTFS 75992 mb - Windows
Free Space: 8 mb

After the failed installation I know it looked like this(inst failed long after partitioner step was done):

C: NTFS(reinstalled win in order to dual-boot) 10.5 gb - Windows
D (/windows): FAT32(formatted by linux inst) 59 gb - empty
swap: 1 gb
linux root (/): ext3 59 gb - empty

---

### Post by alexbOrsova on 2006-08-22
*bump*
 
I'll check back tomorrow.

---

### Post by alexbOrsova on 2006-08-23
*bump*
 
I'm here.

---

### Post by alexbOrsova on 2006-08-23
I just tried the Fedora Core 5 installation cds. Here's the error I get."
RAMDISK: Compressed image found at block 0
invalid compressed format (err=1)
EXT2-fs: unable to read superblock
isofs_fill_super: bread failed, dev=md1, iso_blknum=16, block=32
Kernel panic-not syncing:VFS:Unable to mount root fs on unknown-blo_
ck(9,1)
 
and then a bunch of error codes go here
"
I'm not sure if that helps, but it sure is a lot more descriptive than Ubuntu.
 
P.S. The _ symbol means continued on the next line.

---

### Post by alexbOrsova on 2006-08-23
You're never going to believe what I just found out. The Knoppix 3.2 (live) cd boots without any problems. :biggrin: :biggrin: Now, why does knoppix boot, but not Ubuntu and Fedora Core?

---

### Post by alexbOrsova on 2006-08-23
As a matter of fact, I'm posting from Knoppix right now. I'd post a screenshot, but I don't know how.

---

### Post by randell6564 on 2006-08-23
> **alexbOrsova said:**
> As a matter of fact, I'm posting from Knoppix right now. I'd post a screenshot, but I don't know how.

Good, i'm glad that you got something working!  But the error that fedora gave you, I am quite sure indicates that something is wrong with your hard drive. Part of it is bad.

I'll look into it more on google.

Scratch that!  What I meant to say is it's something wrong with your Ram, not HD!

Sorry

---

### Post by .t. on 2006-08-23
Or, it could be your memory or your CPU. I doubt it's your HD (booting from CD), or your CPU (works in XP). So, memory is my best bet. Can you do a memtest86+ test (I think there's the option on the Ubuntu LiveCD boot menu)?

---

### Post by alexbOrsova on 2006-08-23
I've already tried a memtest86, it just gives me the same error as everything else. I'll try again, though. Be back in a few minutes.
 
P.S. For some weird reason, the windows on it doesn't want to boot anymore. I think when the text mode Ubuntu install crashed it did something to the C: partition.

---

### Post by .t. on 2006-08-23
Perhaps it is an HD problem then. If memtest86+ won't boot then it must fail between hitting enter in GRUB and loading the file from the HD.

---

### Post by alexbOrsova on 2006-08-23
Actually, that was my mistake. Memtest86 does boot after all, I just ran it now. It passed 100%.

---

### Post by randell6564 on 2006-08-23
SO., My Friend, You either got a HD problem OR a memory problem!

You choose!  You said that you built your box.  I would, in that case, make YOU the suspect here.

You should probably go back and eliminate all possibility's!

Reset your memory sticks, use some kind of HD anylyzer to see if you have a problem with your HD. (Keep in mind that all the suggestions that I am giving you come from research on the net!)

Start over My Friend.  From the beginning.

---

### Post by randell6564 on 2006-08-23
You keep fighting against what folks are suggesting that you do.

We cant help you if you keep NOT doing what is suggested!

I asked earlier that you post a screen shot of your drive from XP.  You chose not to because you "already knew how it was set up".  Alt+Prt Scrn will take a pic of your screen.  You dont need any special software to do that!

Keep doing what you are doing because it seems that you are figuring it out on your own!

---

### Post by alexbOrsova on 2006-08-23
Start over from the beginning? Great, just wonderful. Back to square 0.   :sad: Sigh*

---

### Post by alexbOrsova on 2006-08-23
One last thing, what do you think a "crc error" is?
 
[edit]
 
I'm not fighting against what you're suggesting. I didn't know about the Alt+Print Screen trick (remember my first post: I'm a beginner!). And I really did know how my hard disk was setup because I had set it up that way when I installed windows. Believe me, I've tried all your suggestions and more. And if I would've known about the Alt+Print Screen trick I would've used it.

---

### Post by randell6564 on 2006-08-23
> **alexbOrsova said:**
> One last thing, what do you think a "crc error" is?

That is another answer that you ALREADY recieved!  My final suggestion is that YOU do the research! You can obveously get online so GOOGLE IT!

If you want someone to do the work for you then take your box to a PC repair shop!

---

### Post by alexbOrsova on 2006-08-23
I don't want someone doing it for me, I only asked on this forum because I thought the people here might have more experience than me (you've got 381 more posts than me) and the other people that get turned up by google (this is the official site of ubuntu, after all!). If the best advice people can get from the official ubuntu forum is "google it" then why should they come here in the first place? Someone on the forum telling you to "google it" is like a company representative telling you "it's not my problem". After two days of ubuntuforums.org, I've only managed to rule out my graphics card. Seriously though, thanks for at least trying. I've been to some forums where they completely ignore you unless you have 100 or more posts.
 
P.S.
 
for every 9 minutes this forum is online, 1 minute it's offline

---

### Post by randell6564 on 2006-08-23
> **alexbOrsova said:**
> I don't want someone doing it for me, I only asked on this forum because I thought the people here might have more experience than me (you've got 381 more posts than me) and the other people that get turned up by google (this is the official site of ubuntu, after all!). If the best advice people can get from the official ubuntu forum is "google it" then why should they come here in the first place? Someone on the forum telling you to "google it" is like a company representative telling you "it's not my problem". After two days of ubuntuforums.org, I've only managed to rule out my graphics card. Seriously though, thanks for at least trying. I've been to some forums where they completely ignore you unless you have 100 or more posts.
 
P.S.
 
for every 9 minutes this forum is online, 1 minute it's offline

I agree My friend!  You should not have to come here and get "google it!"

But, as I said before, if you keep trying things on your own, and they WORK, then post them for someone who needs it!  We are trying to get YOU working, and I cant do that on my test box if you keep posting new results!

As was stated.,try and find something related to Hard drive issues or Ram, because I am not getting the same errors as you.

You REALLY need to do as was suggested!  When someone here asks you to post the results of something, then you really should!

---

### Post by randell6564 on 2006-08-23
> **alexbOrsova said:**
> 
P.S.
 
for every 9 minutes this forum is online, 1 minute it's offline

Yeah!! You noticed that too!  This forum is experiencing some real issues!

---

### Post by Original Brownster on 2006-08-24
Hi,
I've just read through this post, I think you need to eliminate the possibility that your install cd is corrupt.

Did you download ISO images from the net? If so you can check the image downloaded correctly by using the tool 'md5sum' in linux, hopefully it's on the knoppix cd you have, otherwise you can get it for windows too.

[Here]("http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/MD5SUMS") are the md5 sums

The CRC errors could be nothing more than the installer unpacking the compressed install files and checking there integrity hence the errors.

I would not do anything else until you can verify this cd is correct. 

The above will only check the iso image integrity, this still leaves the possibility the burn was corrupt, so if the md5sum for your iso is correct then maybe burn the disk again at a slow speed. 


Cheers,

---

### Post by m.musashi on 2006-08-24
I don't know if you are still having trouble and I can't claim to know more than those who have been helping you. However, at one point you mentioned that the noapic or similar option seemed to help. I had the exact same problems on a system I built and spent a good couple months fighting with it until I managed to get it to work (yes, persistent ain't I). The solution, I waited for a new BIOS update. It seems my board had a faulty BIOS in something called the description tables (I still don't know what those are). It seems windows doesn't care about them but Linux does. The new BIOS seemed to resolve the issues.

When was the last time the BIOS was updated? Is there a newer version available? If so, it might be worth a shot.

As mentioned above, I'd also check the CD and the md5 sums. If you can rule that out, then give the BIOS a look.

---

