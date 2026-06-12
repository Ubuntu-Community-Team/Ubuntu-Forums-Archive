---
title: "Shortcuts gone wrong and prefered apps gone"
date: 2007-06-26
forum: Desktop Environments
---

### Post by felipe82 on 2007-06-26
Damn it, I just got Ubuntu working like I wanted to, a then this happens.

I had desktop shortcuts for my 2 NTFS partitions (Felipe and Documents, both were there by default), and I added shortcuts for Home folder, Computer and Network, by dragging them from the Places menu. They all worked fine, but today they started to go wrong one by one. They changed the icon and name from Home to nautilis-home.desktop for example, and when I tried to open them gedit shows up trying to edit the file :(
Also when I open the Computer folder from the Places menu, all items are *messed* up as well. I tried dragging shortcuts from everywhere in the menu and they all lokk the same.

And the other thing, all my programs associations are gone. When I double click a document, I get a "Cannot open /media/sda2/153319839.pdf: No application suitable for automatic installation is available for handling this kind of file." for example. I have to manually select an app from the list.

Here's a screenshot of some of the problems.

I just installed TexLive from a DVD iso, and I mounted it with these scripts:
[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)

I think that's about all I've done all day, besides web browsing and managing some files. I use Beryl too, but even with a fresh reboot without running it, the problem persists.

Help please! I was just getting used to Ubuntu working perfectly!

---

### Post by ComplexNumber on 2007-06-26
it seems like it *may* be a problem with your mime types.

go into synaptic and reinstall the following:
gnome-mime-data
mime-support
shared-mime-info

you may have to log out then back in again.

---

### Post by felipe82 on 2007-06-26
Thank you sir! That solved the icons problem.

Now, I'm still having problems with associated programs, when I try to open a jpg, png, avi or mov file, I now get an error like this:

[I]The filename "image_35482.jpg" indicates that this file is of type "jpg document". The contents of the file indicate that the file is of type "JPEG image". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "JPEG image", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/I]

If you read the first paragraph carefully you can see it's kind of a silly error...

Is there anyway to just reset all the file extensions and apps associations, and leave them all by the default ubuntu settings (like when you first installed it)?

thx again

---

### Post by ComplexNumber on 2007-06-26
ahhh well, glad the mime issue is sorted.

right click on a jpg file, for instance, and select 'properties', then select the 'open with' tab. does it show any programs at all?

i'm wondering if that script that you ran earlier overwrote various files when it should have added to the contents instead. that sometimes happens, and the mime data gets overwritten. thats why a reinstall of those packages that i mentioned about is necessary.

---

### Post by felipe82 on 2007-06-26
It does show all the installed programs that can open the file in the "open with" tab, it even shows which is the prefered one. I think is not a problem about file associations, because if I rename a file that I can't open normally with a double click, then I can open it with no problems.

---

### Post by ComplexNumber on 2007-06-26
i don't really know what to suggest. it's almost like the system just needs to be reset and that there isn't actually anything wrong at this point.
try rebooting and see if that returns it to normal.
i would have thought merely logging out then in would suffice.

---

### Post by felipe82 on 2007-06-27
aha! fixed it!

Apparently it's very old bug (like 2 years), I found the bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/19101](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/19101)

And after a lot of ranting posts for 2 years someone finally types in the solution:

```
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus
```

It worked for me.

Someone really need to warn new Ubuntu 7.04 AMD64 users to NEVER install gDesklets (remove from automatix at least, I'll send them an email), it didn't even work, and when I got it to work I realized that there weren't than many desklets out there, so it gave me nothing but these 2 bugs in the end.

Apparently screenlets work better, if you want to give them a try.

thx for all the help ComplexNumber

---

### Post by ComplexNumber on 2007-06-27
yeah, there is a command called update-mime-info, but i've never used it. i discovered it when i typed in "update-" then pressed the TAB button when i was looking for the exact sysntax of updating the icon chache for various icon themes, and it brought up a whole load of 'update-whatever' files

---

