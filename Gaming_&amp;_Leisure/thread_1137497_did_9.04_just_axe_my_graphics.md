---
title: "did 9.04 just axe my graphics?"
date: 2009-04-25
forum: Gaming &amp; Leisure
---

### Post by maheshjr2000 on 2009-04-25
Whats up hombres!

Intel 945gm: mesa 1.4 
Urban Terror is running REALLY slow after a fresh install of 9.04. Much slower than it did in 8.10.
Im getting about 200 fps in glxgears.

I realize my GFX card SUCKS but it doesnt suck THIS much.

Oh and my lshw says that display is unclaimed.

---

### Post by maheshjr2000 on 2009-04-25
Using glide-init.exe in wine just froze my computer after I pressed query opengl info. I am getting 10fps at 640 by 480 in UT.

---

### Post by 5nak3 on 2009-04-25
If I am not mistaken there is a problem with the intel graphics card and Jaunty. I believe it was in the release notes of the upgrade. And I am under the impression that the forums have been awash with people stating to read the notes. The fact that this has been documented I have kept away from jaunty on my intel based PC. However, I also think my ATI chip took a hit after the jaunty upgrade UT seems sluggish....

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

About three quarters of the way down the page it should explain the problem I think.

---

### Post by maheshjr2000 on 2009-04-25
Edit: IGNORE THIS REPLY apparently I cant read English. 

Im going to try downgrading and see if it fixes. Peace out hombres!

---

### Post by 5nak3 on 2009-04-25
When you say downgrade, i hope you don't mean by removing packages?!

As far as I am aware there is no safe way to downgrade without a clean install, or have I misunderstood something?

Back everything up that is of use first, and then do what you have to do. Let us know how things go!

---

### Post by maheshjr2000 on 2009-04-25
Thanks but it's not necessary. Im a newb but not that much of a newb. Im just going to revert the driver for my gfx card to the 2.4. Everything else in 9.04 wont be touched. My important files are on paper or my Gdrive.

---

### Post by maheshjr2000 on 2009-04-25
Well that fixed it...for about a second. As soon as I hit the action it breaks again. 7 fps.

---

### Post by 5nak3 on 2009-04-26
i have the same card as you in my other pc try these settings:

800x640 (sucks but what can you do)
Normal textures
Bilinear filter
Desktop default as opposed to 16bit or 32bit (for whatever options require this, cant remember them)
Maybe also turn off the dynamic lighting of the gun
And put compress textures to yes

That may help, if not all i can really recommend if go back to 8.04 or 8.10

---

### Post by maheshjr2000 on 2009-04-26
I tried it on both 800by600 and 640by480. Everything else is the same as you. Oh and texture compression would actually decrease performance. This isnt a memory issue.

---

### Post by 5nak3 on 2009-04-26
i just recommended the compress textures since Urabanterror.net also recommends this as it has been used to speed up the fps for some players.

Honestly, if you are still not getting speeds on the card, maybe you should go with an older version of ubuntu, they will still be supported for some time to come (go for 8.04, probably best bet as it is LTS)

Personally i haven't had a chance to give UT a real run on my ATI card with Jaunty but before in Intrepid I had stable fps of about 25-35. On smaller maps this went up to 35-45fps.

Also as a side not, what other programs are you running in the background, and / or what server are you playing on, and also is compiz enabled?

I found that more programs slower game (obviously), but more surprisingly, one server in particular i get about 10fps if i am lucky. Swap servers, same map, same amount of people and i get about 25-30fps. That could also be the problem maybe...

---

### Post by maheshjr2000 on 2009-04-26
Ive tried many servers, all modes, no programs, none special effects, and Im just going to wait till a patch comes out for it.(depending of course if they are working on it XD).

---

### Post by 5nak3 on 2009-04-26
ok well hope things get sorted. In the mean time, maybe keep this toward the top of the forum see if anyone else has any ideas on how to solve it. I'm assuming over the coming few weeks the mass of bugs associated with jaunty are going to be looked into and maybe something gets solved.

Sorry I couldn't be of much more help

---

### Post by maheshjr2000 on 2009-04-26
Dont worry about it, you were plenty of help actually! Id have spent all day on google looking for why this was happening. You linked me to the release notes. Atleast I know HOW its broken if not how to fix it XD.

---

### Post by Orlsend on 2009-04-26
I also have the same Issue with Jaunty. No Compiz and UT has about 750 MB or ram to use (So its not ram).

---

### Post by 71CH on 2009-05-04
Any updates on this?  Anybody know if a fix or update is being worked on?

---

