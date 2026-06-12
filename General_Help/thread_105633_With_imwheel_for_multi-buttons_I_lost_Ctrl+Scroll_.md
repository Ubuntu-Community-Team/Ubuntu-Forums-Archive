---
title: "With imwheel for multi-buttons I lost Ctrl+Scroll in firefox to change text size"
date: 2005-12-18
forum: General Help
---

### Post by Mguel on 2005-12-18
I followed the [wiki ubuntu guide to configure thumb buttons]("https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons") of my mouse, which now work great. But I lost the shortcut Ctrl+Scroll to increase/decrease text size.

Any idea how can I correct this?

Thanks,
Mguel

PS: Ubuntu 5.10, Firefox 1.5 (but also on 1.07)
PSS: I have in firefox correctñy configured to do that action at:
mousewheel.withcontrolkey.action (3)

---

### Post by BathroomNinja on 2005-12-19
I'm willing to bet that it no longer see's your scroll wheel as the same button that it used to.  Does your scrool wheel still work at all for scrolling?

---

### Post by Mguel on 2005-12-19
[QUOTE=BathroomNinja]Does your scrool wheel still work at all for scrolling?[/QUOTE]
Yep... working fine for scrolling on firefox and on other programs.

---

### Post by BathroomNinja on 2005-12-19
Adjust the value of mousewheel.withcontrolkey.action to 1, and also try 2, and tell me what happens each time.

---

### Post by Mguel on 2005-12-19
Found the problem... according to what you told me I took an extra look to the imwheelrc file and the problem was that I had the following lines uncommented from the original imwheelrc:
```
None , Up, Button4
None , Down, Button5
```
Now the Ctrl+Scroll changes the text size, but at the same time it scrolls the page... almost perfect ;)  

Could it be possible to avoid that scrolling? or is it the "usual" behaviour?

And thanks a lot for the answers ;)

---

