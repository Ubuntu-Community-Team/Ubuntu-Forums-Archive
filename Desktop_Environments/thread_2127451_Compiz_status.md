---
title: "Compiz status"
date: 2013-03-20
forum: Desktop Environments
---

### Post by nibal on 2013-03-20
I went over to Compiz's home: [http://www.compiz.org](http://www.compiz.org). The wiki doesn't work. Last post in forums was from end of September 2011, almost 2 years now. No bug reporting. Meanwhile the code is not entirely stable. It looks like in a state of abandonment.:icon_frown: 

Ubuntu is thriving, and have shown signs of integrating compiz (unity). Any plans to continue with it?

BR,
Nikos

---

### Post by VeeDubb on 2013-03-20
The current direction for Ubuntu seems to be focussing on Mir, which is going to completely replace the X server.  Several other major distros are doing the same thing, although everybody other than ubuntu plans on moving to a display server called Wayland. (not that the specifics matter to your questions)

All of these replacements for X will start with a 3D capable base, which means that the core functionality of compiz (creating a 3D compositing layer) will no longer be required or useful.  Many people will want some of the functionality and/or eye candy that compiz plugins offered, but they will have to be developed from the ground up to work on Mir/Wayland instead.

In short, compiz is stable and functional as is, and will be made obsolete over the next couple of years.  As such, there is little if any reason for people to continue working on it.

---

### Post by nibal on 2013-03-20
@VeeDubb:
> In short, compiz is stable and functional as is, and will be made obsolete over the next couple of years. As such, there is little if any reason for people to continue working on it.

I wouldn't consider it stable yet. For example creating a 4x4 workspace and using X-windows controls <Ctrl>-<Alt>-<arrows>, will work fine for left & right, but will crash Compiz on up & down.
But I see the reasoning behind what you say. Xorg seems to go that way, too.

That's good news. Integrating 3D into the main windows server, is a much stronger commitment. Thanks for the update, very useful info.

BR,
Nikos

---

### Post by VeeDubb on 2013-03-20
> **nibal said:**
> I wouldn't consider it stable yet. For example creating a 4x4 workspace and using X-windows controls <Ctrl>-<Alt>-<arrows>, will work fine for left & right, but will crash Compiz on up & down.
But I see the reasoning behind what you say. Xorg seems to go that way, too.

Compiz may not be *perfectly* stable, but the majority of functions used by the majority of people work fine.  (not many people want or need 16 desktops, and it's perfectly fine with 4, i.e. - 2x2)

Beyond that, we're in total agreement.  There's a lot of work left to be done on Mir and/or Wayland, but the X server is a dinosaur.  Building in 3D support from the ground up is just common sense if you're going to build a replacement today.  As for which replacement will be superior, time will tell.  Wayland has a big head start, but Mir is backed by canonical and there has been talk that they're working with the major gpu manufacturers to some degree on the project.  Whichever replacement comes out on top will almost certainly be a vast improvement.

---

### Post by nibal on 2013-03-20
@VeeDubb:
> Compiz may not be perfectly stable, but the majority of functions used by the majority of people work fine. (not many people want or need 16 desktops, and it's perfectly fine with 4, i.e. - 2x2)

I am not saying that I am using 16 desktops, just when testing Compiz. I didn't want Compiz crashing on me, just because it ran out of desktops to cover each face of the cube! ;-)

BR,
Nikos

---

### Post by grahammechanical on 2013-03-20
Work is still being done on Compiz. I have been running 13.04 development for almost 5 months and I have seen several updates to Compiz. It is Compiz Configuration Settings Manager that is not receiving much development work. Some of the Compiz effects have been discontinued. There is a basic reason for this, in my opinion. 

Maintenance of Compiz fell upon a single person for a while and he became very discouraged by all the negative comments made about Compiz. On top of all that buggy proprietary video drivers were making Compiz unstable. Each update to a proprietary driver would break Compiz in some way and he would have to start work all over again putting in a work-around which would be broken by the next update to the video driver. And people would complain about Compiz being no good.

We do not realize when we complain about this not working right and bugs not being fixed is that the problem is often caused by what is called Upstream code that Ubuntu developers can do little about except pass on bug reports and suggest fixes. It is up to the Upstream developers to make the corrections. And that does not always happen fast enough.

Regards.

---

### Post by nibal on 2013-03-20
> **grahammechanical said:**
> Work is still being done on Compiz. I have been running 13.04 development for almost 5 months and I have seen several updates to Compiz. It is Compiz Configuration Settings Manager that is not receiving much development work. Some of the Compiz effects have been discontinued. There is a basic reason for this, in my opinion. 

Maintenance of Compiz fell upon a single person for a while and he became very discouraged by all the negative comments made about Compiz. On top of all that buggy proprietary video drivers were making Compiz unstable. Each update to a proprietary driver would break Compiz in some way and he would have to start work all over again putting in a work-around which would be broken by the next update to the video driver. And people would complain about Compiz being no good.

We do not realize when we complain about this not working right and bugs not being fixed is that the problem is often caused by what is called Upstream code that Ubuntu developers can do little about except pass on bug reports and suggest fixes. It is up to the Upstream developers to make the corrections. And that does not always happen fast enough.

Regards.

In this forum, I have heard nothing but praises about Compiz! Ubuntu's developers' commitment to it, further atests to that. I was disappointed to see Compiz go, as evidenced by their 2 yrs almost silent forums, but also happy that 3D graphics are integrated in the new windows servers. This is another example of how compiz has influenced the market. If that is not a sign of success, I don't know what is. My comment that the down arrows would crash it, was not critical to that effect, but rather to point out a shortcoming, which in no way deters me from using it daily. 
And for that reason I visited their site.
Besides, the problem of switching desktops with the arrows, a classic X-windows control, has nothing to do with proprietary drivers, since the left and right arrows work fine, instead it was left out to hang like that.  Like leaving good work unfinished.

My 2 cents,
Nikos

---

