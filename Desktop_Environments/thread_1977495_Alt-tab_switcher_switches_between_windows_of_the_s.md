---
title: "Alt-tab switcher switches between windows of the same application sometimes"
date: 2012-05-10
forum: Desktop Environments
---

### Post by sparhawkthesecond on 2012-05-10
Hi,

I have alt-tab set to switch between applications, which is the default (I think). *However*, if the previous window I viewed was the same application, then alt-tab switches between windows of that same application, rather than selecting the next application. In general, Ubuntu alt-tabbing is application-based, not windows-based, so this behaviour is inconsistent.

For example, I have two Nautilus windows open (N1 and N2), and one Firefox window open (F1). I click on F1, then N1. When I alt-tab, I alternate between F1 and N1, as expected. Alternatively, I click on N2, then N1. Now when I alt-tab, I alternate between N1 and N2. I would have expected alt-tab to alternate between N1 and F1.

Does anyone else see this behaviour?

---

### Post by nizamibilal1064 on 2012-05-10
> **sparhawkthesecond said:**
> Hi,

I have alt-tab set to switch between applications, which is the default (I think). *However*, if the previous window I viewed was the same application, then alt-tab switches between windows of that same application, rather than selecting the next application. In general, Ubuntu alt-tabbing is application-based, not windows-based, so this behaviour is inconsistent.

For example, I have two Nautilus windows open (N1 and N2), and one Firefox window open (F1). I click on F1, then N1. When I alt-tab, I alternate between F1 and N1, as expected. Alternatively, I click on N2, then N1. Now when I alt-tab, I alternate between N1 and N2. I would have expected alt-tab to alternate between N1 and F1.

Does anyone else see this behaviour?

It is perfectly normal...if you want to go to firefox just hold the Alt button and press Tab....it will show you all the active windows, keep pressing Tab until you reached desired application...if you will press Alt + Tab and release it and if two active windows of same application are open then they will be switched....hope it will help you:KS

---

### Post by sparhawkthesecond on 2012-05-10
It just doesn't quite seem consistent to me. I'm happy with alt-tab switching applications (not windows) generally, so why should it switch windows if the highest two windows are from the same application? If my window stack is N1 N2 F1 F2, then (without pausing), there is no way to alt-tab to F2, for example. However, you can alt-tab to N2. It just doesn't seem right!

Also, I seem to remember that you could not alt-tab to N2 in 11.10, but perhaps my memory is incorrect. I seem to remember that you could only switch windows within an application with alt-<key above tab>.

---

### Post by markbl on 2012-05-11
I don't know what the first reply here is about but 12.04 works the same as 11.10, i.e. alt+tab switches apps, alt+<key above tab> switches windows within the same app. Always, unless you have configured it non-standard in Compiz or added an extension. Works the same in Unity and gnome-shell (and Max OS X for that matter). You seem to be seeing something odd.

---

### Post by sparhawkthesecond on 2012-05-11
So sorry, just to clarify, I do generally see the behaviour that you describe, where alt-tab switches apps, and alt-<key above tab> switches windows within that app, EXCEPT when the front-most two windows are from the same app. Then, alt-tab switches app.

e.g. open two nautilus windows, and have another application (say firefox) open. Switch to Nautilus, then alt-<key above tab> to the other nautilus window (hence making the front two windows from nautilus). Then hit alt-tab quickly. In my case, I switch to the other nautilus window, where I would have expected to switch to the other application (e.g. firefox).

---

### Post by markbl on 2012-05-11
> **sparhawkthesecond said:**
> So sorry, just to clarify, I do generally see the behaviour that you describe, where alt-tab switches apps, and alt-<key above tab> switches windows within that app, EXCEPT when the front-most two windows are from the same app. Then, alt-tab switches app.

Oops, sorry I knew what you mean't but I use gnome-shell where it works as you expect. I just now logged into Unity and was shocked to discover it works as you say above! I always thought alt+tab worked the same as gnome-shell.

I have no idea why Canonical have implemented like this? Seems to make it too complicated if you ask me. In general, I only use alt+tab/backtick when I am fast switching between 2 specific apps or windows so that is maybe why they have done it that way?