### Post by BathroomNinja on 2005-12-19
according to this: [http://preferential.mozdev.org/preferences.html](http://preferential.mozdev.org/preferences.html)  (search for mousewheel.withcontrolkey.action to get in the right area)  , you may just need to adjust a few values.  Read over the parts about mousewheel, and see what you have it set to currently, then adjust from there, based on what the guide shows.  I hope this helps, but I can't recreate the problem right now, so it's hard for me to solve it for you, only to give you some places to look.

---

### Post by Mguel on 2005-12-19
Read the info, and according to it I have it correctly set. Nevertheless I played with the settings to see if something happened... but nothing, although text changes, the page keeps scrolling. Tired with other modifiers (alt/shift) and it's still the same.

It seem that the text size change occur only sometimes... I start scrolling slowly with the Ctrl pressed down. On every wheel mouse unit movement the page scrolls, and on some of those scrolls the font size changes, but it's not something regular either (ie every 3 wheel scroll the text changes size). Sometimes it happens pretty soon (3rd wheel mouse unit movement, but on the next maybe I have to move it 10 times before I can see the next font size change).

---

### Post by BathroomNinja on 2005-12-19
It sounds like for whatever reason, it's not always seeing that you have the CTRL key held down.  Hence, it is switching instructions between 
mousewheel.withcontrolkey.action
and 
mousewheel.withnokey.action

So you are getting the 'best' of both.

You wouldn't happen to be using a wireless keyboard and mouse would you?  I had a similar problem with my wife's desktop (using wireless) until I moved the wireless adapter to an area closer to the KB.

---

### Post by Mguel on 2005-12-19
It seems like you are clairvoyant...

In fact I'm using a wireless mouse, but not keyboard.

Tested with the mouse very near to the wireless receiver but it still has the same behaviour :(

---

### Post by BathroomNinja on 2005-12-19
[QUOTE=Mguel]It seems like you are clairvoyant...

In fact I'm using a wireless mouse, but not keyboard.

Tested with the mouse very near to the wireless receiver but it still has the same behaviour :([/QUOTE]


HA! I wish.  But I'm still willing to bet that whatever wireless device you are using, it is not sending a constant signal to ubuntu.  so instead of ubuntu seeing this:

mousebuttonmousebuttonmousebuttonmousebuttonmousebutton

it's seeing this

mousebutton-mousebutton-------------------mousebutton-----

(or something close to that.  essintially, it's not seeing the 2 keypresses as happening at the same time.  Hence, you get the behavior of a single keypress instead of the behavior of 2 keys pressed at once)

Although, oddly, it would make a LOT more sense if the KB was wireless...
I'm sure you have already tried fresh batteries.  

This is going to sound weird, but go with me here.   Try doing the CTRL-mousewheel OR just the mousewheel by it'self.  But this time when you do it, keep the mouse MOVING the entire time you do it.  Let me know what happens.

---

### Post by Mguel on 2005-12-19
[QUOTE=BathroomNinja]Although, oddly, it would make a LOT more sense if the KB was wireless...[/QUOTE]
Yep...

[QUOTE=BathroomNinja]I'm sure you have already tried fresh batteries.[/QUOTE]
Yes...

[QUOTE=BathroomNinja]This is going to sound weird, but go with me here.   Try doing the CTRL-mousewheel OR just the mousewheel by it'self.  But this time when you do it, keep the mouse MOVING the entire time you do it.  Let me know what happens.[/QUOTE]
Very weird... but as you are the clairvoyant... I'll just obey ;)  

(It's not that weird really, now that you mention it, but I wouldn't have thought it)

OK, lets do the test...
And the result: failed... not much difference.

But following your reasoning I tried another thing: press and leave pressed one of the thumb mouse buttons and then without releasing the thumb do the Ctrl+Scroll
And voila! Changing text size without scrolling a bit!

This was a really mystic and spiritual experience... :P

So a workaround for this problem would be: Thumb+Ctrl+Scroll... or is there a better way round? (besides changing the mouse)

And thanks again!
Mguel

---

### Post by BathroomNinja on 2005-12-19
I don't think there is an easy way around the problem other than what you just did.  As stated before, I think it's a polling problem, where the wireless device isn't polling/refreshing fast enough to let ubuntu know that the button is being used at the same time.  I was thinking that moving the mouse at the same time would force the polling, but as you said, using the thumb button actually worked instead.  

Without switching the keys invovled, I don't think you can fix it shy of physically opening the wireless device and haX0ring it to poll at a different rate.  Of course, I could be wrong.  I have been wrong twice before in my life /sarcasm.

I would suggest setting different Keys on the KB to adjust text size; like CTRL+UP ARROW KEY, but I take it you adjust the text size a lot and this would be a pain.  Perhaps you can set it up to work with just the thumb-button and the scroll wheel.

---

### Post by Mguel on 2005-12-19
> Perhaps you can set it up to work with just the thumb-button and the scroll wheel.
I was thinking of that... but I'll do it tomorrow, I have to sleep now.

If it doesn't work I really don't mind doing the thumb+ctrl+scroll thing (I still can move my thumb fast enough)

Cheers,
Mguel

---

### Post by taisao on 2007-10-31
Oke, this thread is quite old. But I'm also searching for a solution, after installing imwheel the Ctrl+mouse_scroll wouldn't work anymore. 

This is a solution that I have and it work for me:

put this in the imwheel configuration file _/home/[COLOR="Navy"]user[/COLOR]/.imwheelrc_ (change user with the login name)

```
".*"
Control_L, UP, Control_L|equal
Control_L, DOWN, Control_L|minus
Control_R, UP, Control_R|equal
Control_R, DOWN, Contrl_R|minus

```

change [COLOR="Navy"]equal[/COLOR] to [COLOR="Navy"]plus[/COLOR] if you use the numpad key instead of the other key (with plus and equal)

[COLOR="Navy"]".*"[/COLOR] cover all programs that is not specified in the configuration file, if you just want the settings for firefox change [COLOR="Navy"]".*"[/COLOR] to [COLOR="Navy"]"^Firefox-bin$"[/COLOR]

---

### Post by hyperair on 2008-01-12
I've got a solution! =P Derived from the post above:

```

".*"
Control_L, Up, Control_L|Button4
Control_L, Down, Control_L|Button5

```

This will work for Amarok's Control+Scroll on the tray icon as well. ^^

EDIT: Changed Control_R in the second line to Control_L on Cir's request.

---

### Post by Cir on 2008-05-16
> **hyperair said:**
> I've got a solution! =P Derived from the post above:

```

".*"
Control_L, Up, Control_L|Button4
Control_R, Down, Control_L|Button5

```

This will work for Amarok's Control+Scroll on the tray icon as well. ^^

Thanks, this fixed the problems I was having with Hardy / Firefox. Just one thing: change the second line's first "Control_R" to "Control_L".

---

