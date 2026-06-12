---
title: "Problem with Beryl in Feisty."
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by Bundai on 2007-04-20
Okay, well first I reinstalled beryl manager and emerald things but I cant see my top bar in my browser or in any window (I mean that where are minimize, maximize, exit). Then first the cube thing doesn't work I changed to compiz window manager and its a bit more stable but it haven't got the cube.

I was wondering how to get beryl working (including the cube and so I could see my top bar in browsers again). Ive pretty much tried everything (searched for those guides and tried to do what they said but no luck so far).

Edit: But I think Feisty is great, got my videos working! Before today my videos were really messed up, but now all formats and stuff works great!

---

### Post by DJ_Peng on 2007-04-20
This may not fix your error but I had the same problem when I upgraded to Feisty (and fixed my Nvidia drivers). You don't say what kind of video card you're running, but after making sure the Emerald window decorator was running I double checked the Beryl install page and saw that the upgrade removed some lines from my xorg.conf. You may need to make sure the following is in there> Option  	"AddARGBGLXVisuals" "True"

---

### Post by Bundai on 2007-04-20
Ok I will try that out. I have geforce 7950gt. 
Hmm I'm quite new to ubuntu so please give me accurate codes what I should type in to the terminal.

Edit: But I forgot to mention, everything works perfect when I uninstall beryl and stuff, but then I miss the cube, which I really liked.

---

### Post by Grout58 on 2007-04-20
When loading emerald try it like this "emerald --replace"

---

### Post by Bundai on 2007-04-20
> **DJ_Peng said:**
> This may not fix your error but I had the same problem when I upgraded to Feisty (and fixed my Nvidia drivers). You don't say what kind of video card you're running, but after making sure the Emerald window decorator was running I double checked the Beryl install page and saw that the upgrade removed some lines from my xorg.conf. You may need to make sure the following is in there

Okay I checked, that line exists in my xorg.conf file. Any other suggestions?

Edit: Ah I tried something what I saw in other thread: I typed glxinfo | grep -i direct into terminal and it says Direct rendering: No. And I think it should be yes, not sure if its because I use compiz windows manager thing in beryl because its a bit more stable at the moment. So how do I enable direct rendering or is that the problem at all?

---

### Post by Bundai on 2007-04-20
Okay I actually got it to work someway with the compiz manager thing, atleast now I can see that top bar in my browsers, but now I still dont have the cube. So the problem appears to be in beryl window manager... 
Correct me if I'm out of my league here, I'm still so new with ubuntu. :)

Edit: So to be clear, my goal is to get beryl window manager working so I can use the cube thing once again.

---

### Post by DJ_Peng on 2007-04-20
Sound good. You may also wantot check over at the [Beryl](http://www.beryl-project.org/) site to see if they have anything that we missed.

---

### Post by the.allstar on 2007-04-27
> **Bundai said:**
> Okay I actually got it to work someway with the compiz manager thing, atleast now I can see that top bar in my browsers, but now I still dont have the cube. So the problem appears to be in beryl window manager... 
Correct me if I'm out of my league here, I'm still so new with ubuntu. :)

Edit: So to be clear, my goal is to get beryl window manager working so I can use the cube thing once again.

How did you get your title bars to show up again?  Ok some background first: I just installed Feisty last w/e and decided to try out the Desktop Effects.  They are pretty neat, but they took all my title bars away.  I'm not sure this is the right thread to post on (I don't recall installing Beryl separately after I upgraded) but my issue sounds identical to whats been posted here.

Forgot to mention that I'm running with an nVidia card and I think I have the latest drivers.  In addition to losing all my title bars when I run Desktop Effects, I also just get a blank (white) terminal window.

---

### Post by le_mulot on 2007-05-02
ANSWER:
You should set DEFAULT DEPTH at 24 in xorg.conf

It's incredible what king of weird bugs you get everywhere when you set 16 instead of 24...

---

