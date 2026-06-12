---
title: "Enabling Desktop Composite Effects wants to install &quot;old&quot; NVIDIA driver."
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by mistman123 on 2008-01-11
Ok I HAD to create a new thread because I can't find this anywhere...

I have an HP laptop with the GeForce 8400M GS in it... after first installing Ubuntu 7.10 (Gutsy) It seemed to have the compiz working but there will still quirky effects problems where windows would stick (not just snap) and start wobbling wierdly, the screen would draw weird colored lines, the cube didn't work, and all other sorts of things... so I decided to take it off (turn the effects to "Normal" again). Then I went and downloaded the  [latest Linux Display Driver - x86 (32 bit) Version: 169.07]("http://www.nvidia.com/object/linux_display_ia32_169.07.html") and installed it successfully. All checks reveal it is actually using this driver (I haven't even wanted to use the "NoSplash" option because I actually want to see the splash screen, just to make sure that it's using the "nvidia" driver instead of the "nv", "nvidia_new", or "nvidia_legacy" everytime I reboot). If I go to the restricted drivers manager I see that the NVIDIA checkmark is off but it still says "in use" which I know is normal because it's using the newly installed driver instead of the restricted ones available from ubuntu. Now, the problem actually is that whenever I want to re-enable the composite extention (compiz) in the appearance options, it says I have to enable the restricted NVIDIA driver for this to work. I did that at first to see if it was just some kind of switch but it just installed the nvidia_new (version 100.x.x) driver over the latest (version 169.x) I had installed, and messed everything up again so I reinstalled the latest driver and find myself at the same spot now. I do have my Extension option "Composite" in "Enable" but I still get no compiz and same problem. Any help please!?!?

---

### Post by chewearn on 2008-01-11
One possible solution:

Press ALT+F2, type in:
```
compiz --replace
```

If this works, add it into your Sessions > Startup Programs

---

### Post by mistman123 on 2008-01-15
Thanks! Worked perfectly... Wouldn't that just work for my session though? Is there a way to have it load automatically for every session?

---

### Post by chewearn on 2008-01-15
> **mistman123 said:**
> Thanks! Worked perfectly... Wouldn't that just work for my session though? Is there a way to have it load automatically for every session?

Add the command into your start-up list, as mentioned in my post #2 (its function is similar to Windows Start-up sub-menu).

---

### Post by Raincheque on 2008-01-15
So I have never done this before, but here is what I'm having a problem with:
I go to System>preferences> appearance> visual effects and try to change it to custom and I get a message that reads Desktop effects can not be enabled. I actually can't change it to anything other than 'none'.
Is this a simple oversight on my part? How can I fix it?

---

### Post by chewearn on 2008-01-15
> **Raincheque said:**
> So I have never done this before, but here is what I'm having a problem with:
I go to System>preferences> appearance> visual effects and try to change it to custom and I get a message that reads Desktop effects can not be enabled. I actually can't change it to anything other than 'none'.
Is this a simple oversight on my part? How can I fix it?

What graphics card do you have?

---

### Post by mistman123 on 2008-01-17
> **Raincheque said:**
> So I have never done this before, but here is what I'm having a problem with:
I go to System>preferences> appearance> visual effects and try to change it to custom and I get a message that reads Desktop effects can not be enabled. I actually can't change it to anything other than 'none'.
Is this a simple oversight on my part? How can I fix it?
You probably don't have the xserver package installed. Go to the Synaptics Manager and search for xserver and install it.

---

### Post by mistman123 on 2008-01-17
> **AstalaVista said:**
> Add the command into your start-up list, as mentioned in my post #2 (its function is similar to Windows Start-up sub-menu).
Yes I had done that and whenever I log in the compiz loads and it works perfect. What I meant was: If I make another account (with a different username) for someone else, would I have to go to "their" start-up list? Or would adding the command on mine suffice for all other sessions?

---

