---
title: "Age-old &quot;Adobe black-box Flash&quot; prob, with a twist"
date: 2012-06-07
forum: Desktop Environments
---

### Post by SketchMan3 on 2012-06-07
So, I just installed Ubuntu 10.04. Using Firefox. Flash doesn't work. All it shows is a black box. 

Not even Youtube vids are working. 

Flash-Aid didn't fix it, with either beta or stable, enabled GPU validation or Disabled GPU validation.

Tried installing from Synaptic, Adobe.com, Software Center. Nothing.

I copied my extensions, bookmarks, etc., to my new profile from my old one. I removed all add-ons that could I think could conflict, namely Ad Block Plus, which had caused problems for me on system I'd been running before...

I'd been running from a persistent 10.10 Live USB for about a year, the USB started to die, so I switched to a hard drive. I was advised to use 10.04 since 10.10 is end-of-life, and no longer supported.

Flash worked on the 10.10 Live USB, which had an older version of Firefox.

Can somebody help me?

---

### Post by wilee-nilee on 2012-06-08
> **SketchMan3 said:**
> So, I just installed Ubuntu 10.04. Using Firefox. Flash doesn't work. All it shows is a black box. 

Not even Youtube vids are working. 

Flash-Aid didn't fix it, with either beta or stable, enabled GPU validation or Disabled GPU validation.

Tried installing from Synaptic, Adobe.com, Software Center. Nothing.

I copied my extensions, bookmarks, etc., to my new profile from my old one. I removed all add-ons that could I think could conflict, namely Ad Block Plus, which had caused problems for me on system I'd been running before...

I'd been running from a persistent 10.10 Live USB for about a year, the USB started to die, so I switched to a hard drive. I was advised to use 10.04 since 10.10 is end-of-life, and no longer supported.

Flash worked on the 10.10 Live USB, which had an older version of Firefox.

Can somebody help me?

Is it the flash in chrome, it has its own built in.

---

### Post by SketchMan3 on 2012-06-08
> **wilee-nilee said:**
> Is it the flash in chrome, it has its own built in.
I don't get what you mean. I've seen the word "chrome" thrown around, but I always thought it was Google Chrome, lol.

---

### Post by wilee-nilee on 2012-06-08
> **SketchMan3 said:**
> I don't get what you mean. I've seen the word "chrome" thrown around, but I always thought it was Google Chrome, lol.

I figured you could extrapolate flash and chrome together means google chrome.

Am I being to generous with my assumption of your cognitive reasoning. :)

---

### Post by vasa1 on 2012-06-08
> **wilee-nilee said:**
> Is it the flash in chrome, it has its own built in.

The first line in the first post indicates OP was referring to **Firefox**.

---

### Post by SketchMan3 on 2012-06-08
Yes, yes you are.

I recently found out that Firefox has a feature called chrome that has something to do with the way it looks, so you confused me a bit.

Are you implying that my only solution is to use google chrome instead of Firefox? I don't like that... =(

I really hope there is a way to actually fix this problem... maybe I should have just installed 10.10 and used a dead version of ubuntu...

---

### Post by vasa1 on 2012-06-08
> **SketchMan3 said:**
> Yes, yes you are.

I recently found out that Firefox has a feature called chrome that has something to do with the way it looks, so you confused me a bit.

Are you implying that my only solution is to use google chrome instead of Firefox? I don't like that... =(

I really hope there is a way to actually fix this problem... maybe I should have just installed 10.10 and used a dead version of ubuntu...
You are correct. Depending on the context, chrome can mean different things. There's Chrome, the browser. There's also "chrome" in the context of any graphical browser and here chrome refers to elements of the user interface and not to the contents of the web page.

---

### Post by wilee-nilee on 2012-06-08
> **vasa1 said:**
> The first line in the first post indicates OP was referring to **Firefox**.

Yes but many are not aware of chromes built in flash, and have troubles.

It is a fair question, to cover all the bases rather then to assume.

---

### Post by wilee-nilee on 2012-06-08
> **SketchMan3 said:**
> Yes, yes you are.

I recently found out that Firefox has a feature called chrome that has something to do with the way it looks, so you confused me a bit.

Are you implying that my only solution is to use google chrome instead of Firefox? I don't like that... =(

I really hope there is a way to actually fix this problem... maybe I should have just installed 10.10 and used a dead version of ubuntu...

I am not implying anything that is a projection on your own part, I was merely trying to get all the facts,  like Joe Friday.

Personally I don't like [COLOR=Red]GOOGLE[/COLOR] chrome I never use it.

---

### Post by SketchMan3 on 2012-06-08
Ok, thank you. 

Well, if anybody can think of any possible helpful tips, feel free to chime in.

PS: I'm using Google Chrome now. Hopefully not permanently. It's pretty great to be able watch videos in full screen (AT ALL) PlUS with no scan lines or frame rate drops, though.

---

### Post by mrmo64 on 2012-06-13
Hello try this:
Download this file [http://help.jolicloud.com/attachments/token/cnfn3zj6fguv1pa/?name=flashplugin-installer_11.2.202.236ubuntu0.10.04.1_i386.debwnload](http://help.jolicloud.com/attachments/token/cnfn3zj6fguv1pa/?name=flashplugin-installer_11.2.202.236ubuntu0.10.04.1_i386.debwnload) 

and this one

[http://help.jolicloud.com/attac:](http://help.jolicloud.com/attac:) sudo dpkg -i flashplugin-*hments/token/qcn4awxkyxleyjs/?name=flashplugin-nonfree_11.2.202.236ubuntu0.10.04.1_i386.deb

Make sure they are saved in Downloads

Then open the terminal (Ctrl+Alt+T)

Type cd Downloads
Then type:
 sudo dpkg -i flashplugin-*
Enter system password and the Flash plugin will be installed
Close terminal and reboot

---

### Post by SketchMan3 on 2012-06-19
> **mrmo64 said:**
> Hello try this:
Download this file [http://help.jolicloud.com/attachments/token/cnfn3zj6fguv1pa/?name=flashplugin-installer_11.2.202.236ubuntu0.10.04.1_i386.debwnload](http://help.jolicloud.com/attachments/token/cnfn3zj6fguv1pa/?name=flashplugin-installer_11.2.202.236ubuntu0.10.04.1_i386.debwnload) 

and this one

[http://help.jolicloud.com/attac:](http://help.jolicloud.com/attac:) sudo dpkg -i flashplugin-*hments/token/qcn4awxkyxleyjs/?name=flashplugin-nonfree_11.2.202.236ubuntu0.10.04.1_i386.deb

Make sure they are saved in Downloads

Then open the terminal (Ctrl+Alt+T)

Type cd Downloads
Then type:
 sudo dpkg -i flashplugin-*
Enter system password and the Flash plugin will be installed
Close terminal and reboot
OH! A helpful response. =D

Your second link confuses me, though. I don't know what to do with it. It seems to be broken (there's a space in there)

Edit: Also, my problem isn't with Google Chrome. It's with Mozilla Firefox.

---

### Post by dryfire on 2012-07-23
Hello,

I am running 12-4 from a 4Gb usb "stick". No hard drive. Works well.
I would like to add Adobe Flash and Goggle Chrome to the stick, so I don't have to download them after every re-boot. I have other computers to do this.

Jim

---

