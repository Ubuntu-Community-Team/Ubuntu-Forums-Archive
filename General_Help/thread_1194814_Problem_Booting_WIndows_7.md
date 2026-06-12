---
title: "Problem Booting WIndows 7"
date: 2009-06-23
forum: General Help
---

### Post by rectec794613 on 2009-06-23
I recently had a chat with a Microsoft agent. Here's the problem (copied from chat): > Well I decided to delete Windows XP since I never use it, and eventually go buy Windows 7 when the final release comes out. Then I rebooted and couldn't get back into Windows (I thought this would happen), so I booted off my Kubuntu Live CD and tried to install GRUB, but it wouldn't work, then I booted off the recovery CD my friend let me borrow, and I guess it was made for Vista only, so when I booted back into Windows, I saw a Vista boot screen (even though it's Windows 7), and that's when I knew something was wrong. I logged on, and it said "preparing your desktop", which was weird, and I saw just a blue screen with "this copy of Windows is not genuine" on the bottom right corner of the screen. I think it might be booting to some sort of half-Vista, half-Windows 7 thing...I really need help 'cause my whole family uses this PC, I'm using the live CD right now

Is it too much to ask to have a working computer? All help is appreciated.

---

### Post by coffeecat on 2009-06-23
Perhaps if you explained precisely what you did, someone might be able to help you. After you deleted XP, what did you use to install Windows 7? If you've got the Windows 7 RC DVD you don't need a Vista Recovery disc, because the Windows 7 DVD has a recovery console. Besides, if you used a "recovery CD" (it would need to be a DVD for Vista anyway) from a friend, this was probably an OEM disc, which might account for the not genuine message.

So - did you do a fresh install or an upgrade install with a Windows 7 DVD, or something else? Have you got a Windows 7 product key? You need a product key specifically for Windows 7 RC - Microsoft are giving them out free at the moment, and as many as you need. Each key can be used on up to three machines, by the way.

---

### Post by rectec794613 on 2009-06-23
I deleted XP inside Windows 7, therefore, it was already installed. I tried to use the recovery console, but it keeps saying my admin password is invalid, even though I don't have one. Thanks for the response.
Yes I have the key in a txt file on the hard drive.

---

### Post by coffeecat on 2009-06-23
**rectec**, this is not meant unkindly, but reading your posts is like looking at a landscape through a pair of binoculars that's covered in cobwebs, dust and condensation. I get a rough idea of what's out there, but I can't make out the details.

> **rectec794613 said:**
> Is it too much to ask to have a working computer? All help is appreciated.

Not too much at all, but is it too much to ask what it is you are trying to do? Do you want to reinstall XP? Do you want to repair Windows 7? Do you want to repair grub so that you can boot up into Linux?

Whatever you want to achieve, you need to provide more information. What is your partition layout? Which OS is on which partition? How did you install Windows 7? How did you try to repair grub from the live CD?

> **rectec794613 said:**
> I tried to use the recovery console, but it keeps saying my admin password is invalid, even though I don't have one.

I may be wrong but I thought that Windows 7 wouldn't let you get away without creating an admin password. It's the same as Ubuntu: the first user's password is the admin password. Whatever, this password problem may be because of what you did with the Vista recovery disc.

---

### Post by rectec794613 on 2009-06-23
**coffeecat**, this is not meant unkindly, but reading your posts is like looking at a very confused cat, particularly because the cat is in a cup filled with coffee. (lol)
Well I wanna repair Windows 7, I just have Windows on one partition. It wasn't the recovery disc that did it, I tried numerous times before but the recovery console kept rejecting me.
No offense but, use your common sense, my Boot's all screwed up, instead I wanna go and join the army, no, of course I wanna fix it!
I installed Windows 7 from an ISO file from Microsoft using Daemon Tools.

---

### Post by rectec794613 on 2009-06-23
I still need help here, this is crucial!

---

### Post by sschnee on 2009-06-23
Do you have access to a computer with a DVD burner?  If so, I would do a couple of things.

1) Burn a Windows 7 DVD
2) Boot up from the DVD and try using the recovery console that I believe is on the Windows 7 DVD.  

I don't know if you need an activation ID (key?) for this.  You said you have one on your HD - you may as get it using a live CD, or go to the Microsoft website and get a new one.

