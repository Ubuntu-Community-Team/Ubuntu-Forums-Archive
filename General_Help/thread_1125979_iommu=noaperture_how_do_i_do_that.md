---
title: "iommu=noaperture how do i do that?"
date: 2009-04-14
forum: General Help
---

### Post by jackslap on 2009-04-14
Hello, I'm new to ubuntu and linux all around.  I am knowledgeable about XP however and have been fooling around with computers for about 6 years.  I don't understand much about DOS (can do lame stuff like pingip, tracert, ipconfig..., but can't navigate to a file or run a program from DOS)and I don't speak any computer languages.

I installed ubuntu in the windows environment (option when the ubuntu image was mounted) and everything went smooth.  Upon reboot I saw the ubuntu logo loading, but then this dark DOS looking screen popped up with the message about "64MB memory will go missing" and "enable iommu in BIOS".

I searched that topic on google and came up with I need to set iommu=noaperture.

The problem is I don't know how or where to do that.  I tried typing it in on that DOS looking screen when it gave me some DOS command prompt with the command initramfs:  but needless to say that did nothing.  I read something about GRUB but I don't know what that is or how to use it.

My question is, where do I go to make this setting change?  Is it something I can do while in XP, or do I need to have Ubuntu running?  I can't get Ubuntu running because it holds up on this screen.  Help much appreciated.  Thanks for taking the time to hear a rookies problem.

---

### Post by jackslap on 2009-04-15
uhhh...bump?

---

### Post by dcstar on 2009-04-15
> **jackslap said:**
> 
.........
I installed ubuntu in the windows environment (option when the ubuntu image was mounted) and everything went smooth.  Upon reboot I saw the ubuntu logo loading, but then this dark DOS looking screen popped up with the message about "64MB memory will go missing" and "enable iommu in BIOS".
.........

It is a basically obsolete message regarding AGP video, you can safely ignore it as even if you did lose 64MB (really only address space), it is a tiny fraction of the RAM you have.

I do not know why it was put in the particular kernel that outputs this message on boot, all it does is panic people unnecessarily.

---

### Post by jackslap on 2009-04-15
Thanks for the reply but it didn't really answer my question.  I need to find a way to get around this error because it is preventing my Ubuntu install from booting up.

I get to a ubuntu loading screen, then a black screen pops up with that particular error message on it and what looks like a command prompt that says

initramfs:

It seems as if it is waiting for input from me, but I don't know what to do.  That is what I am asking.  There is no IOMMU option in my mobo BIOS that I can see.  

Anyone help on this one?

---

### Post by jackslap on 2009-04-15
Someone has got to know this one.

How do i boot up Ubuntu around this error message?  I've tried a re-install and same thing.

Just need to get it started, don't care if the message shows up everytime.  Need a way around it.

---

### Post by bkwillard on 2009-04-17
My problem is exactly as jackslap stated it.  I read a lot of thread about "editing kernal" and iommu=noaperture etc....but my problem is I just don't know where to begin.  How can I edit something that isn't installed?

In jackslaps case, it looks like he installed from Windows...I'm trying to install on bootup, but it looks like even if I install through windows I'll end up right where jackslap is.

I'd really appreciate an explanation from square one: I have this message on my screen in dos (or something like dos).  It just sits there.  Now what do I do?

Thanks so much to anyone who can help me and jackslap out.  Very appreciated.  I haven't come across an issue that was so hard to find beginner info on.

---

### Post by fballem on 2009-04-17
I don't know if this will help or not, but [http://ubuntuforums.org/showthread.php?t=971671](http://ubuntuforums.org/showthread.php?t=971671)

Regards,

---

### Post by dcstar on 2009-04-17
> **jackslap said:**
> Thanks for the reply but it didn't really answer my question.  I need to find a way to get around this error because it is preventing my Ubuntu install from booting up.

I get to a ubuntu loading screen, then a black screen pops up with that particular error message on it and what looks like a command prompt that says

initramfs:
.........

That message has nothing to do with your problem, it is an **informational** message and making it go away will not make your system boot.

There are a multitude of issues that can cause the initramfs prompt, you would be well advised to search out posts with similar problems (and that means nothing to do with aperture messages).

---

### Post by bkwillard on 2009-04-21
> **fballem said:**
> I don't know if this will help or not, but [http://ubuntuforums.org/showthread.php?t=971671](http://ubuntuforums.org/showthread.php?t=971671)

Regards,

Thanks for the link. I didn't find a solution for my problem there, but it did, somehow, lead me to my solution.  I was unable to install Ubuntu at all, because the installation would not continue past the error.  I discovered the solution in post by maheshjagadeesan here:

[http://ubuntuforums.org/archive/index.php/t-587168.html](http://ubuntuforums.org/archive/index.php/t-587168.html)

He stated that he added the boot parameter (I think by hitting F6) of "all_generic_ide".  This worked for me, at least to get it installed.  I continue to see a message on boot up of ubuntu, but it does not halt...I can live with that.

---

