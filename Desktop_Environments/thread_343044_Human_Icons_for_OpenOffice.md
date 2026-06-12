---
title: "Human Icons for OpenOffice"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Munchkinguy on 2007-01-20
[SIZE="5"]**Human Icons for OpenOffice**[/SIZE]

**Note: Ubuntu Feisty will be shipped with the Human Icons. I am working on them as you read this. As a result, this icon package mentioned below will *not* be maintained.**

With the adoption of the Tango-like "Human" icon theme in Ubuntu Dapper, the Industrial icons in OpenOffice began to stick out like a sore thumb.

The solution: a new icon file! Download it [here]("http://librarian.launchpad.net/6551119/images_industrial.zip").

Then, just go to "/usr/lib/openoffice/share/config/" and replace the old "images_industrial.zip" with the one you just downloaded.

If the theme is not applied, close OpenOffice, clear out the contents of "~/.ooo-2.0/user/config/imagecache", then restart the program.

This is, of course a work in progress, but an improvement at any rate.

---

### Post by Munchkinguy on 2007-02-16
===RELEASE NOTES FOR 0.3.2 (MANDATORY) ===

This is a patch release. The main goal is to replace some functions lost by adding the previous release.

_Improvements_
[LIST]
[*]Align/distribute icons from the Art Libre project
[*]The lost resize functionality problem should be fixed
[*]Tangoised "shape" icons now have shadows
[/LIST]

_Yet-to-do_
[LIST]
[*]Finish the "shape" icons and put shadows under them
[*]Improve small icon support
[/LIST]

[Click Here]("http://librarian.launchpad.net/6551119/images_industrial.zip") to download.



===RELEASE NOTES FOR 0.3.1===

_Improvements_
[LIST]
[*]Added many arrows
[*]Began conversion of "shape" icons to Tango
[*]Lots of new icons for Base
[*]Bullet navigation set
[*]Improved icons overall
[/LIST]

_Yet-to-do_
[LIST]
[*]Finish the "shape" icons and put shadows under them
[*]Improve small icon support
[/LIST]

[Click Here]("http://librarian.launchpad.net/6492033/images_industrial.zip") to download.

---

### Post by Morbett on 2007-02-17
The download stops and disappears at 1.8mb out of 3.3mb.  I can't download the whole file, in other words.  My download manager just disappears.

---

### Post by Sammi on 2007-02-17
Are these new icons going to be in Feisty?

---

### Post by Munchkinguy on 2007-02-17
> **Sammi said:**
> Are these new icons going to be in Feisty?

I hope so. I've been trying to contact the people in charge of OpenOffice on Ubuntu.

---

### Post by Munchkinguy on 2007-02-17
> **Morbett said:**
> The download stops and disappears at 1.8mb out of 3.3mb.  I can't download the whole file, in other words.  My download manager just disappears.

Try downloading it without the download manager. (ie via Firefox)

---

### Post by picpak on 2007-02-17
Wow, it looks like Abiword.

I'm impressed.

---

### Post by will m. on 2007-02-20
These icons look great!  But after installing them I discovered that they do not include the symbols and operators under the "Formula Editor" on the "Insert" toolbar.  There is still a text menu that indicates what the operators are but the symbols are helpful.

Any plans to include those in future editions?

Will M.

---

### Post by lapsey on 2007-02-20
hopefully someone will also address theming of openoffice outside of Gnome: under icewm it looks terrible!

---

### Post by cleniri on 2007-02-20
Looks fantastic!! The same look as Abiword and Gnumeric.

---

### Post by Obor on 2007-02-20
Nice one. I've been thinking about those ugly icons every time I've opened OO. These should definitely be a default in Feisty.

---

### Post by colonels1020 on 2007-02-20
Awesome! I sure hope these come preloaded in Feisty. :)

---

### Post by blime45 on 2007-02-20
Nice!

For anyone unsure of how to do this...

in terminal, change to whatever directory you downloaded the file to (most likely Desktop)
Then run "sudo cp images_industrial.zip /usr/lib/openoffice/share/config"

Done.

---

### Post by strabes on 2007-02-20
Openoffice (on ubuntu) comes with several icon sets by default. You can change them by going to Tools, Options, Openoffice.org, View, and selecting an icon theme under "Icon size and style." I find that the "industrial" icon theme works much better with my gnome desktop than the default set of icons.

---

### Post by macewan on 2007-02-20
Very nice work. I'd love to use these at work.
:KS

