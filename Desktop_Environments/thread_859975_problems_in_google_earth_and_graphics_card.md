---
title: "problems in google earth and graphics card"
date: 2008-07-15
forum: Desktop Environments
---

### Post by novitsky on 2008-07-15
in Gutsy:

I have an Intel on-board graphics card, my mobo is df965gf. I can't show images on-top of google-earth. I think it is something to do with 3d of the the graphics card or driver. when I upload the computer I have no screen attached and I have a display on another computer via vino vnc (remote-desktop). 

1. what should be my definitions in xorg.conf in order to upload the system whithout a screen conected
2. does my graphic card supports google earth or is it too much for it.

thanks!

---

### Post by skiwithpete on 2008-07-15
I have the same problem...  terrible refresh rates, can't put other images on the screen.  Hope this has a solution.

---

### Post by paul101 on 2008-07-15
prob a problem that can be solved by disabling compiz fusion




use the compiz fusion icon to quickly switch compiz on / off :)


(if you dont have it)
```
sudo apt-get install fusion-icon
```

[img]http://tombuntu.com/wp-content/uploads/2008/03/fusion-icon1.jpg[/img]


To start Fusion-icon whenever you log in, add it to the Startup Programs list in 

System->Preferences->Sessions.


[img]http://tombuntu.com/wp-content/uploads/2008/03/fusion-icon2.jpg[/img]

---

### Post by novitsky on 2008-07-16
no compiz on my machin - it was very bugy - couldn't add more workspaces and some more problems. I think it is something to do with the graphics driver but I'm too ignorant about this stuff. :confused:

---

### Post by stitchmysmile93 on 2008-07-17
I had problems with compiz too with adding more workstations. I had to add them with the advanced desktop effect settings tool. But it worked after awhile. And google earth I can only get working in root for some reason sudo googleearth try that...

---

### Post by stitchmysmile93 on 2008-07-17
oh paul101 thanks for that post lol I didn't know about that tool everytime I log in I have to do a metacity --replace that makes it easier...

---

### Post by novitsky on 2008-07-17
> **stitchmysmile93 said:**
> I had problems with compiz too with adding more workstations. I had to add them with the advanced desktop effect settings tool. But it worked after awhile. And google earth I can only get working in root for some reason sudo googleearth try that...

well, I can have google earth work on my user, nothing different when using sudo. I'm sure it's the graphics card - when looking in google earth --> tools --> options --> Graphics Mode, I have only "use safe mode" and not the usual OpenGL or DirectX options.

Must be the intel 965 onboard G. card.

thanks anyways!

---

### Post by stitchmysmile93 on 2008-07-17
I'm not liking google earth at the moment anyways..

---

### Post by p4cldba on 2009-01-18
i could not make it work on my ubuntu 8.10 /hp  dv6135nr laptop . thinking of  removing it soon.

---