I mainly use spread view (super+w in Unity) as I think that is the easiest way to switch between apps/windows. You don't have to think too hard. Gnome-shell is essentially designed around spread-view so that is why I prefer it.

---

### Post by sparhawkthesecond on 2012-05-11
Strange, huh?! Thanks for confirming the "bug" (feature?).

(FWIW, I find spread view a bit hard to use, because I cannot identify which window is which quickly. Also, I'm a bit more keyboard focussed than mouse focussed.)

---

### Post by sparhawkthesecond on 2012-05-11
I created a [bug report](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/998285). If it's not too much trouble, please confirm it, by saying that it affects you.

Cheers.

---

### Post by markbl on 2012-05-11
> **sparhawkthesecond said:**
> I created a [bug report](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/998285).
But I don't think it is a bug. Clearly that is intended design. I am guessing that the idea is that alt+tab should always switch between the last 2 windows which is the fundamental use case for alt+tab. The gnome-shell method means you have to think first "do I have to alt+tab, or alt+backtick" to get to the last window depending on whether it is the same app or not. The new scheme makes sense to me actually.

BTW, the spread (activities) view in gnome-shell makes it a little easier to discriminate between windows because they are labelled, unlike spread view in Unity.

---

### Post by sparhawkthesecond on 2012-05-11
Ah ok, but I think even if it is "intended design", I feel it's counter-intuitive. Perhaps I should give gnome shell a run. The labelled spread sounds great. Do you know if gnome shell is compatible with Unity? i.e. can I switch back and forth and not lose settings, etc.? Thanks.

---

### Post by markbl on 2012-05-12
> **sparhawkthesecond said:**
> Do you know if gnome shell is compatible with Unity? i.e. can I switch back and forth and not lose settings, etc.?
Yes. Just "sudo apt-get install gnome-shell" or via software center. That gives a "GNOME" option on the login screen which is gnome-shell, "Ubuntu" is Unity. Neither affects the other.

While in gnome-shell, go to [http://extensions.gnome.org](http://extensions.gnome.org) and just click to install extensions. The [media-player-indicator](https://extensions.gnome.org/extension/55/media-player-indicator/) and [alternative-status-menu](https://extensions.gnome.org/extension/5/alternative-status-menu/) are two essentials I think.

---

### Post by sparhawkthesecond on 2012-05-12
Thanks for that. I'll give it a go when I have a bit more time to fiddle. :)

---

### Post by markbl on 2012-05-15
> **markbl said:**
> 
BTW, the spread (activities) view in gnome-shell makes it a little easier to discriminate between windows because they are labelled, unlike spread view in Unity.
Just want to correct this post of mine ...

I later discovered that Unity spread (scale = super+w) view can label windows somewhat like gnome-shell. Just enable the "Text" plugin in compiz settings (ccsm) and then enable the "Scale Addons" plugin and activate "Window Titles". Compiz will muck about then but log out/in and should work.

---

### Post by sparhawkthesecond on 2012-05-16
Thanks for that. I was actually envisaging each window having a graphical icon, rather than a text label. Having said that, you inspired me to google more, and I found out that you can do it via ccsm > Scale > Appearance > Overlay Icon. FWIW it looks pretty crappy (expecially "big"), and I much prefer the look of [this gnome-shell extension]("https://extensions.gnome.org/extension/60/overlay-icons/").

---

### Post by sparhawkthesecond on 2012-05-16
> **markbl said:**
> But I don't think it is a bug.

I think I've come across a workaround that suggests it is a bug (either in the behaviour we've been talking about, or in the workaround). Either way there is inconsistent behaviour between the two.

Install ccsm, then deselect Desktop > Ubuntu Unity Plugin > Switcher > Automatically grid windows on timer in switcher. You might need to run "$ unity --replace", but I can select or deselect this setting and the alt-tab behaviour changes accordingly. It's a bit funny that this setting should have this side-effect, as it's not directly related.

(Turning on this setting does the following. When holding onto alt-tab, if you hover over an application icon with multiple windows open, after a short time the window thumbnails are exposed. If this setting is off, then alt-tab only shows the application icon.)

---

