---
title: "Swap partition not being utilized"
date: 2005-08-13
forum: Desktop Environments
---

### Post by TGDuff on 2005-08-13
I have a swap partition that is not being used by the OS.  My system memory is being used just fine but swap space is shown with 0k used.  It is listed in fstab as:

/dev/hda7 none swap sw 0 0

I have used the mkswap and swapon operations on the partition to no avail.  I would prefer not reinstalling the OS or deleting/recreating the swap partition (root is on hda8 ).  

Any assistance would be appreciated.

---

### Post by nad on 2005-08-13
Use a partition editor to confirm the location of your swap space.

There will be no need to reinstall the os. Let's try to figure out what is going on.

---

### Post by PeP on 2005-08-13
Depending on your amount if ram you may just don' t need it: how much do you have?

---

### Post by TGDuff on 2005-08-14
I only have 512MBs of RAM in my system.  And the partition is listed as type 82, linux swap.  

My PC appears to run fine without the swap being used.  I would just feel more comfortable if it was used.

---

### Post by nad on 2005-08-14
"Only 512 MBs" of ram! I run servers with less memory!!! If your system doesn't need the swap space it won't use it.

As far as the location of your swap partition, I am sorry that you misunderstood what I meant. Is your swap partition correctly listed as /dev/hda7 in fstab and your partition editor?

---

### Post by TGDuff on 2005-08-14
[QUOTE=nad]"Only 512 MBs" of ram! I run servers with less memory!!![/QUOTE]

lol  Sorry, I am coming from Windows :)

Yes, my swap partition is listed correctly as /dev/hda7.  The reason I write this post is because I noticed activity on my swap on a prior installation on this system.  I decided to try Gentoo but found it to be much too time consuming.  I then switched back to Ubuntu (formatting the linux partitions in the process) and now there is no swap activity.

---

### Post by Hikaru79 on 2005-08-14
Type 'free' in a terminal and paste the output =)

---

### Post by TGDuff on 2005-08-14
[IMG]http://img.photobucket.com/albums/v249/TGDuff/Screenshot-tgduffubuntu-home-tgduff.png[/IMG]

---

### Post by Hikaru79 on 2005-08-14
Well, there you go =) You have a whole gig of swap space -- its just not being used because of your 512 MB of ram, only about 150 MB of it is being used by anything. Swap only gets used when you run OUT of ram.

This is a good thing, because Swap is SLOW. Swap basically is a portion of your harddrive that can act as a temporary ram disk. Reading and writing to and from your hard drive is MUCH slower than reading and writing to RAM, therefore you generally should be pretty happy about not having to use swap space. Fear not, when you need the space, Ubuntu will know to use it.

In other words, your 'free' output says that everything is going as planned. Nothing to worry about.

---

### Post by az on 2005-08-14
Open fifteen differrent photos in the gimp at the same time.  Browse some web pages and start Open Office.   Do all of this at the same time.

Check your memory again. Post your results.

---

### Post by TGDuff on 2005-08-14
[IMG]http://img.photobucket.com/albums/v249/TGDuff/70ab453d.png[/IMG]

Cool :) Was a little worried there for a second.  Thanks for the assistance, everyone.

---

### Post by Hikaru79 on 2005-08-14
=) Glad to hear it. By the way, how do you get those neat screenshots, that only show one window at a time with that neat drop shadow effect? :)

---

### Post by TGDuff on 2005-08-14
I am not sure where the drop shadow comes from but the window comes from alt+printscreen.

---

### Post by az on 2005-08-14
"alt+printscreen."

Whoa!  Never did that before!  Cool!

---

### Post by rwabel on 2005-08-15
[QUOTE=azz]"alt+printscreen."

Whoa!  Never did that before!  Cool![/QUOTE]
 that means it takes only a screenshot of the active window, think it's same under windows. very handy stuff

---

