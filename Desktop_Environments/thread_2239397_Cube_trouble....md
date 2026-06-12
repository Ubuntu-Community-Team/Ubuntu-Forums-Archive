---
title: "Cube trouble..."
date: 2014-08-13
forum: Desktop Environments
---

### Post by Mike_Walsh on 2014-08-13
Evening, all.

I'm trying to set up the desktop cube on Unity, in Ubuntu 14.04.

Most of the tutorials I've looked at over the last couple of days appear to show settings which on my version of Compiz don't seem to be there. I installed it from the Software Centre, and it says it IS the most up-to-date version.

For instance; In 'General', under 'General Options', on the 'Desktop' tab, there should be three entries. 'Horizontal Virtual Size', 'Vertical Virtual Size' ...and 'Number of desktops'. The last one is missing in my version!

Also, every single tutorial shows me a DIFFERENT way of going about the configuration. OK, so they cover the same options, but all seem to do it in a different order...and some imply that if you DON'T do things in a pre-determined order, it won't work. ( I can believe this last bit, as it was the same when setting-up my scanner; data package HAD to be installed before application...)

Is there a DEFINITIVE guide to setting the cube up, so that it will work correctly? There probably is, but I'm not too sure where to find it on the site.


Regards,

Mike.

---

### Post by deadflowr on 2014-08-13
> [COLOR=#000000]Is there a DEFINITIVE guide to setting the cube up, so that it will work correctly? There probably is, but I'm not too sure where to find it on the site.[/COLOR]

Even though it is old and closed the top link in this sub-forum still applies, with a few changes here and there.
[Wiki page from the cube thread here]("https://help.ubuntu.com/community/CompositeManager#Cube_And_Effects_for_Ubuntu.2C_Xubuntu.2C_Lubuntu.2C_Kubuntu_and_Edubuntu_in_release_10.04.2C_11.10_and_12.04")
Change number one would be that you only need to install compiz-plugins for 14.04, where as older versions like 12.04 need compiz-plugins-extras.
Change number two would be 3d windows got busted sometime around 12.10 and has yet to be fix so don't bother enabling it, unless you like distorted screens.

But basically the method which works is to disable the unity plugin change the desktop from wall to cube, enable rotate(adjust the zoom here if you want), and then re-enable unity plugin.
I believe you need to turn off and on the unity plugin or else it gets confused about what is happening.(Is it still running the wall or is it using the cube?) Which from memory, causes it to start acting up, if that makes sense.


As far as the number of desktops missing, it could be either that it was not under development anymore or that it was no longer considered core or needed and as such simply removed.
There have been a couple things like that in compiz for 14.04, most notably the fire animation plugin.
But if it bothered you that it did not exist on your system, don't worry you are not alone.

---

### Post by mc4man on 2014-08-14
from compiz changelog
> compiz (1:0.9.11+14.04.20140423-0ubuntu1) trusty
.....
 [ Chris Townsend ]
  * Remove the Number of Desktops option in CCSM as this option confuses
    Compiz and is really no longer needed since the Horizontal/Vertical
    Virtual Desktop Size is what is used for determining the size. ([LP: #1289820]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1289820"))

---

### Post by Mike_Walsh on 2014-08-16
Thanks for replying guys, and sorry for the late response.....I've got so many posts in different forums on the go at the moment, it's a job keeping track of them all..!

Thanks, deadflowr; yeah, that's pretty much what most of them say, it's just the order in which you're supposed to do things seems to change, depending on which blog post you're reading. I just wondered if there was some sort of 'official' version, that's definitive..?!

mc4man; I thought it might have been something along those lines. There's an absolutely bewildering array of sites out there, dealing with this very issue.....but most of them seem to be dealing with 12.04, 12.10, 13.04; a few releases back, anyhow. I guessed with this being such a popular desktop tweak, it would most likely still be under some form of development, so.....changes DON'T surprise me. Thanks for that!

Regards,

Mike.

---