---

### Post by stalefries on 2007-02-20
This thread has been [Dugg]("http://digg.com/linux_unix/Ubuntu_Human_Icons_for_OpenOffice").

---

### Post by TriggerHappyChewie on 2007-02-20
Simple, but genius.  :-)

Thanks a bunch.

---

### Post by dantum on 2007-02-20
Good Stuff(tm)

---

### Post by sicofante on 2007-02-20
Very nice. Thanks a lot to the authors. These things bring consistency so they help usability.

I would suggest using the same icon for help as in the desktop (the '?' sign instead of the lifesaver.)

---

### Post by loell on 2007-02-20
> **strabes said:**
> Openoffice (on ubuntu) comes with several icon sets by default. You can change them by going to Tools, Options, Openoffice.org, View, and selecting an icon theme under "Icon size and style." I find that the "industrial" icon theme works much better with my gnome desktop than the default set of icons.

thanks ;) , those preinstalled icon looks nice , specifically the crystal

---

### Post by DnasTheGreat on 2007-02-20
Oooh.

OpenOffice *needs* a themeable icon set...
[SIZE="1"](For that matter, it also needs to be rethought from the beginning and gotten a clear direction rather than find-the-next-MsOffice-feature-we-don't-have-and-copy-it... especially Impress... it's just a mess.)[/SIZE]

> hopefully someone will also address theming of openoffice outside of Gnome: under icewm it looks terrible!
set $OOO_FORCE_DESKTOP to "kde" or "gnome"

~/.xprofile is a nice place to put it.

---

### Post by Munchkinguy on 2007-02-21
> **sicofante said:**
> Very nice. Thanks a lot to the authors. These things bring consistency so they help usability.

I would suggest using the same icon for help as in the desktop (the '?' sign instead of the lifesaver.)

I'll do that for the next release.

---

### Post by Munchkinguy on 2007-02-21
Question for discussion:
Should the shape icons have shadows or not?

---

### Post by loell on 2007-02-21
> **Munchkinguy said:**
> Question for discussion:
Should the shape icons have shadows or not?

i guess yes,

[http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines]("http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines")

---

### Post by ziadoz on 2007-02-21
Anyone got a mirror for these icons? The bandwidth has been exceeded.

---

### Post by mostwanted on 2007-02-21
If one of the people who downloaded this could upload it to Ubuntu Forums that would be great. That theme looks *de-li-cious!*

---

### Post by dré on 2007-02-21
Please also see the Wiki page here:

[https://wiki.ubuntu.com/OpenOfficeHumanIcons](https://wiki.ubuntu.com/OpenOfficeHumanIcons)

Perhaps we can add this as an interim solution.

Cheers

---

### Post by rko618 on 2007-02-21
yeah a mirror would be great.  Or even if someone could send me the icons I would host them on my site.

Now that this post has been dugg we definitely need to get the icons back up.

---

### Post by eyelessfade on 2007-02-21
Yeah, I can also mirror it.

---

### Post by Munchkinguy on 2007-02-21
> **eyelessfade said:**
> Yeah, I can also mirror it.

You can now download it from Launchpad at [http://librarian.launchpad.net/6492033/images_industrial.zip]("http://librarian.launchpad.net/6492033/images_industrial.zip")

---

### Post by helliewm on 2007-02-21
Wow they are brilliant. Thank you.

Helen:popcorn:

---

### Post by Aninhumer on 2007-02-21
Will it be possible to link OpenOffice's theme to the Gnome theme, so that we can use whatever theme we like?

I know I prefer standard Tango to the Human theme, and I'm probably not the only one.

---

### Post by mostwanted on 2007-02-21
> **Aninhumer said:**
> Will it be possible to link OpenOffice's theme to the Gnome theme, so that we can use whatever theme we like?

I know I prefer standard Tango to the Human theme, and I'm probably not the only one.

You can always download the Tango theme for OpenOffice for a quick fix.

---

### Post by bigken on 2007-02-21
kool infact very nice :)

---

### Post by sicofante on 2007-02-21
> **Aninhumer said:**
> Will it be possible to link OpenOffice's theme to the Gnome theme, so that we can use whatever theme we like?
That would be nice, but it would be the task of Ubuntu devs, I believe, not the OP's. Hopefully, we'll soon have those nice Forum Ambassadors asking things like that to the devs for us!

---

### Post by JohnPhys on 2007-02-21
Is there a way to get these installed in addition to all of the pre-installed themes?  I'd like to have as many themes as possible available.

---

### Post by H.E. Pennypacker on 2007-02-21
Sweet!  Thanks.

---

### Post by munkar on 2007-02-23
does this work for OOo 2.1? doesn't seem to for me.

the problem, i assume, is that in OOo 2.1 there is no "/usr/lib/openoffice/share/config/".

---

### Post by Mateo on 2007-02-23
Am I the only person who can't tell the difference between these icons and the default ones?

---

### Post by munkar on 2007-02-23
in my OO.o 2.1, images_industrial.zip is located in "/opt/openoffice.org2.1/share/config/".

so you open a terminal in the folder to which you've downloaded the icon set, and do

sudo cp images_industrial.zip /opt/openoffice.org2.1/share/config/

---

### Post by Munchkinguy on 2007-02-23
> **Mateo said:**
> Am I the only person who can't tell the difference between these icons and the default ones?

You have to clear your OpenOffice "cache".  In the home folder (in Nautilus), click Ctrl-H. The hidden folders will be revealed. Delete the folder called ~/.ooo-2.0/user/config/imagecache

---

### Post by Quillz on 2007-02-23
Good work.

---

### Post by t_ras on 2007-02-24
Kubuntu 6.10
OOO 2.0.4 
AMD64
Pasted with relevant permissions the zip. There are two more zips there: images and crystal_images.
No change in OOO, neither have I any "Icons and size" or anything alike to change icons.
nothing in cache.
Any ideas?

---

### Post by kiddo on 2007-02-24
It works well, except that there are no more "handles" for resizing images. Could you find out what is missing for this to work? I know this theme is the problem, because I actually made a tango theme for openoffice months ago (but never got around to releasing it).

Basically, single-clicking an image will not display the small green squares in the corners, so you can't resize it. Any idea?

---

### Post by Gargamella on 2007-02-24
wow I love them...the standard icons remember me old MS office... this is much much better ;D

thank you

---

### Post by Munchkinguy on 2007-02-24
> **kiddo said:**
> It works well, except that there are no more "handles" for resizing images. Could you find out what is missing for this to work? I know this theme is the problem, because I actually made a tango theme for openoffice months ago (but never got around to releasing it).

Basically, single-clicking an image will not display the small green squares in the corners, so you can't resize it. Any idea?

I'll look in to it, but if you do have a tango theme, I suggest you paste all the icons from my theme into yours and then it will include anything I have left out.

---

### Post by kiddo on 2007-02-24
Nah, my tango theme suffered the same problem! Thanks for looking into it, I'm curious what could be the problem :)

Oh yeah, by the way, icons for mathematical formulae are missing. To see the problem, go in **Insert>Object>Formula**. The floating toolbar will have no icons.

---

### Post by Munchkinguy on 2007-02-25
> **kiddo said:**
> Nah, my tango theme suffered the same problem! Thanks for looking into it, I'm curious what could be the problem :)

Oh yeah, by the way, icons for mathematical formulae are missing. To see the problem, go in **Insert>Object>Formula**. The floating toolbar will have no icons.

I think I've fixed the problem. Get the new release at [http://librarian.launchpad.net/6528993/images_industrial.zip]("http://librarian.launchpad.net/6551119/images_industrial.zip")

---

### Post by legalizemeth on 2007-03-01
> **kiddo said:**
> It works well, except that there are no more "handles" for resizing images. Could you find out what is missing for this to work? I know this theme is the problem, because I actually made a tango theme for openoffice months ago (but never got around to releasing it).

Basically, single-clicking an image will not display the small green squares in the corners, so you can't resize it. Any idea?I noticed the same problem with the resizing handles for drawing shapes in Presentation.  I reverted to the ugly stock icons and the handles came back. :(  Too bad, because otherwise your icons look very nice!

---

### Post by kiddo on 2007-03-01
another bug, alignment images in the image properties dialog are not shown

---

### Post by Munchkinguy on 2007-03-04
> **kiddo said:**
> another bug, alignment images in the image properties dialog are not shown

As noted above, I have released an update, which should fix most of these problems. Download the new icon file, clear your cache, and try it out. Please report any further problems.

---

### Post by kiddo on 2007-03-04
munchkinguy, I cleared ~/.openoffice.org2/user/config/imagecache/, tried rebooting, changing icon sizes in the preferences and all, but I still see exactly the same bugs as previously. Are you sure you uploaded the fix properly or something?

---

### Post by Munchkinguy on 2007-03-05
> **kiddo said:**
> munchkinguy, I cleared ~/.openoffice.org2/user/config/imagecache/, tried rebooting, changing icon sizes in the preferences and all, but I still see exactly the same bugs as previously. Are you sure you uploaded the fix properly or something?

Works fine for me. Make sure you're downloading from [http://librarian.launchpad.net/6551119/images_industrial.zip](http://librarian.launchpad.net/6551119/images_industrial.zip)

---

### Post by kiddo on 2007-03-05
Weird. I'm pretty damn sure I had downloaded the right one. I would recommend editing your posts in this thread so that there is only ONE link at the top (post #1) to avoid confusion. Thanks for the fix, it works wonderfully.

---

### Post by deadlydeathcone on 2007-03-06
From a recent feisty update for Open Office:

```
* Add tango icons from upstream CVS; merge some icons from the gnome-icon-theme, tango-icon-theme,
tangerine-icon-theme, human-icon-theme packages.
```

Did you have a hand in this, Munchkinguy? Furthermore, has anyone tried it? :)

