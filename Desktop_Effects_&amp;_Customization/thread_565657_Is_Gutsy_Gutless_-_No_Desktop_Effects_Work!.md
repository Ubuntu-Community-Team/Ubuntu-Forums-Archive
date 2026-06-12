---
title: "Is Gutsy Gutless - No Desktop Effects Work!"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by scwinn on 2007-10-02
With Gutsy only two weeks away, I decided to sneak a peak at the latest beta. But I was unimpressed. When I went to the control panel and looked at the desktop effects settings the standard desktop effects settings were enabled. BUT there were no wobbly windows and I could not drag any windows from one work surface to another. So in essence although "standard desktop effects" was set on, there were none. I had at least some of these with Feisty. (Gosh I like Feisty!!)

I am using an NVIDIA MX400 video card (a little dated but excellent 2d video.. with 3D thrown in as an afterthought (LOL))

I am using a recent Samsung 19 inch monitor.

I have an AMD 2800 CPU.

Got any ideas??:popcorn:

---

### Post by FuturePilot on 2007-10-02
How much on board video RAM does it have?

---

### Post by greenstar on 2007-10-02
There's a huge difference between an AMD Athlon XP 2800+ and an AMD Athlon 64 2800+. The Athlon XP will struggle mightily to do desktop compositing, while the Athlon 64 will handle it decently, though it will not be a stellar performer either. 

I'll make a guess that you're probably using an Athlon XP, as that would be contemporary with a GeForce MX400.

You may get desktop compositing to work, but based on my experience & IMHO, the desktop effects you're after really need faster hardware to render smoothly, and 64 bit hardware to really shine.

Greenstar

---

### Post by lincolnlad on 2007-10-02
Wobbly windows are in the 'extra effects' setting. On the 'normal' setting, you just get stuff like transparent windows. Don't know about multiple desktops as I don't use them.

---

### Post by scwinn on 2007-10-02
I have a few questions.

1 - If all I want is wobbly windows and the spinning 3d desktop that I use now will extra effects give that to me? Where do I find "ectra effects"???

2 - I looke at Linux Mint and played with Beryl and most things worked. Why dont they in Gutsy?

3 - If I change my graphics card to a new one, will that help?

As suspected I have an AMD 2800 XP (not 54) and 1.5 gigs of RAM.

Thanks for the help.:)

---

### Post by lincolnlad on 2007-10-03
You need to install the compizconfigsettingsmanager package if you want to actually tweak any desktop settings.  There's a gnomepackage, too, called gnomecompizmanager that has a more basic set of preferences you can change.  I'm not sure how compatabile either package is with the latest compiz packages in ubuntu though.

---

### Post by FuturePilot on 2007-10-03
> **scwinn said:**
> I have a few questions.

1 - If all I want is wobbly windows and the spinning 3d desktop that I use now will extra effects give that to me? Where do I find "ectra effects"???

2 - I looke at Linux Mint and played with Beryl and most things worked. Why dont they in Gutsy?

3 - If I change my graphics card to a new one, will that help?

As suspected I have an AMD 2800 XP (not 54) and 1.5 gigs of RAM.

Thanks for the help.:)
Try running```
compiz --replace
``` from the terminal and post what it says.

---

### Post by Armadillo Kilr on 2007-10-03
so with all these requirement specs flying around this thread, does this mean that the whole "being able to run on older hardware" rep is dissolved with gutsy?

---

### Post by greenstar on 2007-10-03
> **Armadillo Kilr said:**
> so with all these requirement specs flying around this thread, does this mean that the whole "being able to run on older hardware" rep is dissolved with gutsy?

Absolutely not. We're simply talking about the specs needed for "Desktop Effects"; aka. desktop compositing; aka. Compiz-fusion (formerly Beryl/Compiz)

Ubuntu (and Xubuntu especially) still do fine on older hardware. Hardware with specs less than those discussed in this thread likely will not be able to run "Desktop Effects" or most things that require 3D capable hardware.

Be assured that Ubuntu (AFAIK) will continue supporting older hardware.

Greenstar

---

### Post by scwinn on 2007-10-06
But I just do NOT get it. Feisty had a very simple desktop effect option. It allowed wobbly windows and spoun the desktop around 3D style to give me access to different work surfaces. Is there any very simple way to do this again? Why would UBUNTU developers tamper with something that worked so easily and elegantly?

---

### Post by Flyingjester on 2007-10-06
preferences -> appearance -> visual effects tab -> select extra

---

