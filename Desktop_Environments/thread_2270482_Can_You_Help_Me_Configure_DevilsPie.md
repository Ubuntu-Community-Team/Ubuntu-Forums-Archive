---
title: "Can You Help Me Configure DevilsPie?"
date: 2015-03-23
forum: Desktop Environments
---

### Post by lambdafox on 2015-03-23
I am new to linux; so, I am finding it really difficult to filter out what is deprecated information on my issue...

I am running Xubuntu 14.10.

i have a Radeon video card.

I have two monitors:

The first is a Samsung computer monitor.
1600x1200 resolution
currently set to "left" so, the upper left corner is 0,0 on Xinerama (I think)

The second is a Vizio HDTV.
1920x1080

90% of the time, I do not have the Vizio powered on.  I really only use it with Kodi.

What I really want is for all of my windows and child windows to open on the Samsung.  If possible, I would like Kodi to open full screen on the Vizio.

[strike]From reading the forums I *think* I need to disable Xinerama. [/strike]

When I open the XFCE 4.10  display settings application, there are check boxes for turning off mirroring.  I did that, and it automatically turns my desktop into one big window stretched across the monitors.  I "think" that is what is meant when they refer to Xinerama, no? 

I do not see any setting for this in the Settings editor either.

[strike]March 26, update...  It looks like I need to set up "zaphod mode".  This, evidently must be done in xorg.conf...  Setting up zaphod seems to require a separate keyboard for each monitor.  I could use my bluetooth kb for kodi...[/strike]

March 29, update ... With a little more googleing, I think the answer I am looking for is DevilsPie.

Now I just need to figure out how to create a configuration file  to open kodi on the vizio, and "everything else" on the Samsung...

In rough pseudo code, here is what I want to do:

# when a window opens
if it is kodi
    open in a 1920x1080 window starting at 0,0 on the Vizio
    # would that be 1601x0 on the xinerama desktop?

else
    open with the upper left corner at 810x540
    # i think that would put "all other" windows on my Samsung in the lower right corner of the screen.

Can anyone who has used devilspie tell me if the "else" part of that will do what I think it will?   Will it catch chlid windows and put them there too, even if an application wants to put them somewhere else?

---

