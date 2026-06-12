---
title: "Too much KDE"
date: 2006-03-11
forum: Desktop Environments
---

### Post by nmastae on 2006-03-11
Last night I installed (apt-get) the KDE (not Kubuntu) desktop over Gnome using the default settings. However, I have "only" a P3, 768mb PC100 RAM, 20 gig HD, and this program is straining my system: taking rather a long time to access files, etc.

How do I know which of the zillion little programs to remove (to speed things up) and how to I clear out any traces of them afterwards?

For instance, I, personally, don't need the development tools, nor all the default games.

Thanks for your guidance in this.

---

### Post by aggiechemist on 2006-03-11
I would say the number of installed programs is probably not the problem. The only ones that matter are the ones that are actively running.

I seem to recall getting things a little faster by taking a few steps to simplify what is going on:

1. Only one desktop. On the pager preferences, turn the number down to just one.

2. Get rid of all the cute little apps on the toolbar. You don't need the pager running, or the weather, or the inbox monitor, or a thousand other options. Have the toolbar list the running apps, the buttons to open menus, and the clock. Or even just get rid of the clock too.

3. I once read somewhere that using a very plain background gives another MB or two back to the ram.

4. Check your visual preferences. Don't use transparency, fun boucy notification icons, or anything even slightly fancy. Minimalist is the idea here.

5. If you are brave and/or bored and/or good with linux, try redoing you kernel. I am just learning how myself, but it is not that bad and should give a performance boost.

---

### Post by aysiu on 2006-03-11
768 MB of RAM isn't modest at all. I'm running on 512 MB of RAM, and KDE *flies*.

You can try this, though.
Go to KMenu > System > Konsole and type ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` follow the wizard and choose "fewer effects," allowing only image previews and a desktop wallpaper.

---

### Post by GeneralZod on 2006-03-11
As a previous poster says, the number of apps you have *installed* shouldn't make a jot of difference.  Since you've previously been running GNOME, I'm going to assume that DMA is already enabled - if not, you should definitely enable it.  I ran KDE for ages on a Athlon 1500 with 256MB (upgraded to 384MB a few weeks back) and I currently have a crap Java app I wrote, konsole with 7 tabs, Firefox with 29 tabs, Kontact, kile, kdvi, kpdf, 6 konqueror instances, 2 kdesvn instances, kopete, and ~20 source files open across two instances of kate (not to mention the bunch of tray apps and background processes like kbluetoothd, etc!), and everything's fine - at worst, there is maybe 2 seconds of swapping when switching to apps I haven't used before.  Firefox is by far the most sluggish app here.

One thing that you definitely will notice though is that the startup speed for many apps is slow - this seems to be true of Linux in general (as it is heavily dependent on shared libraries which must be linked each time you start them) but is apparently doubly true of C++ apps, as the linker is not as well optimised (yet) for C++ (I think :))

What's the precise issue you're having?

---

### Post by nmastae on 2006-03-12
[QUOTE=aggiechemist]I would say the number of installed programs is probably not the problem. The only ones that matter are the ones that are actively running.

I seem to recall getting things a little faster by taking a few steps to simplify what is going on:

1. Only one desktop. On the pager preferences, turn the number down to just one.

2. Get rid of all the cute little apps on the toolbar. You don't need the pager running, or the weather, or the inbox monitor, or a thousand other options. Have the toolbar list the running apps, the buttons to open menus, and the clock. Or even just get rid of the clock too.

3. I once read somewhere that using a very plain background gives another MB or two back to the ram.

4. Check your visual preferences. Don't use transparency, fun boucy notification icons, or anything even slightly fancy. Minimalist is the idea here.

5. If you are brave and/or bored and/or good with linux, try redoing you kernel. I am just learning how myself, but it is not that bad and should give a performance boost.[/QUOTE]
Thank you for these tips.  I will try them. 

So much to learn!

---

### Post by nmastae on 2006-03-12
[QUOTE=aysiu]768 MB of RAM isn't modest at all. I'm running on 512 MB of RAM, and KDE *flies*.

You can try this, though.
Go to KMenu > System > Konsole and type ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` follow the wizard and choose "fewer effects," allowing only image previews and a desktop wallpaper.[/QUOTE]
I will try this. Thanks Aysiu.

BTW, I tried the "keeping the menus clean" trick and it didn't work for Gnome. Many KDE apps in those menus. Exasperating!

---

### Post by nmastae on 2006-03-12
[QUOTE=GeneralZod]As a previous poster says, the number of apps you have *installed* shouldn't make a jot of difference.  Since you've previously been running GNOME, I'm going to assume that DMA is already enabled - if not, you should definitely enable it.  I ran KDE for ages on a Athlon 1500 with 256MB (upgraded to 384MB a few weeks back) and I currently have a crap Java app I wrote, konsole with 7 tabs, Firefox with 29 tabs, Kontact, kile, kdvi, kpdf, 6 konqueror instances, 2 kdesvn instances, kopete, and ~20 source files open across two instances of kate (not to mention the bunch of tray apps and background processes like kbluetoothd, etc!), and everything's fine - at worst, there is maybe 2 seconds of swapping when switching to apps I haven't used before.  Firefox is by far the most sluggish app here.

One thing that you definitely will notice though is that the startup speed for many apps is slow - this seems to be true of Linux in general (as it is heavily dependent on shared libraries which must be linked each time you start them) but is apparently doubly true of C++ apps, as the linker is not as well optimised (yet) for C++ (I think :))

What's the precise issue you're having?[/QUOTE]
I think you're right about the longer startup time for most applications. I think this is primarily what I'm noticing.

Thanks for weighing in on this issue.

---

### Post by Adrian on 2006-03-13
[QUOTE=nmastae]BTW, I tried the "keeping the menus clean" trick and it didn't work for Gnome. Many KDE apps in those menus. Exasperating![/QUOTE]

You can always remove them manually from the menu editor. Removing an item from the menus in one desktop environment doesn't remove it from the menus of the other.

---

### Post by nmastae on 2006-03-14
[QUOTE=Adrian]You can always remove them manually from the menu editor. Removing an item from the menus in one desktop environment doesn't remove it from the menus of the other.[/QUOTE]
Update: I found another set of instructions that removed KDE from Gnome.

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*


To get Gnome out of KDE I did this, and while I am just becoming aquainted with that desktop, I think it worked:

$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo &#8216;OnlyShowIn=KDE;&#8217; >> $i
# fi
#done

I found those instructions here: 
[http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

---

