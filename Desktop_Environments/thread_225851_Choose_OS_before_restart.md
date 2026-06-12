---
title: "Choose OS before restart?"
date: 2006-07-30
forum: Desktop Environments
---

### Post by allanlewis on 2006-07-30
Is it possible to run a command "reboot into windows" from Ubuntu? What I mean is to have a command which restarts the PC and then boots into Windows, which is not the default OS in GRUB. (I've set Windows to location 0 in my GRUB menu; Ubuntu is location 5.)

Perhaps it is a bit much to ask, but could the reverse be done in Windows (XP Home), i.e. a "reboot into Linux" command/shortcut?

Thanks in advance!

---

### Post by Tomosaur on 2006-07-30
Not without hitting grub first, no. The most you could do is write a script which sets windows to the default OS before the system goes down, and another script which sets ubuntu back to default on the next linux-boot. You can't access your linux partitions from within windows, so you won't be able to touch your grub setup from there unfortunately.

---

### Post by allanlewis on 2006-07-30
> **Tomosaur said:**
> Not without hitting grub first, no. The most you could do is write a script which sets windows to the default OS before the system goes down, and another script which sets ubuntu back to default on the next linux-boot. You can't access your linux partitions from within windows, so you won't be able to touch your grub setup from there unfortunately.

I can access my Linux partitions! See [http://www.fs-driver.org/](http://www.fs-driver.org/) (and some others too). (Obviously, if I want to save text files I have to use a text editor that can save in unix lf format, but that's not usually a problem.)

So could you give me an example of a script to do what you describe? I'm not familiar with sh scripting.

Thanks in advance.

---

### Post by jonnymccullagh on 2006-07-30
I've actually seen something like this when I used to use Suse - Suse 9.3 so it was over a year ago but it when you choose K-Shutdown there was a drop down allowing you to choose which OS from your Grub that you wanted to boot back into.
I imagine that something similar could be done on Ubuntu. It is only useful if you are still dual booting - I can do without it myself now.

---

### Post by Tomosaur on 2006-07-30
Interesting, I'd never heard of fs-driver before.

About the script - I'll have a tinker around and see what I can come up with, but I don't know when it'll be safe and ready to use. I'll put this thread on my subscription list and remember to get back to you when I'm done. Thanks for the link though, I'll have a look at it.

Also, I see you're near me :P I live in Liverpool.

---

### Post by allanlewis on 2006-07-30
> **jonnymccullagh said:**
> I've actually seen something like this when I used to use Suse - Suse 9.3 so it was over a year ago but it when you choose K-Shutdown there was a drop down allowing you to choose which OS from your Grub that you wanted to boot back into.
I imagine that something similar could be done on Ubuntu. It is only useful if you are still dual booting - I can do without it myself now.

Yeah, I seem to remember that from my experiments with Mandriva (which uses KDE). Perhaps someone with more programming knowledge than me could find the relevant bit of the KDE sourcecode?

(I've also posted a [feature request]("http://gnomesupport.org/forums/viewtopic.php?p=52596") on the Gnome forums to see if any Gnome-savvy developers can help.)

---

### Post by allanlewis on 2006-07-30
> **Tomosaur said:**
> Interesting, I'd never heard of fs-driver before.

About the script - I'll have a tinker around and see what I can come up with, but I don't know when it'll be safe and ready to use. I'll put this thread on my subscription list and remember to get back to you when I'm done. Thanks for the link though, I'll have a look at it.

Also, I see you're near me :P I live in Liverpool.

Thanks, I await your prototypes!

---

### Post by Tomosaur on 2006-07-31
EDIT: This got bumped and I'd forgotten all about it. The script people are talking about here is old and probably pretty unsafe if you do anything wrong. The link in my sig is the updated version, and is much safer (and more powerful), so if you're interested, use that one. In case you can't see my sig, [here's the link](http://www.ubuntuforums.org/showthread.php?t=228104).

---

### Post by allanlewis on 2006-07-31
Thanks so much! I'd be happier using the generic version so I can use it in the future when I install kernel upgrades and/or delete old ones.

(You could have saved the scripts as text and attached them that way ;) )

Thanks again,
Allan.

PS Perhaps post this to a mod for the "HOWTO" board?

---

### Post by Tomosaur on 2006-07-31
Yeah, guess I could've just made a .txt lol. Added one now anyway.

I dunno whether this is HOWTO worthy really. As far as scripts go, it's kinda messy, and it relies entirely on XP being the last item in the menu. By far the most useful thing in it is the ability to just pass it the menu item you wish to load, which I guess is a bit more noob-friendly than editing the menu.lst by hand.

---

### Post by ciscosurfer on 2006-08-06
@Tomosaur

Yet again you surprise and amaze me!  While the script might be crude (your words), it is concise and succinct.  Cheers!

---

