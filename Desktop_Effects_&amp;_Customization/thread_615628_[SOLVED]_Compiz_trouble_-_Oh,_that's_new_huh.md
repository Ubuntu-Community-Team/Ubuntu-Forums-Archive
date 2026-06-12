---
title: "[SOLVED] Compiz trouble - Oh, that's new huh?"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by Motorhead Kaze on 2007-11-17
Okay, I'm at a loss.

When I upgraded to Gutsy, I installed Compiz, ticked off all the right boxes, according to a buddy who has all his "Cube juju" going well.  I got the settings manager and Emerald and set up everything (I thought) and only the wobbly windows and things like "Super+Tab" would work.  So then I did  sudo gedit /etc/X11/xorg.conf , made sure I had 

Option "AddARGBGLXVisuals" "true" and added 
Option "AddARGBVisuals" "true"  below it.

Then, I went out and got the Compiz Fusion Icon 
git-clone git://anongit.opencompositing.org/users/crdlb/fusion-icon
cd fusion-icon
sudo make install

then restarted Gnome.  Ok, so the cube appeared and I played with that and had a good ol' time.  Then, I tried to install the 3D and screensaver plugins from this webpage:  [http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)
But upon a restart of Gnome, not only didn't the cube work, nothing in Emerald worked at all.  My title bars were gone, and reloading the window manager did nothing to bring them back.  Also, in that state, Alt+F2 didn't work.  I couldn't close navigator windows or anything.  I restarted gnome to get Metacity back.

So, I really don't know what's going on here, feeling on the one hand like I should have been happy with the cube when it worked, but on the other hand wondering why all these things work for my friend but not for me.

Any good words on where to go from here?

---

### Post by gn2 on 2007-11-17
> **Motorhead Kaze said:**
> 

Any good words on where to go from here?

Linux Mint ?

---

### Post by Motorhead Kaze on 2007-11-17
Is my computer's breath noticeably THAT BAD?!  (hoho)

No, sorry, I'll Google that because I don't know what it is.

---

### Post by DutyDuty on 2007-11-17
As far as title bars are concerned, ```
emerald --replace
``` and ```
compiz --replace &
``` should do the trick. 

Again, the plugins in that thread are unstable. There is a warning.

---

### Post by Motorhead Kaze on 2007-11-17
Yes.  Sorry, I wasn't clear about that...I got my title bars back via the compiz fusion icon/select window manager/metacity  but that doesn't give me title bars in COMPIZ nor help compiz to work correctly.

What I'm looking for is how to make Compiz work.

---

### Post by overdrank on 2007-11-17
> **Motorhead Kaze said:**
> Yes.  Sorry, I wasn't clear about that...I got my title bars back via the compiz fusion icon/select window manager/metacity  but that doesn't give me title bars in COMPIZ nor help compiz to work correctly.

What I'm looking for is how to make Compiz work.

Hi uninstall all the compiz you have install and install from synaptic. Why are you using tar when you can get if from synaptic manager?

---

### Post by Motorhead Kaze on 2007-11-17
Hello.  Well, I tried using the tar files because, when I first upgraded to Gutsy, I used synaptic to get Compiz and Emerald and only Emerald appeared to be working, but Compiz was only putting out very minimal effects (shift+tab, and alt tab)

Because Synaptic didn't appear to give me what I wanted I went through some forum posts, websites, yadda yadda and like I said above, messed with enough things that for about 30 min. I had the cube and all that.  But trying for the 3D look, I tried to get that going through the terminal (the same process my pal got working fine) but somehow Compiz went out or Emerald did, and I ended up with none of it working.

So...I just now went back to Synaptic, completely removed Compiz and Emerald, installed them again, and still, nothing related to either is working.  

Actually?  I don't care about the cube.  It doesn't help me in anyway in my computing.  I just don't like things that work for everyone but I can't get to work right.  Just a challenge.  Still, I would like to know why it isn't working when I follow directions well.

:confused:

---

### Post by DutyDuty on 2007-11-17
Could you tell a bit more about what isn't working? What are your current settings for said problems? Are you in Compiz or Metacity? Are your accelerated graphics on?

---

### Post by Motorhead Kaze on 2007-11-17
Currently?  Nothing related to Emerald or Compiz is working.  Well ok, the compiz fusion icon works to bring me back to Metacity from Compiz.  

But when I say "Nothing" I mean that when in Compiz, there are no effects at all.  No title bar, no cube, no hotkey functions for compiz related fx, and no wobbly windows.  When in Metacity, everything is standard, no troubles.

I don't know if my accelerated graphics are on.  I haven't turned them on, and don't know what they are.  

In the compiz manager, I have many things selected.  Cube, rotation, water, all sorts of things.  They didn't work, then I did the changes listed above, and compiz was super.  Then I installed 2 plugins, and compiz stopped working.  I removed the plugins and still, anything compiz or emerald is down. 

I hope that is useful,  because that is all the information I have.

---

### Post by Motorhead Kaze on 2007-11-17
Compiz wasn't the only trouble, upgrading to Gutsy tweeked my Ubuntu world so....Finally what I ended up doing was reformating my system with a fresh copy of Gutsy.  Compiz from the repos did NOT work even with my Nvidia tweeks. By following this particular method: [http://ubuntuforums.org/showthread.php?t=626666](http://ubuntuforums.org/showthread.php?t=626666)  I got Compiz working.  I would still like to know WHY, specifically, this method worked and others didn't.  But for now, "It works" is ok.

---

### Post by gn2 on 2007-11-18
Linux Mint is a very polished distro that is based on Ubuntu.

It's well worth trying. [http://linuxmint.com/](http://linuxmint.com/)

You could try removing everything Compiz related by searching Synaptic for Compiz and Emerald and mark them all for removal.
Then manually install Beryl and Emerald after downloading them from here:
[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

---

### Post by Motorhead Kaze on 2007-11-18
Linux Mint huh?  I may try it on my laptop, since it's still got XP on it.  Thanks.

About Compiz:

So!  Since getting Compiz Fusion from Synaptic didn't work for ME, I removed Compiz, Compiz Fusion and Emerald with Synaptic.  THEN, I went through the Phorolinux install tutorial on this page:  [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)

I followed those directions, then, went to Alt+F2, entered "compiz --replace gconf".  Then in the Compiz Fusion Icon Button, under "Select Window Manager" I chose COMPIZ over Metacity and POOF! have cube, window decoration, water, and all sorts of silly shite.  

Just ***WHY*** fetching Compiz from synaptic didn't work and this did?  I dunno.  I suppose we could mark this Solved but my curiosity is still unsatisfied.  
Perhaps I need to know a whole lot more about computers than I do to understand the "Why".

Thanks anyway for all your comments.:)

---

