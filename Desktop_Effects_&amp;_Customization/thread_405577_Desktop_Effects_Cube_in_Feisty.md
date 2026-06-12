---
title: "Desktop Effects Cube in Feisty"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by Biscuitpie on 2007-04-09
Hi,

I recently downloaded and burned the Feisty Live CD to test to see if the desktop effects work. The wobbly windows worked fine, however I don't know how to use the cube. I used Ctrl+Alt+Left-Click (I Googled it). Am I doing something wrong, or is it Feisty?

Video Card: Intel i915

Thanks.

---

### Post by picpak on 2007-04-09
It's ctrl+Alt+Left Arrow.

---

### Post by Biscuitpie on 2007-04-09
Really? I thought that would just move to the workspace over, not use the cube, I thought the cube was something you could control with your mouse (which would be fun). =/

---

### Post by Biscuitpie on 2007-04-09
Just tested it, that just brings me to another workspace.

---

### Post by dzv on 2007-04-10
When it's working properly, CTRL-ALT-LeftArrow should switch workspaces, with a rotating cube effect.

And

CTRL-ALT-LeftClick should allow you to move the cube with your mouse, the same as in Beryl.

Sounds like the cube effect isn't working for you, for some reason.

---

### Post by esodin on 2007-04-10
Have you checked in Beryl settings that it's turned on?

---

### Post by Biscuitpie on 2007-04-10
I don't think it's Beryl, as I'm using the Fesity Live CD. It's built in.

---

### Post by wigglydiggly on 2007-04-10
Deisty uses compiz by default.  I had the same problem with my feisty install.  I installed compiz setting manager and GL Desktop and got it to work.  I'm still having troubles with water effect.

---

### Post by Biscuitpie on 2007-04-10
How do I download those 2?

---

### Post by Vlatko on 2007-04-20
Does the rotating cube effect, switching between workspaces, work in Compiz? I mean when you scroll the mouse wheel to switch between workspaces? It doesn't work on my Ubuntu, however when I ctrl-alt-left click I can rotate it normally, but the mouse scrolling doesn't work.

---

### Post by OmniCloud on 2007-04-20
WOW just upgraded to 7.04. Awesome stuff, the wiggly pages and rotating cube are both standard under preferences. There just turned off by default for users with older computers. But they work fine, is a bit basic compared to Beryl, but a lot more stable...

Ubuntu is the distro for me man...really impressed, but what else is new here?

---

### Post by g8m on 2007-04-20
The cube did work for me. But after a while it didn't anymore. I could't get it working with desktop effects,  but with gnome-compiz-manager I got it working again. Why is compiz installed by default but the manager not?

---

### Post by BlacKat on 2007-04-20
The cube worked the first time i turned on the settings. Then i wanted to turn off the wobly windows and the cube stopped working. It was a glorious 10 seconds :(
I tried all kinds of combinations, even reinstalling the driver...wont work :(
So...either trying compiz or beryl which are quite unstable and often dont work properly, or settleling for the wobbly bubbly crap.HELP! :(

---

### Post by dr.modding on 2007-04-20
I had the same problem and i made everrything.... maybe because its experimental.. waiting a update [-o< anyway Ubuntu 7.04  excellent!!

---

### Post by scotty2hott2k on 2007-04-20
open up gconf-editor then goto applications->compiz->general->screen 0->options then set hsize to 4

---

### Post by dr.modding on 2007-04-20
Thanks Its Alive!!!!!! :lolflag:

---

### Post by Fillibuster on 2007-04-20
> **OmniCloud said:**
> WOW just upgraded to 7.04. Awesome stuff, the wiggly pages and rotating cube are both standard under preferences. There just turned off by default for users with older computers. But they work fine, is a bit basic compared to Beryl, but a lot more stable...

Ubuntu is the distro for me man...really impressed, but what else is new here?

Is that you Omni?!?  :guitar: 

[/offtopic]

My cube wasn't working and I used the advice and went into the gconf-editor and edited that hsize and it works again.  I was under the impression that it was running Beryl, which explains why Beryl settings didn't work!  I'm going to try to install the compiz settings and see how that goes...

---

### Post by Toxic-Waste on 2007-04-20
I get a "Composite Extension not available" error... When I had the Live CD in i got a white screen also but now that I have installed Feisty Fawn it doesn't work... If i run the Sabayon Live CD Beryl work fantastic!!!
Anybody got any advice?

---

### Post by schnupi on 2007-04-24
> **scotty2hott2k said:**
> open up gconf-editor then goto applications->compiz->general->screen 0->options then set hsize to 4


you're one legend! thanks very much! ... any ideas how i can change the background when i go like ctrl alt leftmouse? ... or can i just do that with beryl?... i dont see a point installing it when i have all those features on anyways..

---

### Post by icechen1 on 2007-04-24
Well,i know the fix for the swiching workspaces in cube:
Go to terminal and do:
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
i think this way is faster

---

### Post by OmniCloud on 2007-04-25
> **Fillibuster said:**
> Is that you Omni?!?  :guitar: 

[/offtopic]

My cube wasn't working and I used the advice and went into the gconf-editor and edited that hsize and it works again.  I was under the impression that it was running Beryl, which explains why Beryl settings didn't work!  I'm going to try to install the compiz settings and see how that goes... Why yes...yes it is!!!:guitar: PSINEXT in the building BABY!

I think I'm gonna leave the cube/beryl stuff alone until it's more stable. Just trying to get Winff to work so I can put my converted Naruto on my PS3. I'm fine with the wiggly pages for now:-)

---

### Post by akshunj on 2007-05-28
Editing gconf settings will definitely get you to the dance, but installing the gnome-compiz config tool is by far the better way to go.  Gives you control over all compiz settings.  Just enable the cube and give it 4 viewports, and your cube is back.

Why isn't this installed by default in Feisty?  Big miss, in my opinion.

Also, was anyone else confused by the fact that Feisty came with compiz instead of beryl?  I could have sworn I read that beryl was built into Feisty.  But maybe they were looking for stability and not cutting-edge.  Probably a smart decision...:)

--Akshun J

---

### Post by WinterWeaver on 2007-05-28
They decided against all of that for Feisty. But still left compiz in as a kind of demo/experiment.

This is prob why they don't have the settings manager included (though it would be better if it was :P )

---

### Post by hammedhaaret on 2007-05-28
i don't think it will work while on a live cd, cause i seem to remember you need the gfx drivers installed first.

---

### Post by MailmanTX on 2007-09-21
Hey all

I was just about to post this question - I like how the forum auto searches your subject line and brings up similar topics before you post!

Anyhew... the conf edit worked fine and I gotta say I'm loving Ubuntu now! I was on the Kubuntu kick for a bit, then had to go back to windows for something and never rebooted... so I decided why not try the parent of all the buntu's and hit up Ubuntu... Everything worked "outta the box" (even imported my documents from Windows (well, not even half of what was in the my documents directory but no matter): NFTS read access without terminal mount commands, easy access to restricted repositories... anyhew... I've been emersed back in Ubuntu for three days now - don't know why I left.

---

