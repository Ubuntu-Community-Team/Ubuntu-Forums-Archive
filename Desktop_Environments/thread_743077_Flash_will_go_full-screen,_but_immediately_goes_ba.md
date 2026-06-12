---
title: "Flash will go full-screen, but immediately goes back to embedded"
date: 2008-04-02
forum: Desktop Environments
---

### Post by Levander on 2008-04-02
I originally got full screen flash to work with compiz enabled by unclicking the "Legacy Fullscreen Support" box in the Enable Workarounds plugin.  I had the standard problem where when on Youtube, I'd click on the full screen button, and get a tiny window that would disappear when you click on it.  But, unclicking "Legacy Fullscreen Support" let me use full screen flash just fine.

However, I was recently playing with compiz settings, figuring out how to use the cube, I found a kick-*** theme (SolidSlate Modified)...  Few days later, I'm back on Youtube.  Now, when I click on full screen, it does go full screen for a split second.  Then it zaps, on its own, right back into the embedded player in Firefox.

I tried going into the Compiz Settings Manager and in Preferences, I reset all settings to default.  Then, I go and unclick the "Legacy Fullscreen Support" box.  On Youtube, I click on the full-screen button, and the same thing happens with snapping back to the embedded flash player.

If I go to "Advanced Desktop Effects Settings" and choose "None", I'm back to getting full screen flash on Youtube just fine again.  But, that leaves the problem that I can't use my new kick-*** theme.

Anyone seen this before?  Anyone know how to fix?  Anyone know if Flash issues have gotten any better in Hardy?  What about 64-bit Hardy, which is what I'm thinking about switching to.

---

### Post by Levander on 2008-04-03
Well, I was able to reproduce it. In the Appearance dialog, I'm using Normal for Effects.  Then, you go to Compiz Settings and turn off the Snapping Windows plugin.  Completely exit X, like with a Ctrl-Alt-Backspace is what I did.  Log back in.  Go to Youtube.  Play a video and click the full-screen button.   At this point I saw full screen for an instant and then it snapped right back to embedded.

I did test Youtube before starting this whole process, and full-screen worked fine.

Is it worth it to file a bug with Hardy about to come out in a couple of weeks?

---

### Post by jens.bergqvist on 2008-04-30
I have this issue on Hardy (final). Disabling "Unredirect Fullscreen Windows" makes fullscreen flash work reliably again. This interferes with regular video playback though... Are there any other solutions to this?

---

### Post by wfsswmr7285 on 2008-06-22
bump

---

### Post by hanzomon4 on 2008-07-01
Double Bump

---

