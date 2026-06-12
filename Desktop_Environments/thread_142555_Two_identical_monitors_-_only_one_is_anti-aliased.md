---
title: "Two identical monitors - only one is anti-aliased?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by JimJones56 on 2006-03-10
OK folks, here's a strange one:

I've got a Radeon 9500 graphics card with dual heads. Plugged in to this are two identical NEC LCD monitors. I'm using Xinerama to expand the desktop across both monitors.

However, **only one of the monitors is anti-aliased.** The secondary one, on the right, looks perfect whilst text on the 'primary' one, on the left, is all jagged and horrible...

The entries in /etc/X11/xorg.conf are identical for each device; each of the* Device, Monitor and Screen* sections has the same settings: resolution, color depth etc. As mentioned earlier, I'm using Xinerama. I'm using the graphics card drivers from the CD.

Any thoughts would be appreciated - I've managed to get through most of the installation and setup with the help of this forum, but I couldn't find any previous answers on this topic. Thanks!

---

### Post by dcstar on 2006-03-10
[QUOTE=JimJones56]OK folks, here's a strange one:

I've got a Radeon 9500 graphics card with dual heads. Plugged in to this are two identical NEC LCD monitors. I'm using Xinerama to expand the desktop across both monitors.

However, **only one of the monitors is anti-aliased.** The secondary one, on the right, looks perfect whilst text on the 'primary' one, on the left, is all jagged and horrible...

The entries in /etc/X11/xorg.conf are identical for each device; each of the* Device, Monitor and Screen* sections has the same settings: resolution, color depth etc. As mentioned earlier, I'm using Xinerama. I'm using the graphics card drivers from the CD.

Any thoughts would be appreciated - I've managed to get through most of the installation and setup with the help of this forum, but I couldn't find any previous answers on this topic. Thanks![/QUOTE]
Are you 100% sure it is only text that is different?

Take a very close look at any detailed graphics and see if they are absolutely identical.

---

### Post by JimJones56 on 2006-03-10
Hmmm - the plot thickens... 

I tried to take a screenshot to show everyone what I mean but when I display the "un-aliased" screenshot on the right-hand (aliased) monitor, it displays perfectly. Equally, if I display a properly-aliased screenshot on the left-hand monitor, it looks crappy. It's almost as if Ubuntu is sending (and storing) the correct information but that the driver is rendering things on the left incorrectly?

Also, on closer examination, the left-hand ("un-aliased") monitor **is** actually anti-aliased, but not to the same extent that the right-hand is. The left-hand screen has a tiny amount of aliasing whilst the right-hand fonts look **much** smoother. On capital "W"s, for example, you can really notice the difference.

David, in answer to your question: Icons are noticably different - the yellow arrow on a Firefox shortcut is aliased on the right monitor and not on the left, for example. The 'preview' icons for a plain text document are different. The same thing happens with diagrams - those on the right look smoother than those on the left. Difficult to tell with photos.

Thanks again

---

### Post by engla on 2006-03-10
[QUOTE=JimJones56]Hmmm - the plot thickens... 

I tried to take a screenshot to show everyone what I mean but when I display the "un-aliased" screenshot on the right-hand (aliased) monitor, it displays perfectly. Equally, if I display a properly-aliased screenshot on the left-hand monitor, it looks crappy. It's almost as if Ubuntu is sending (and storing) the correct information but that the driver is rendering things on the left incorrectly?

Also, on closer examination, the left-hand ("un-aliased") monitor **is** actually anti-aliased, but not to the same extent that the right-hand is. The left-hand screen has a tiny amount of aliasing whilst the right-hand fonts look **much** smoother. On capital "W"s, for example, you can really notice the difference.

David, in answer to your question: Icons are noticably different - the yellow arrow on a Firefox shortcut is aliased on the right monitor and not on the left, for example. The 'preview' icons for a plain text document are different. The same thing happens with diagrams - those on the right look smoother than those on the left. Difficult to tell with photos.

Thanks again[/QUOTE]


It sounds to me as if it's the monitor hardware, not something that ubuntu does.

I mean, if you compare **bitmap pictures** like the smilies on this forum, or png files, they should look exactly the same; nothing in ubuntu, Xorg, gnome etc does anything to the rendering of those..

---

### Post by JimJones56 on 2006-03-10
It isn't the monitor hardware because I've just swapped them over and the problem persists; i.e. the monitor which was previously displaying correctly now looks different. Could be graphics-card-related I suppose but [cliché]everything works fine in Windows...[/cliché] 

I've also got rid of Xinerama - back to mirrored desktops - and the problem is still there.

Swapping them over did remind me (!) that the one with problems is connected via DVI whilst the 'good' monitor is using VGA, I wonder if that's the problem?

---

### Post by dcstar on 2006-03-11
> **JimJones56]It isn't the monitor hardware because I've just swapped them over and the problem persists said:**
> everything works fine in Windows...[/cliché] 

I've also got rid of Xinerama - back to mirrored desktops - and the problem is still there.

Swapping them over did remind me (!) that the one with problems is connected via DVI whilst the 'good' monitor is using VGA, I wonder if that's the problem?
Possibly there is a sync/refresh rate difference between the two outputs when used by Ubuntu, try "Auto-adjusting" the bad monitor.

---

### Post by JimJones56 on 2006-03-12
David - you're a genius! That's exactly the problem - the DVI monitor had a vertical rate of 60Hz; whilst the VGA monitor was using 75Hz. By setting the VGA monitor to 60Hz, they both look the same. Unfortunately, they both look rubbish. It appears that my monitors don't support digital syncs of > 60Hz so time to find a DVI-> VGA adaptor.

Thanks.

---

