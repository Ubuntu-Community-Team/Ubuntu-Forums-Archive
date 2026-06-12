---
title: "alt + button 1; &quot;raise behaviour&quot;, 11.04 beta, compiz"
date: 2011-04-12
forum: Desktop Environments
---

### Post by damogran on 2011-04-12
hi there,

i've just upgraded from ubuntu 10.04 to the latest 11.04 beta and encountered a little difference in the window raise behavior in compiz which i would like to change if possible.

lets say i have a desktop with two windows, window A (which is in front) and B (which is in the background)

in the past i could raise B by pressing ALT + button1 on any spot on B (the same method you can move windows by clicking on every spot, not just only on the window border)
but now, ALT + button1 only moves the window but B keeps in the background. i do have to click on the border of B to get the window on top.

i know this may sounds stupid but it is a feature i really liked.
searched all over the compiz settings manager but could not find a button to change it

is there any? :)

thanks for your help !

damo

---

### Post by ankspo71 on 2011-04-12
Hi,
First make sure the "move window" plugin is enabled. 
Second, go to General Options > Focus and Raise Behavior;
and make sure "Raise On Click" is enabled.

Without Raise On Click enabled, we would need to click on a titlebar to raise a window, and I can reproduce the problem you are having by disabling it.

Hope this helps.

---

### Post by damogran on 2011-04-12
> **ankspo71 said:**
> Hi,
First make sure the "move window" plugin is enabled. 
Second, go to General Options > Focus and Raise Behavior;
and make sure "Raise On Click" is enabled.

Without Raise On Click enabled, we would need to click on a titlebar to raise a window, and I can reproduce the problem you are having by disabling it.

Hope this helps.

Hi there,

thanks for your reply!

unfortunately i forgot something to mention. another feature i use a lot is that you don't raise a window by clicking somewhere on it (except I am pressing alt). the all day scenario is that i have a terminal in front and a browser or some documentation in the background. with that setup i can work in the terminal and copy and past stuff from the documentation in the background without raising the window an loosing my terminal. there plenty of other situations where i use that. but actually this is where the ALT story comes in place because it gives me the control in when i want to have a windows raised and when not.

i know this sounds very very specific, but as a matter of fact i'm using that feature for about 10 years, and it worked before with compiz in ubuntu. 

cheers

damo

---

### Post by halfmanhalfpint on 2011-05-06
I use "traditional" Unix window focus as well, i.e. sloppy focus,
no click on raise, use alt + button 1 to raise.
Not being able to type into a background window is just dumb.
I blame Apple.

I have to login with Ubuntu Classic with no effects to
get alt + button 1 to work in 11.04.

Looks like a bug.

Michael

---

### Post by dchky on 2011-05-07
I concur, this particular feature (alt+button1) is one I've been using since OLVWM (Maybe even before that) to raise windows.

ankspo71 I think misunderstood the problem - the basic click to raise is not desirable since it brings the entire window to the front in cases where all you might want to do is give focus to a specific form field in the background as you copy and paste between windows.

The Solution (for me anyway)

Compiz settings -> General -> Key bindings

Raise Window will be set to Ctrl + button 6 (or some other weirdness)

Change this to <Alt>Button1

It'll pop up a window saying it conflicts with the window move feature - just click "Set Raise Window anyway" since in this case the conflict is okay. (You can still move windows using alt+button1 in addition to having the ability to raise windows properly once more)

---

### Post by damogran on 2011-07-14
> **dchky said:**
> I concur, this particular feature (alt+button1) is one I've been using since OLVWM (Maybe even before that) to raise windows.

ankspo71 I think misunderstood the problem - the basic click to raise is not desirable since it brings the entire window to the front in cases where all you might want to do is give focus to a specific form field in the background as you copy and paste between windows.

The Solution (for me anyway)

Compiz settings -> General -> Key bindings

Raise Window will be set to Ctrl + button 6 (or some other weirdness)

Change this to <Alt>Button1

It'll pop up a window saying it conflicts with the window move feature - just click "Set Raise Window anyway" since in this case the conflict is okay. (You can still move windows using alt+button1 in addition to having the ability to raise windows properly once more)


thanks! excatly what i was looking for. just a small addition just in case someone else wants that too.

you have also uncheck "raise on click"

---

### Post by lenooh on 2012-04-13
> **damogran said:**
> thanks! excatly what i was looking for. just a small addition just in case someone else wants that too.

you have also uncheck "raise on click"

But some of us want to have it the other way around:
I want to move a window (with alt+click) without raising it. I have focus follows mouse, so I click only when I want to raise. In my case alt+click should not raise window.

---

