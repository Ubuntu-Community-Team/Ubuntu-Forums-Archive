---
title: "ZSNES gamepad diagonals problem"
date: 2009-08-18
forum: Gaming &amp; Leisure
---

### Post by holamyburrito on 2009-08-18
Hey all,

I'm trying to set up a little ZSNES action for my eeepc900 for when I'm not home. I'm trying to use a Logitech cordless rumble pad but I have this weird problem with the directional buttons.

When I press any diagonal, say Down-Right, and then roll to either Down or Right on it's own, the game still registers it as a diagonal until I lift up. I first noticed it when playing Chrono Trigger because if you try to run in one direction and then nudge left or right, the character continues in diagonal until you release the button altogether. 

I searched through the ZSNES forums but I only found one person who also had this problem (see [http://board.zsnes.com/phpBB2/viewtopic.php?t=13034](http://board.zsnes.com/phpBB2/viewtopic.php?t=13034)). As you can see, he solved the problem by running the windows version in Wine. I tried this, and for some reason, it runs very slowly, and I think that with the slower CPU this won't work. 

Now this problem doesn't happen when the keyboard is used, only when using the gamepad. Does anyone know how to solve this or a way to permanently map the directional axes to the arrow keys (as in, not have to run any other utilities before opening ZSNES)?

Thanks a lot in advance.

---

### Post by Nevon on 2009-08-18
I've got the same problem with my gamepad. To run to the left or right, you have to press EXACTLY left or right. And if you want to move directions and go down or up instead, you have to let go of the control pad and then press either up or down - you can't just roll your thumb. 

I'll be checking this thread to see if you get an answer. I sure hope so, as I'm hoping to put together a Linux powered media-/gaming centre once I move into my new apartment.

---

### Post by holamyburrito on 2009-08-18
Ah, solidarity. I'm glad I'm not the only one with this problem. I hope that doesn't mean it's unsolveable. >_>

---

### Post by Wolf-Jakob Gratz on 2009-11-16
Bump.

I also encountered this problem. This bug is really annoying with a lot of games, esp. RPGs like Earthbound. :( Using Wine may be an (ugly) workaround for many people, but this method would be way too slow on my notebook.

Another possible workaround would be a system-wide key mapping driver for gamepads. Is this possible?

Still hoping though that this will be fixed in ZSNES.

---

### Post by Wolf-Jakob Gratz on 2009-11-16
I found a patch here: [http://board.zsnes.com/phpBB2/viewtopic.php?t=12544&sid=a7bed4f92c9afbbe7426d847f19ad54e](http://board.zsnes.com/phpBB2/viewtopic.php?t=12544&sid=a7bed4f92c9afbbe7426d847f19ad54e)

I wasn't exactly sure on how to apply it to the source, though.

But I thought of another, easier workaround:
This will only work, however, if your gamepad has an ANALOG stick and a button that switches between DIGITAL and ANALOG:
When setting up the keys in Zsnes, set the SNES direction keys to your analog stick. Now you can just switch the controls on your gamepad and ... enjoy :)

Still just a workaround, I know, but less painful than using Wine. Now, would anyone dare to apply the aforementioned patch and build it from source? Please, report results!

---

### Post by bluerabbit4210 on 2010-03-02
Not to bump a dead thread or anything, but I stumbled across this PPA with 32 and 64 bit builds of zsnes with the above mentioned patch applied. (It totally fixed my diagonals issue) Hopefully this helps anyone who stumbles across this thread (like I did) while googling for answers.

zsnes ppa:
[https://launchpad.net/~smaxein/+archive/ppa/+packages]("https://launchpad.net/%7Esmaxein/+archive/ppa/+packages")

---

### Post by Slantzalot on 2010-03-02
I know I'm a bit off topic with this, but where do you guys get these emulators? I'm new to Ubuntu and I'm not sure which applications I can trust.

---

### Post by Nevon on 2010-03-03
> **Slantzalot said:**
> I know I'm a bit off topic with this, but where do you guys get these emulators? I'm new to Ubuntu and I'm not sure which applications I can trust.

Most emulators are pretty well known. If they're in the Ubuntu repositories, they're generally safe to use.

---

### Post by Medo42 on 2010-06-09
I updated the ppa with packages for Lucid and added another patch (improved OpenGL performance when drawing scanlines) - Probably not very important but I wanted to add *something* while I'm repackaging already :P

Edit: The package is still waiting for build at the moment, you can download it in an hour or so.

---

### Post by zer010 on 2010-08-13
Personally, I am having trouble assigning diagonals to my gamepad. It is a Game Elements Recoil; GGE908. I am of course using ZSNES.  I tried to set diagonals on the d-pad, which I'd prefer for Street Fighter, then tried to set them to the analog sticks. Either way, all I'm able to map is left/right and up/down, NO diagonal! Any thoughts?

---

### Post by dfreer on 2010-08-13
> **zer010 said:**
> Personally, I am having trouble assigning diagonals to my gamepad. It is a Game Elements Recoil; GGE908. I am of course using ZSNES.  I tried to set diagonals on the d-pad, which I'd prefer for Street Fighter, then tried to set them to the analog sticks. Either way, all I'm able to map is left/right and up/down, NO diagonal! Any thoughts?

Do you really need to assign the diagonals directly? I believe the option is in there solely for Keyboard users, if you have a game pad you should be able simply press, say left + down, and it should move diagonally. Have you given it a try just using the up+down+left+right?

---

### Post by zer010 on 2010-08-13
Yes, I tried using that option. When I experienced this problem, I had  just gotten Street Fighter II Turbo.  I couldn't get any of the special  moves to work. As you know, SF without a Hadokken is NOT SF! :(
Probably just a crappy gamepad....
*but then again, i just played a little Earthworm Jim and I was able to shoot diagonally! Any suggestions for a good "diagonal test game"?

---

### Post by tacitdynamite on 2010-09-22
I have this issue as well on my Logitech RumblePad 2 USB running Zsnes 1.51 on Ubuntu 10.10 Maverick Meerkat. Any chance you can put up Meerkat in the PPA?

I've noticed that [other people have already talked about this issue]("http://www.uluga.ubuntuforums.org/showthread.php?t=1140723") on the forum, but for them the problem was deeper than zsnes; maybe worth a look.

---

### Post by Medo42 on 2011-01-28
Sorry for taking this long, but I have a new version for Maverick in the ppa.

> I've noticed that other people have already talked about this issue on the forum, but for them the problem was deeper than zsnes; maybe worth a look.

If you look at the patch that fixes this in zsnes, it seems to be a stupid mistake in handling this kind of input, rather than a deeper bug.

---

### Post by phormicola on 2011-07-11
> **Medo42 said:**
> I updated the ppa with packages for Lucid and added another patch (improved OpenGL performance when drawing scanlines) - Probably not very important but I wanted to add *something* while I'm repackaging already :P

Edit: The package is still waiting for build at the moment, you can download it in an hour or so.

I am trying to install the i386 deb package now, but.....its telling me that there are unmet dependencies.

I installed ZSNES using synaptic before and it installed just fine.....anyone got any idea what the problem might be and how I can fix it?

super frustrated help appreciated :)

---

### Post by Medo42 on 2011-07-12
Hi. I don't actively maintain this PPA so this doesn't come as a big surprise, but I can take a look later this week.

Edit: I pulled the latest package source from debian and I'm currently trying to get everything to build/work. However, I didn't have a problem installing the maverick package in natty/32-bit. What exactly is the error message?

---

### Post by Medo42 on 2011-07-13
I'm making progress, on the third attempt only the amd64 build failed, so there is now a natty i386 build available. I'll try to see if I can get the amd64 build working, too.

Edit: There is a build for both i386 and amd64 now, after six attempts :D. Please try it out and reply if you have any problems.

---

### Post by Sahasrahla on 2011-07-19
> **bluerabbit4210 said:**
> Not to bump a dead thread or anything, but I stumbled across this PPA with 32 and 64 bit builds of zsnes with the above mentioned patch applied. (It totally fixed my diagonals issue) Hopefully this helps anyone who stumbles across this thread (like I did) while googling for answers.

zsnes ppa:
[https://launchpad.net/~smaxein/+archive/ppa/+packages]("https://launchpad.net/%7Esmaxein/+archive/ppa/+packages")

Could anybody help me with how to apply this?

---

### Post by Medo42 on 2011-07-19
Installing packages from the PPA is described on its main page: [https://launchpad.net/~smaxein/+archive/ppa](https://launchpad.net/~smaxein/+archive/ppa)
Look under "Adding this PPA to your system".

---

