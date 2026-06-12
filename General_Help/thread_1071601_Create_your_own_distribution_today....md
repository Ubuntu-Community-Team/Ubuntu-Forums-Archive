---
title: "Create your own distribution today..."
date: 2009-02-16
forum: General Help
---

### Post by grndslm on 2009-02-16
Use remastersys.

I created this guide, that I'd like other people to see.
[http://loscompanion.com/forums/index.php?topic=6456.0](http://loscompanion.com/forums/index.php?topic=6456.0)

Tell me what you guys think!

EDIT:  Ubuntu Forums version is here--
[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

---

### Post by grndslm on 2009-02-17
I did a little more tweaking to my guide again this morning.

Hopefully somebody finds this useful!

---

### Post by grndslm on 2009-02-18
Nobody likes it?? - :^(

---

### Post by LowSky on 2009-02-18
I don't undetstand what your trying to explain, because remastersys has been around for a good while. And its a decent program for making new instals but its really simple to use I dont see why you need to post a blog about it

---

### Post by grndslm on 2009-02-18
First of all.... it's not a blog.  It's a guide in post of a forum.

Sure remastersys has been around for awhile, but ANY noob could read this guide in about 5 min and create their own customized distribution TODAY!!

If you know of a more complete guide, then please show me.  It took me days trying to understand what folders to put in /etc/skel/, what to disable in GNOME Sessions & Services & sysv-rc-conf, that Usplash was buggy, that splashy spat out an error if you didn't use PNGs, how to change grub on the installed system, etc.

Thanks for the encouragement on my work, tho!  :-(

---

### Post by grndslm on 2009-02-19
I'm soo discouraged by the [lack of] response.

And could a moderator tell me why my submission to the Tutorials & Tips section isn't accepted?  I initially only sent a link to my guide, but then I submitted the whole formatted version of the guide for the consistency of Ubuntu Forums.  It should now be acceptable, so could somebody please do something about it, or forward it to someone who can?

---

### Post by grndslm on 2009-02-19
Surely somebody knows who is in charge of accepting threads into the Tutorials & Tips section... ???

---

### Post by grndslm on 2009-02-19
YESS!!  It finally got accepted in the Tutorials & Tips section!

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

Woot!!  I guess I can stop spamming the Gen Discussion forum now.

---

### Post by Tek-E on 2009-02-19
The only thing I can say against it is that it doesn't explain how the Linux OS actually works.  And that is what a lot of newbies need. They need to know how the operating system they are spending so much time on functions.  Its a good tutorial you posted...but I would recommend that newer people wanting to build custom distributions look into Linux from scratch where they work from the ground up building their own custom distribution

---

### Post by grndslm on 2009-02-20
People sure do like to nitpick.

The tutorial is clearly on how to create your own Debian- or Ubuntu-based distribution as quickly as possible.

If I wanted to explain how Linux works, kernel programming, device reverse engineering to create modules, init scripts (SysV -vs- BSD), etc... the guide would never end.  There's a word in our language you should look into --- organization.

If you have something in particular in mind that you feel like I missed... then by all means, let us see it.  Or if you have some other references that distro n00bs should read... post it here!

---

### Post by jamesnmandy on 2009-02-21
i am going to be perfectly honest, i give a rats behind how Linux works, i just want it to work for me, this guide, which i havent looked at yet because i just dont have time to mess with it right now sounds like it avoids explaining things i dont need to know, which is downright awesome.....

---

### Post by grndslm on 2009-02-21
:D :D :D :D :D :D :D

Ahhh.. Thank you!

:guitar:

---

### Post by grndslm on 2009-02-23
Made a few updates...

Now I need to figure out if there're any other restricted firmware/drivers I should add to my distro, particularly in the networking department like the broadcom chips (I'm certainly familiar with both NVidia & ATI)??  Some other decent examples of helpful software that's not included with Ubuntu are ntfs-3g & ntfs-config.

You guys got any more ideas like these to make my distro more compatible, which inherently makes it more adoptable?

---

### Post by abn91c on 2009-02-23
This is a better way to do a distro than having to do all that CLI coding
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by mpsii on 2009-02-23
Personally, UCK is UCKy for "creating your own distro".

Basically UCK only relabels and redoes graphics the last time I used it.

Using remastersys, while not hard, DOES actually allow you to either create a fully installable backup of your favorite stuff and your environment or create a distributable version of all the stuff you find appealing.

After all... one of the things I HATE is all the time spent getting the environment just the way you like it... just to have a hard drive crash or some other such osik.

Congrats, grndslm!!

You go boy and do what you want. Don't be discouraged by the lack of response.

---

### Post by grndslm on 2009-02-24
> **abn91c said:**
> This is a better way to do a distro than having to do all that CLI coding
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)
Yes, UCK is definitely yUCKy.  That was the first recommendation given to me for creating my own distro.  I was ecstatic enough to know that with UCK, I'd easily be able to edit my sources.list, upgrade packages to current, add a bunch of packages, and delete some packages.  Sad thing is that after I aptitude installed a huge list of packages, YUCKY would freeze in the conversion process.

UCK is nothing but command line, but you say remastersys is "CLI coding"??  WTF?  Why do so many people open their mouths when they don't know WTF they're talking about?

I have customized all the applets on my panels, changed fonts, changed icons & cursors, changed gtk, metacity, gdm, [& occasionally usplash] themes, customized gconf, turned the CapsLock key into an extra Ctrl key, trimmed the startup services, etc... and made all these settings consistent for all users created with the adduser command, including the "custom" LiveDVD user.  Boot my LiveDVD and you won't find much evidence that let's you know it's really just Ubuntu.  You can't do any of that kinda tweaking with UCK.

Reconstructor is another story.  I haven't tried it yet, but I don't need to because remastersys is exactly what I was looking for.  If anybody could tell me the difference between remastersys & reconstructor... I'd be all ears, however.

---

### Post by grndslm on 2009-02-24
> **mpsii said:**
> After all... one of the things I HATE is all the time spent getting the environment just the way you like it... just to have a hard drive crash or some other such osik.Exactly.  The reason remastersys got me all excited is because nearly every 6 months, I've been re-configuring multiple laptops and desktops by hand because I didn't know remastersys existed.  Now, I simply pop the CD in, give it a partitioning scheme, user, & pass... verify the info and then BAM... I've got Ubuntu already tweaked to just the way I like it.  I can hand it out to people and they can resize Windows partitions, use their wireless Broadcom chip, watch YouTube videos, etc.  You can't do any of that with the default Ubuntu LiveCD, and that's just the start of it.

> **mpsii said:**
> Congrats, grndslm!!

You go boy and do what you want. Don't be discouraged by the lack of response.Thanks, man!  I'm definitely gonna keep figuring out the ins and outs of Ubuntu and Linux for myself... adding stuff like the Wubi solution when I get a chance to talk to the Wubi dev.

---

### Post by grndslm on 2009-02-26
It wasn't even necessary to continue asking the Wubi dev questions about integrating Wubi with remastersys, because somebody already created a guide for it [here](http://ubuntuforums.org/showthread.php?t=1062504).

I've made a few formatting changes and now added the completed RESTRICTED FIRMWARE & DRIVERS section and WUBI section to my guide, which can now be found in my sig.

Happy times we live in... remastersys is the greatest thing that ever happened to Ubuntu & Debian.

---

