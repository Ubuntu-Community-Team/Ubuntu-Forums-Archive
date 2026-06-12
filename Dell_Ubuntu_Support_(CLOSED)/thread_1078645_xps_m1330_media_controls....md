---
title: "xps m1330 media controls..."
date: 2009-02-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vrv123 on 2009-02-23
Hi experts,

I have a dell xps m1330 with Ubuntu 8.10 installed.
issues with media controls(images attached):
1) the remote control is not working with ubuntu 8.10.
2) only the volume buttons on the keyboard are working, the rest eject, play/pause etc are not working.

as the system was preinstalled with vista, the media center remote control used to work fine with it, but does not work with Ubuntu 8.10.

how do i get these to work, is there an alternative media control existing for Ubuntu 8.10 ?

please help me....

Thanks in advance.

---

### Post by vrv123 on 2009-02-23
pls reply....

---

### Post by PsychedelicReaction on 2009-02-23
i had the same problem months ago when i installed for the first time Intrepid Ibex, then it solved by itself. do you keep your system updated?

---

### Post by vrv123 on 2009-02-23
just curious, how did you resolve this ?
could you recollect if there was a particular package that you had installed to get this to work. 

my system is uptodate, i check and install updates on a daily basis.

not sure why this is not working.
pls let me know.

i was under the impression that all media controls + remote control would work outofthebox w/ ubuntu, but unfortunately it did not. may be i am missing a particular driver/package.

---

### Post by PsychedelicReaction on 2009-02-25
mmh no sorry, i can tell you that when i installed Intrepid Ibex the keys were not working since the beta versions (while no problem with Gutsy). then i just forgot them for some time and one day, a couple of months ago, i tried and they were working magically so i can't tell you if it was actually an update or some different package i installed.

---

### Post by TobyReynolds on 2009-02-26
> **vrv123 said:**
> Hi experts,

I have a dell xps m1330 with Ubuntu 8.10 installed.
issues with media controls(images attached):
1) the remote control is not working with ubuntu 8.10.
2) only the volume buttons on the keyboard are working, the rest eject, play/pause etc are not working.

as the system was preinstalled with vista, the media center remote control used to work fine with it, but does not work with Ubuntu 8.10.

how do i get these to work, is there an alternative media control existing for Ubuntu 8.10 ?

please help me....

Thanks in advance.

An expert I am NOT! But my experience is that my media buttons and remote worked out of the box with 8.10 (same laptop as you). What are you testing them in? Neither will work with VLC, and as far as I could find out there does not seem to be a workaround (somebody please correct me if I am wrong, which I would love to be!). Play/pause work in Totem though, and the L/R buttons (on the plus pad area of the remote) skip fwd and bkwd. You might also try the plus pad arrows and OK (tick) and BACK buttons to navigate folders in nautilus and see if it works.

You could check your keyboard shortcuts (System > Preferences > Keyboard Shortcuts). My "Play (or play/pause)" action is set to "XF86AudioPlay". If yours is not, click on the shortcut and press the play/pause button (you could try this anyway, even if it is already set, just to see if it registers a media key or remote control button press).

The "Eject" button will not work for me, and again I don't think there is a workaround. I think it is because it cannot unmount the drive first. If you right-click the CD icon on your desktop and click "unmount", then the button will work, but if you are going to do this you might as well just click "eject" from the drop down menu, which unmounts AND ejects.

Hope this helps
Toby

---

### Post by kevyin_ on 2009-03-01
they work with rythmbox for me

someone mentioned keytouch here [http://ubuntuforums.org/showthread.php?t=717314](http://ubuntuforums.org/showthread.php?t=717314)

i'm trying that out atm

---

### Post by PsychedelicReaction on 2009-03-02
i just upgraded to Jaunty and the problem is back. they work fine with totem but not with banshee.

---

### Post by nwadams on 2009-03-02
i have an xps m1330 too. They seem to work fine in hardy. except for the eject button of course. But that isn't a problem with the button assignment. It is a problem with the way ubuntu handles cd drives because it is a slot loading rather than the traditional type of cd drive. 

My biggest problem is still the brightness issue that only sort of works properly... </offtopic>

---

