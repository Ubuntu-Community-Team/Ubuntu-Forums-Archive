---
title: "Omg someone please help me!!"
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by chroncile on 2007-09-23
My intel i915 is running my cedega games so slow, when I tried to install the intel linux graphics, it says a error, kernel modules did not compile, it's driving me crazy 	](*,)

```

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

Also my cedega won't start any games, how do I uninstall it, PLEASE DON'T JUST LOOK AT THIS THREAD AND NOT REPLY OMG I'M SO SAD, NO ONE HELPS ME AND I'M A NOOB :( :'(

I want to uninstall my cedega and install it again, please someone help me :(
Please also help me install the intel linux graphics :(

---

### Post by shad0w_walker on 2007-09-23
The Intel graphics drivers are open source i believe, they should be properly installed when you first installed Ubuntu. What game(s) are you trying to play, and what specs does you system have? Also bear in mind that some games simply won't work in Cedega, it's not a guaranteed thing.

P.S. You might also want to check the Cedega forums. If you payed for Cedega then they will give you help. If you didn't then I'm afraid your on your own, the forum doesn't look kindly on pirated stuff.

---

### Post by quadomatic on 2007-09-23
> **shad0w_walker said:**
> 
If you payed for Cedega then they will give you help. If you didn't then I'm afraid your on your own, the forum doesn't look kindly on pirated stuff.

Yes Indeed, piracy is not welcome here.

If you're not willing to pay for Cedega, just use WINE. Or, if you're unwilling to use either, and you have Windows, then Dual Boot.

---

### Post by ddrichardson on 2007-09-23
Uninstalling and reinstalling most liekly wont help, try launching Cedga from a terminal and you get outpu showing any problems. As for the Intel graphics -  I'm not familiar with how you are installing, are you following a guide or something? It looks like you are missing the required build stuff for kernel compilation.

Incidentily, you are likely to get more useful responses if you post a quick synopsis of the problem rather than "OMG Someone help me", many of us on the forums check a lot of new posts and will pick out the ones me knw most about first, hence a title like "Cedga Problem" will get you more of the right people for your problem.

---

### Post by jacob01 on 2007-09-23
i have an intel x3000 igp and i don't get that good of performance with it so i assume that on your 915 wont do to well either.
just use the driver from the repository that one will work just fine.

---

### Post by Ferrat on 2007-09-23
Havn't looked lately but isn't the CVS version of cedega still free? 

Besides why would cedega help with a agpgart compiling error? ect. it's a kernel problem not a cedega one?

---

### Post by chroncile on 2007-09-27
Ok so forget about cedega, but please just help me install the intel linux graphics, I only get 1200 fps in glxgears, a guy installled the intel linux graphics and said he got 3000+ fps in his glxgears, please I want to install them so badly!
Here is the website I am talking about :

[http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

---

### Post by cogadh on 2007-09-27
> **Ferrat said:**
> Havn't looked lately but isn't the CVS version of cedega still free?
Still free, but hasn't been updated in years, doesn't include the GUI and doesn't work nearly as well as the current versions of Wine, Cedega or CrossOver.

---

### Post by Ferrat on 2007-09-27
> **cogadh said:**
> Still free, but hasn't been updated in years, doesn't include the GUI and doesn't work nearly as well as the current versions of Wine, Cedega or CrossOver.

Ahh ok, only use wine so haven't kept up ^^

---

### Post by chroncile on 2007-09-27
Omg no one has helped me, you  just keep talking about cedega :(
I am going to cry :(
Please help me :(!!

---

### Post by ddrichardson on 2007-09-27
Can you start [here ]("https://help.ubuntu.com/community/i915Driver#head-ae723fd1968b04edba50253d75138b29444e1a57")and report any problems.

---

### Post by chroncile on 2007-09-28
I don't want the video drivers for regular stuff, I want it for games, the games are slow that's why I need a new one omg :(

---

### Post by cogadh on 2007-09-28
Unfortunately, the Intel i9XX drivers and chipset are not really known for their performance capabilities, in Windows or Linux. You will not be able to get any better performance than what you get from the default Intel driver that is installed with Ubuntu. In fact, on the Intel Linux driver website, it actually says "If you have a 945 or older graphics controller, your distribution will already have the right drivers included."
[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

---

### Post by chroncile on 2007-09-29
NOOOOOOOOOOOOOOOOOOOOOOOOOOOOO :(
On windows the games are so much faster, why why why!!!!!!!!!! :(

---

### Post by cogadh on 2007-09-29
The short answer is the Windows drivers were developed (and still updated?) by Intel, while the Linux drivers were created by a third party, not technically related to Intel.

If you really want to improve your gaming performance, go out and buy a new video card. In fact, it doesn't actually have to be "new", a 5th or 6th generation GeForce graphics card (GeForce FX or GeForce 6XXX) would run circles around that Intel IGP.

---