Once you get Windows working, you will likely need to repair GRUB, but that is easy and has been described on this forum and many others.  Still, let us know if you need help with that.

Why don't you try that and let us know how it works for you?  Please include as much detail as you can - the more info you give us, the more we can do to help.

---

### Post by rectec794613 on 2009-06-23
No I don't have a DVD burner, but I *can* run Daemon Tools under WINE, using a download from MS, then possibly, boot from Daemon Tools from the BIOS boot menu. (I'll need a guide if there's a way) 
But all my data, programs, etc. will be on the old Windows partition, and believe me, copying and pasting the files doesn't help much.
Thanks for bearing with me on this, guys. I just need to repair the MBR. I'll try using MS-SYS again.

-Rob

---

### Post by rectec794613 on 2009-06-23
Actually, now that I have a new video card, I think Ima install Kubuntu, and get my favorite part of Linux back, Compiz-Fusion:D
I know this won't help with Windows, but if I can't get Windows working, I should set up a "base camp".

---

### Post by bodhi.zazen on 2009-06-23
I am sorry you are having problems with windows. 

I think it is best to direct your windows support questions to a windows forum or Microsoft.

It also sounds as if you are not using a legitimate version of Windows which may be the problem.

---

### Post by rectec794613 on 2009-06-23
No the Windows I'm using is 100% legal, how could it not be? It's a Release Candidate. I'm sorry if I'm shootin' ya guys down here, but I just want my PC to work 'cause my dad gets mad at me if he can't get on Craigslist or Mail Tribune, and I really wanna play my games, so anybody that knows how to fix MBRs, or how to bypass the password thing on the recovery console is welcome to help. I've been to a ton of other sites, as stated twice before, and don't mind me for emphasizing this, but: **_I NEED YOUR GUYS'S HELP_**
My whole family is counting on you guys to help me.

---

### Post by bodhi.zazen on 2009-06-23
You mentioned 3 versions of windows in your post. (XP, Vista, and 7).

You also mentioned :> I booted off the recovery CD my friend let me borrow which I do not think is legal (I could be wrong).

You also mentioned deleting your XP partition.

Hard to know what you did exactly, but I think you are almost certainly looking at installing a replacement OS from scratch.

Boot the Kubuntu CD and install away.

Tell your family it is Windows 7 Pre-view.

---

### Post by rectec794613 on 2009-06-23
> You also mentioned :
Quote:
I booted off the recovery CD my friend let me borrow 


My friend said he got it from Dell.

---

### Post by rectec794613 on 2009-06-23
Also, I'm trying to install GParted, but when I try to run it, it asks me for a password.:confused:
Is there a quick fix to this or am I gonna have to restart?

---

### Post by Saint_ on 2009-06-23
By illegal he meant using your friends vista disk which I also believe is illegal. BUT back to the matter at hand. Let's start from the beginning... what exactly happened when you tried booting to W7 without any recovery disks or anything? Did you get any specific error messages? Was it just a black screen with a blinking cursor? Things like that help us to help you.

Edit: I've got to go have my car looked at, so I'll try helping you once I get back (could be an hour or more), I'm sure others will lend a hand in the mean time

---

### Post by rectec794613 on 2009-06-23
As said before:> I guess it was made for Vista only, so when I booted back into Windows, I saw a Vista boot screen (even though it's Windows 7), and that's when I knew something was wrong. I logged on, and it said "preparing your desktop", which was weird, and I saw just a blue screen with "this copy of Windows is not genuine" on the bottom right corner of the screen.
And all I saw was that blue screen with the message at the bottom, not even a window with the option to activate it. Just blank. It's like the repair installed a (very) mini Vista on my machine.

I'm gonna play GTA 4 for a while, I'll check back in a few.

---

### Post by bodhi.zazen on 2009-06-23
The live CD has no password, ie a blank password. 

sudo -i 

and you are root.

just hit enter and you should be fine.

---

### Post by rectec794613 on 2009-06-23
Thanks, bodhi, but it still doesn't work.
I have a plan, I'm gonna install Kubuntu on a small partition, download and burn a rescue CD, and try and fix Windows. I'll check back if it works.

---

### Post by RJ12 on 2009-06-23
Also the disk you used probally has the drivers for his computer too. Becuase its most likely a OEM disk.

---

