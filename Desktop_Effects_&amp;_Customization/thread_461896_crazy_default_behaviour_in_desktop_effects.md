---
title: "crazy default behaviour in desktop effects"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by emax on 2007-06-02
Hi there,

I have upgraded my machine to Feisty and when I try to enable desktop effects, the default behavior is crazy.

For example, a left-click of the mouse creates a draggable box for creating a screenshot!

I have nuked my .compiz and .gconf/apps/compiz directories to no avail.

I also tried enabling the effects as a newly-created test user to ensure nothing is screwy with my settings.  Same behaviour.

I have run several older versions of compiz in the past and I suspect that there is some configuration conflict somewhere.

Any ideas how I can sanitise my settings?

Thanks.

---

### Post by Lord Illidan on 2007-06-03
I get this too, on a new install of Feisty. I also cannot click any button with the mouse. This is very infuriating, I don't need to tell you that. Also, Alt + left mouse click seems to write on the desktop.

I also find that I start making screenshots of little things, look at the attachment just by clicking on them, it seems.

Beryl, however works very well.

---

### Post by aldreis on 2007-06-03
> **emax said:**
> Any ideas how I can sanitise my settings?

You could start by temporarily disabling the screenshot plugin. It's in the Extras tab on the Beryl Settings Manager. ;-)

---

### Post by RedGlow on 2007-06-09
> **emax said:**
> Hi there,

I have upgraded my machine to Feisty and when I try to enable desktop effects, the default behavior is crazy.

For example, a left-click of the mouse creates a draggable box for creating a screenshot!

I have nuked my .compiz and .gconf/apps/compiz directories to no avail.

I also tried enabling the effects as a newly-created test user to ensure nothing is screwy with my settings.  Same behaviour.

I have run several older versions of compiz in the past and I suspect that there is some configuration conflict somewhere.

Any ideas how I can sanitise my settings?

Thanks.
I did a clean installation of ubuntu, and at first everything worked well with compiz. Then switched into a kubuntu, tried to make compiz work in kde, but no success. Tried some suggestion from the net, but nothing worked; at that time realized that the proprietary ATI driver (automatically installed don't-know-why) did screw my DRI, and got it right again. After that, compiz started making crazy things as it does to you now; exactly the same behaviour, both under GNOME and KDE. But still haven't got any idea how to solve this :-(

---

### Post by emax on 2007-06-10
> **aldreis said:**
> You could start by temporarily disabling the screenshot plugin. It's in the Extras tab on the Beryl Settings Manager. ;-)

Thanks, but I don't have Beryl installed.

Using gconf-editor, I can see that my initiate_button for the Screenshot plugin is "<Super>Button1", so I'm not sure why it is being activated by a simple left-click.

---

### Post by emax on 2007-06-14
Disabling the Screenshot plugin allows me to left-click.  I wouldn't call that a "solution" to the problem though.

Right-clicking now zooms the desktop (as does <Super>Button4 & 5 as expected.

Of course, I could now disable the zoom plugin too but where does all this stop?!

Still keen to work out why the default behaviour is screwed.  Interesting to hear that others are also experiencing this too.

Any more ideas??

---

### Post by emax on 2007-06-14
Actually, I just reverted to metacity and set a keybinding using <Super>1 for switching to desktop 1.

I noticed that merely typing "1" moved me to desktop 1.

Therefore this doesn't seem to be a compiz problem, rather a gnome (or possibly even a keyboard problem).

As others seem to be having similar behaviour, I wonder if it is software rather than hardware?

---

### Post by emax on 2007-06-14
Fired up the machine from the 7.04 install CD and repeated my experiment with the <super>1 keybinding for desktop 1 in metacity.  Couldn't duplicate the behaviour.

At least that rules out a faulty keyboard!

---

### Post by CrazyGuy123 on 2007-06-14
I presume you tried pressing all the modifier keys a few times to see if that resolves the issue (both left and right shift, ctrl, winkey, alt, and the "context menu" button)

I have had this in both windows and ubuntu, and doing that procedure always fixes it - I suspected it happens when the batteries in my wireless keyboard were getting low, so key release signals were never sent to the computer - but it could be any other problem - I never bother investigating because the fix only takes 2 secs to do, and it only happens every few weeks.

---

### Post by emax on 2007-06-14
> **CrazyGuy123 said:**
> I presume you tried pressing all the modifier keys a few times to see if that resolves the issue (both left and right shift, ctrl, winkey, alt, and the "context menu" button)

Thanks for that, it was worth a try but to no avail.  I'm on a standard PS/2 keyboard, a Logitech Internet Pro keyboard to be precise.

The <Super> key works normally when booted off the live CD but seems to behave as if permanently pressed in on my installation of 7.04 in both GNOME and KDE.

---

### Post by dannyboy79 on 2007-06-14
you can modify compiz settings AFTER you install gnome-compiz-manager (i think that's it), which may help

---

### Post by emax on 2007-06-14
> **dannyboy79 said:**
> you can modify compiz settings AFTER you install gnome-compiz-manager (i think that's it), which may help

Thanks, but it seems that the problem is more to do with my keyboard configuration than compiz now.

I have just started a new thread more focussed on this issue:

[http://ubuntuforums.org/showthread.php?t=474047](http://ubuntuforums.org/showthread.php?t=474047)

Thanks

---

### Post by glyphobet on 2007-07-26
I was having exactly the same symptoms. I was able to fix this as follows:

1. start compiz via desktop-effects
2. use gconf-editor to disable the screenshot, annotate, and zoom plugins
3. log out and log back in again

Note that you can send an (apparently) normal click by holding down Control and clicking; this is how I was able to use gconf-editor while the mouse was otherwise broken.

Running gnome-compiz-preferences seems to mangle my gconf compiz settings, so I'd avoid using it to change compiz settings. desktop-effects may also mangle the gconf compiz settings when it gets run; running it seems to make these problems return.

---