### Post by GavinZac on 2007-10-06
> **scwinn said:**
> But I just do NOT get it. Feisty had a very simple desktop effect option. It allowed wobbly windows and spoun the desktop around 3D style to give me access to different work surfaces. Is there any very simple way to do this again? Why would UBUNTU developers tamper with something that worked so easily and elegantly?

so does gutsy :S

it has standard, more, and extra. standard is the default, more is the cube, etc. and extra is most stuff.

mind you, the fuller featured compiz settings manager is quite elegent, actually.

---

### Post by greenstar on 2007-10-08
> **scwinn said:**
> But I just do NOT get it. Feisty had a very simple desktop effect option. It allowed wobbly windows and spoun the desktop around 3D style to give me access to different work surfaces. Is there any very simple way to do this again? Why would UBUNTU developers tamper with something that worked so easily and elegantly?

Desktop compositing isn't simple by any stretch of the imagination. If it were, Microsoft & Apple would be doing it too. Really, Compiz wasn't all that elegant in Feisty. Simple, yes, but not elegant.

A simple method to do/enable something complex does not confer simplicity to the complex task, but rather is intended to bring enough simplicity to the complex task as to make it more widely available to those who might wish to benefit from it's function.

For example, let's consider the procedure to correct vision, now known as Lasik. It used to be called Radial Keratotomy, when it required a surgeon with extremely steady hands and a high level of manual surgical proficiency. Currently, this procedure has been advanced with more modern technology so that we now have physicians with more technical skill, rather than manual skill, using computer controlled lasers. The types and range of skills necessary for RK are no longer necessary for physicians performing Lasik. However, I bet they still teach the lessons learned from the RK years so that the physicians performing Lasik will be knowledgeable about the background, hazards, etc. of the procedure they will be performing.

The procedure to correct vision is now much simpler, in surgical terms, but is just as complex at the biological level. After all, we *are* still talking about eye surgery.

The same is true with desktop compositing. What was previously done with much manual intervention can now be done in a much simpler, more automated way. This doesn't mean that desktop compositing has all of a sudden 'miraculously' become a simple technology. It may still, from time to time, require a bit of expertise, some manual intervention or at least an understanding of the concept from a technical standpoint. 

That being said, if there's something I/we can help you with, bring it and we'll do our best. :)
Greenstar

---

### Post by FuturePilot on 2007-10-08
> **greenstar said:**
> Desktop compositing isn't simple by any stretch of the imagination. If it were, Microsoft & Apple would be doing it too.
But Microsoft and Apple are using compositing. How do you think Microsoft pulled off the Aero effects
[DWM]("http://en.wikipedia.org/wiki/Desktop_Window_Manager")
Or how did Apple pull off those spiffy Mac OS X effects 
[Quartz Compositor]("http://en.wikipedia.org/wiki/Quartz_Compositor")

---

### Post by greenstar on 2007-10-08
> **FuturePilot said:**
> But Microsoft and Apple are using compositing. How do you think Microsoft pulled off the Aero effects
[DWM]("http://en.wikipedia.org/wiki/Desktop_Window_Manager")
Or how did Apple pull off those spiffy Mac OS X effects 
[Quartz Compositor]("http://en.wikipedia.org/wiki/Quartz_Compositor")


Future Pilot: Touche!

The point I was illustrating is that compositing isn't a simple functionality. If it were it would have been easy to implement from the beginning and nobody would be asking how to do it in the forums. 

Greenstar

---

### Post by FuturePilot on 2007-10-08
> **greenstar said:**
> Future Pilot: Touche!

The point I was illustrating is that compositing isn't a simple functionality. If it were it would have been easy to implement from the beginning and nobody would be asking how to do it in the forums. 

Greenstar

Ah, I see your point. Compositing is indeed a complex thing.;)

---

### Post by scwinn on 2007-10-14
I actually now get the message "The composite extension is not available". since I upgraded to RC1. How do I fix this?

Here is more to go on...

sheldon@sheldon-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by FuturePilot on 2007-10-14
Could you post your xorg.conf?
Just post the output of this
```
cat /etc/X11/xorg.conf
```

And we need to get rid of the toggle_shaded error or else it won't start. So press Alt+F2 and type in ```
gconf-editor
```
Navigate to Apps>metacity>window_keybindings
The second key from the bottom should say toggle_shaded and the value should be blank, which we need to fix. It needs to say disabled. So change the value to disabled.

---

### Post by scwinn on 2007-10-15
I found my problem. No AGLX installed. Dont know why. Nut it is fixed. Thanks for the community support!:)

---

### Post by ramasdf123 on 2007-10-19
Still having problems with the desktop effect, installed the ATI XORG files but the prefrence says that mine has no Composite Extention, before it said desktop could not be enabled

---

