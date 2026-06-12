---
title: "How to stop Netbeans stealing focus?"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Rogerborg on 2010-10-15
(Posted under Desktop Environments as presumably the fix will be WM specific)

Using Ubuntu 9.10 Desktop (although the same issue exist in 10.04 and 10.10 Desktop), standard install with GNOME / Compiz (i.e. desktop effects turned on).

Problem: Netbeans IDE 6.8 (et al) has a pathological urge to steal input focus on every interesting event, e.g. start debugging, hit a breakpoint.  Given the geological timescales it takes Netbeans to actually do anything, this means either wasting time waiting and watching it, or getting rudely ripped out of another app where I'm actually doing something productive.

Yes, I've chimed in on the issue(s) already raised at the Netbeans forums about this, but I doubt it's going to get changed.

So I'm looking for a way to stop Netbeans - *specifically Netbeans*, it seems to be 'special' - from stealing input focus.

I've tried and failed using Compiz ccsm:
General Options / Focus and Raise Behaviour / Focus Prevention Level set to "Very High" and Focus Prevention Window set to "any" or "class=java.lang.Thread".  Neither has any effect on Netbeans stealing input focus.

Window Rules (enabled) / Matches / No Focus / class=java.lang.Thread

Stops Netbeans getting focus when I mouse-over, but doesn't stop it stealing focus itself.  Other rules, e.g. "Non-movable windows" do take effect on Netbeans using "class=java.lang/Thread".  It just seems to be input focus stealing that doesn't work.

I'm prepared to get low down and dirty but would rather not fork Netbeans / Compiz / GNOME - although I might cheerfully fork a Netbeans dev in the eye. ;)  Suggestions would be most gratefully received.

---