---

### Post by Munchkinguy on 2007-03-07
> **deadlydeathcone said:**
> From a recent feisty update for Open Office:

```
* Add tango icons from upstream CVS; merge some icons from the gnome-icon-theme, tango-icon-theme,
tangerine-icon-theme, human-icon-theme packages.
```

Did you have a hand in this, Munchkinguy? Furthermore, has anyone tried it? :)

I'm working with some people to get it ready for Feisty. No promises though. Also, I believe that until I iron out all of the copyright issues (a complete audit of each new icon), the current one in feisty will not be as complete as mine.

---

### Post by DC@DR on 2007-03-07
Wow, this is so fantastic, but I wonder why it's in Ubuntu Cafe category? It would have been there in Tutorial&Tips, so people will find it easier. Many thanks for this, Munchkinguy :)

---

### Post by happy-and-lost on 2007-03-07
Nice. There's been a [Tango version]("http://www.deviantart.com/deviation/38088601") on dA for a while. Let's hope better theme support will be in future OOo versions.

---

### Post by kiddo on 2007-03-07
Coming through the updates today is OpenOffice 2.2 which has been patched to have a caramel splash screen and human/tango icons. I will most likely stick to that, I'm pretty happy as it requires less hacky intervention on my part.

---

### Post by Munchkinguy on 2007-03-07
I am pleased to announce that the [Ubuntu bug]("https://launchpad.net/ubuntu/+source/openoffice.org/+bug/42061") has been closed! I think we can all look forward to some better-looking icons in Feisty.

---

### Post by deadlydeathcone on 2007-03-07
> **kiddo said:**
> Coming through the updates today is OpenOffice 2.2 which has been patched to have a caramel splash screen and human/tango icons. I will most likely stick to that, I'm pretty happy as it requires less hacky intervention on my part.

If you don't mind, would you provide a screen shot? I'm not running Feisty and am kind of curious to see how it turned out.

---

### Post by 6205 on 2007-03-10
Amazing !!!!

---

### Post by Athanasius on 2007-03-18
I have been wanting this for a long time, thanks, I will keep watching for never versions.

I really don't know why Ubuntu isn't doing this, even if it was the iconset from the Tango project.

---

### Post by jkzubu on 2007-03-25
Not working on my Edgy.

-JK

---

### Post by FuturePilot on 2007-03-25
Wow! These look great. Thanks!:)

---

### Post by Munchkinguy on 2007-04-05
The Human/Tango icons have now shipped with Feisty Beta!

---

### Post by Bou on 2007-04-12
> **Munchkinguy said:**
> The Human/Tango icons have now shipped with Feisty Beta!

Sorry but, what do you have to do to get the Tango icons? I can only see the Human ones.

---

### Post by Munchkinguy on 2007-04-14
> **Bou said:**
> Sorry but, what do you have to do to get the Tango icons? I can only see the Human ones.

Go Tools --> Options --> View
and then select "Tango" from the "Icon size and style" dialog

---

### Post by SkyScrap on 2007-10-25
I've just upgraded to feisty, and now I have no icons at all in the toolbars! Anyone else with that problem?

---

### Post by dryder on 2007-11-02
Hi,

I would like to be able to choose which OO toolbar icons I use as I may prefer those that are in OO for XP.

Does anybody know how please?

Many thanks,
David

---

