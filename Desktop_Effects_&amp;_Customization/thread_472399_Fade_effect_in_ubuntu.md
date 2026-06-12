---
title: "Fade effect in ubuntu"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by Balvinder25 on 2007-06-13
Hi all,
         I have just installed ubuntu on my pc and im really just loving it  :p .It automatically configured few of my devices automatically..which i liked .like my epson printer c45..worked great in it and my blue tooth device worked great.i used windows xp earlier but got tired of viruses and system lockups..the only this missing is the fade effect tht we have in windows xp ..can we not get tht here in ubuntu..mind you i just have an i810e motherboard with an onboard display card no other things..:)...and i still find the apps to be alittle slugish..can there be any tweaks for this..any help would be really appreciated..

thanks and regards,.

---

### Post by aquavitae on 2007-06-13
Why sort of pc are you running - e.g. CPU, RAM, etc.  Ubuntu should not be sluggish on any computer  less than about 5 years old.  Do you have many services starting when you start up?

Beryl is great for all sorts of desktop effects, but is quite power hungry.  Its also beta software, so is not recommended for n00bs.

---

### Post by Balvinder25 on 2007-06-13
ahh..thnx for the quick response buddy.
i have a 1100mhz processor.
256 ram 
and a 40 gb harddrive.
i dont understand much abt the services tht should be running..so if you could let me know so i could chk them out..
Thanks ..

---

### Post by avik on 2007-06-13
256MB RAM isn't very much, though for Ubuntu it's fine.

On the other hand, if you find everything to be too slow, you could always install and use xubuntu-desktop, which substitutes the GNOME desktop environment with Xfce, a lighter, leaner DE.

---

### Post by aquavitae on 2007-06-13
Hmm, I was hoping you'd know how to check the srevices, cos I can't remember!  The last time I worried about them I was running Gentoo, which is different from Ubuntu anyway!You should have some sort of system monitor installed though, which will at least tell you what processes are taking up the resources.  Under KDE its ksysguard, accessed by Ctrl-Esc, but I'm not sure what it is in Gnome.

On your system, I wouldn't use Beryl.

---

### Post by Balvinder25 on 2007-06-13
hi all,
         im not so sure abt the xubuntu os but i would like to stick to ubuntu for the mean time..i chked the list of services tht were there .i had an evolution clien service runninng tht i stopped...secondlyt the cups for the printer was stopped..and blue tooth service was also stopped..the only thing working now are as below.

1 ) cpu frequency manager ( wonder what this does??)
2 ) graphical logical manager..( i think i knw what this is for)
3 ) hard disk tuning ( hdparm )??
4) speech communication ??

rest of the things are unticked..

i fear stopping anything i dont know..so guys help me on this..

and i just have one more quiry...i have a dual boot with windows xp with three partitions..1st one is fat32 thts read and write but the rest are only read only which i would like to change,,it appears as if ubuntu has only mounted partitions in read only mode..so any help on this would be great  ..

thanks n Regards..

---

### Post by eggdeng on 2007-06-13
You need to install a utility to be able to write to NTFS partitions. See 
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html]("http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html")

---

### Post by franck3d on 2007-06-13
Welcome to Ubuntu and the forum!
Can you describe the "fade effect" from XP that you miss?
I use both XP and Ubutnu every day and I'm not sure what you are referring to.

Also, Xubuntu is not a seperate OS, it is another window manager.
The operating system stays the same but the interface changes.
Xubuntu is much easier on system resources, but I find that straight Ubunutu is easiest to start with as most tutorials and info is based on the gnome environment.

And if you want to get into the beauty of beta beryl, you don't need the newest graphics card.
My wife and kids computer is running a Geforce 440 and only has 256 of ram and beryl is still a fun toy for them!

---

### Post by Balvinder25 on 2007-06-13
hi all,
          thnx for the quick reply i what i wondered was the fade effect tht we have in xp tht is when u clickon menus ..then u have the fade effect ..cant we use tht here.?

thxz in advance


balvinder

---

### Post by jfinkels on 2007-06-13
> **Balvinder25 said:**
> hi all,
          thnx for the quick reply i what i wondered was the fade effect tht we have in xp tht is when u clickon menus ..then u have the fade effect ..cant we use tht here.?

thxz in advance


balvinder

I don't think the menu animations are customizable BY DEFAULT. To gain that functionality (and much, much more customizability in that department), you would have to install beryl, but with 256 MB RAM, you may have a hard time with that.

---

### Post by avik on 2007-06-14
> **Balvinder25 said:**
> im not so sure abt the xubuntu os but i would like to stick to ubuntu for the mean time

Xubuntu *is* Ubuntu, but with a lighter desktop environment.  Just go into Synaptic (System->Administration->Synaptic Package Manager), find and install xubuntu-desktop, and the next time you log on, Xubuntu will be an option in the Sessions menu.

---

### Post by aquavitae on 2007-06-14
Kde has the fade effects you want, but is much heavier on resources than gnome.  Maybe KDE4 will be better...

---

### Post by Balvinder25 on 2007-06-14
hi all,
          i think i have found a way on how sort the prob out..i have decreased the menu show time to 0 ..by creating a .gtkrc-2.0 file with the following coding ..
gtk-menu-popup-delay = 0

and this has made the pc damn good ,,,
thanks all...
Balvinder

---

### Post by Balvinder25 on 2007-06-14
hi all,
            i have been wondering on how to use free pop or ypops in ubuntu..i miss the emails from yahoo ac..if there is a work around this please let me know.

and is there any way on how we can see the max vertical and horizontal sync rate for the monitor  for  tweaking of the xorg file..?

i have a 14" microtec monitor..n im currently using the following rates..works ok but just needed to chk..if there is some other  way to chk the supported sync rates..?

   HorizSync 35.5-55.5
    VertRefresh 65.5-85.5

Regards..

---

### Post by jfinkels on 2007-06-14
> **Balvinder25 said:**
> hi all,
            i have been wondering on how to use free pop or ypops in ubuntu..i miss the emails from yahoo ac..if there is a work around this please let me know.

and is there any way on how we can see the max vertical and horizontal sync rate for the monitor  for  tweaking of the xorg file..?

i have a 14" microtec monitor..n im currently using the following rates..works ok but just needed to chk..if there is some other  way to chk the supported sync rates..?

   HorizSync 35.5-55.5
    VertRefresh 65.5-85.5

Regards..

If you want your questions answered efficiently, please make one thread for each problem you are having and clearly describe your hardware and your problem.

---

### Post by aquavitae on 2007-06-15
> **Balvinder25 said:**
> 
and is there any way on how we can see the max vertical and horizontal sync rate for the monitor  for  tweaking of the xorg file..?

i have a 14" microtec monitor..n im currently using the following rates..works ok but just needed to chk..if there is some other  way to chk the supported sync rates..?

   HorizSync 35.5-55.5
    VertRefresh 65.5-85.5

Regards..

Search the internet - or go to the homepage for your monitor, you should find the technical specs within about 5min of looking

---

