---
title: "[SOLVED] compiz leaves ghosts"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by markusf21 on 2007-12-09
I have found a work around for this please see my last post.
Whenever I have compiz turned on I get ghosts from password screens. If I run synaptic or update manager the box for my password pops up. I put my password in and the box goes away but the outline stays on the screen till I restart or turn off compiz. Here is a screen shot in case I did not explain it well enough. Oh and I am running gutsy.

---

### Post by smartboyathome on 2007-12-09
That's weird, it looks like what happens if you use the Bling plugin with E17... maybe there is a connection?

---

### Post by mtbsoft on 2007-12-10
> **markusf21 said:**
> Whenever I have compiz turned on I get ghosts from password screens. If I run synaptic or update manager the box for my password pops up. I put my password in and the box goes away but the outline stays on the screen till I restart or turn off compiz. Here is a screen shot in case I did not explain it well enough. Oh and I am running gutsy.
I can confirm this behaviour too.  Just upgraded to Gutsy a few days ago and have been having the same issue exactly, though hadn't realised that it was the password dialogs.  I don't use E17. 

Inspiron 9400 with ATI X1400 graphics card if that helps.

---

### Post by Ub1476 on 2007-12-10
I have ATI X1400 as well. No problem. Maybe you should try to delete your Compiz settings?

I did a clean install btw.

---

### Post by markusf21 on 2007-12-10
I don't have e17 or an ATI card. I am running Gnome. This[**_[COLOR="Navy"] Link[/COLOR]_**]("http://emachines.com/products/products.html?prod=W3619") is my computer. The only difference is a 320 GB hard drive I added.

---

### Post by mtbsoft on 2007-12-10
markusf21, did you do a clean install or an upgrade from 7.04?

Ub1476, I might try deleting the settings later after a few other things, though they should all be new as I didn't use compiz on 7.04.

I've made some room on the drive for another partition so I'll do a clean install there rather than an upgrade and see if it makes a difference, maybe it is a hang over from 7.04.

---

### Post by markusf21 on 2007-12-10
I keep /home on a drive of it's own so I always do clean installs

---

### Post by JayTee on 2007-12-11
I have an Nvidia GeForce FX 5200 PCI-E card and I'm getting the exact same thing. I've found that changing themes in Emerald makes the outline box.go away so I suspect there is a bug in the libemeraldengine0 unless someone else in this post is experiencing the problem running metacity or some other window decorator. This is a clean install of Gutsy and all updates applied as of 12/11/07.

---

### Post by markusf21 on 2007-12-13
I don't have emerald I am almost positive that I have metacity running

---

### Post by themusicwave on 2007-12-17
I am having this same issue, with a Dell Insprion E1505 with an Nvidia card.

So it's not an ATI issue.  It's been this way ever since I upgraded to Gutsy, and I have had compiz turned off for months now due to it.

It is really sad, I would love to have compiz, but this is just way too annoying to live with...

I just discovered that it is window decoration related.  I completely turned off window decoration and  the box that was haunting my screen went away.  Unfortunately so did my window decore....

How do I check which decorator I am using, I cant find the setting.

---

### Post by markusf21 on 2007-12-18
KInd of solved, I found a work around but I am not sure if it has any adverse effects. 
Alt F2 to run gconf-editor. 
Click on Apps then gksu then uncheck force-grab. 
And bye bye ghosts. I am still trying to figure out what force-grab does, so use at your own risk.

---

### Post by FuturePilot on 2007-12-19
> **markusf21 said:**
> KInd of solved, I found a work around but I am not sure if it has any adverse effects. 
Alt F2 to run gconf-editor. 
Click on Apps then gksu then uncheck force-grab. 
And bye bye ghosts. I am still trying to figure out what force-grab does, so use at your own risk.

force-grab is responsible for the fading of the screen when gksudo is invoked. It makes the password prompt the only active window. Everything else is frozen in the background. By disabling it you can basically interact with anything in the background while the password prompt is being displayed.

---

### Post by markusf21 on 2007-12-19
Oh thank you, good to know. So nothing important then.

---

### Post by themusicwave on 2007-12-26
The issue remains unsolved for me, even with force grab off the sudo window still leaves a "ghost"  any ideas?

Thanks,

Jon

---

### Post by mtbsoft on 2008-01-29
> **themusicwave said:**
> The issue remains unsolved for me, even with force grab off the sudo window still leaves a "ghost"  any ideas?

Just done a completely clean install of Gutsy and this problem is still there.  Went to look at the force-grab setting and found it already unchecked.

Has anyone reported this as a bug yet?

---

### Post by mtbsoft on 2008-02-02
I have found a workaround for this for those who still have the problem and don't get anywhere with the "force grab off" solution; this assumes you're using Custom compiz settings.

Appearance Preferences -> Visual Effects -> Preferences -> Window Decoration, set the Shadow Opacity to its minimum value (appears to be 0.0100).

This does, admittedly, make all your window shadows disappear but I can live with that as opposed to having the password box shadow there all the time.

---

### Post by Ifrgtmyname on 2008-02-26
Similar problem here; I am running an nvidea 

The ghosts are not with the passwords for me but rather with comment boxes it onl does it some of the time as well

so still unsolved for me  :(

---

### Post by distortedecho on 2008-03-05
Shadow opacity worked for me - but can the bug be fixed?

---

### Post by Royajm on 2008-03-10
I don't know if I'm repeating the above, because I'm running compiz in finnish. Well I had the same problem, until I played with some settings in compiz-fusion and noticed that when I disable something close to "windows shading" (comes right before the "motion blur" option)  I got the ghost frame to disappear. Hope this helps.

Edit: This seems to have done the trick only temporarily, now the ghost is back. It hasn't showed up the few last times after disabling the option though..

---

