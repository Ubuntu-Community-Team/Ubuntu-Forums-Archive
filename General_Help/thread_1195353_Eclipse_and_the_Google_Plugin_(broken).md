---
title: "Eclipse and the Google Plugin (broken)"
date: 2009-06-23
forum: General Help
---

### Post by manualqr on 2009-06-23
I installed Eclipse 3.4.2 yesterday in order to use the Google plugin (for GWT and AppEngine). I installed the sun-java6-jre and jdk for eclipse.

Then I added Google repository for the plugins to Eclipse and installed them, but Eclipse isn't recognising anything. Eclipse showed a progress-bar, downloaded jars, said it was 'installed', and restarted itself but I can't find anything relating to GWT inside the IDE. There are no Google entries in the New Project dialog, in the toolbar, or any place else.

So I looked inside my eclipse/plugins folder and sure enough, all of the necessary google jars were there.

I re-installed the plugins with no luck. I tried it with the java5 jre with no luck. I tried installing it via the dropins/ folder with no luck. Eclipse just refuses to look at the google plugin!

Can someone please help me get the google plugin installed correctly?

---

### Post by manualqr on 2009-07-14
finally found a solution:
re-install eclipse and reboot.

worked like a charm (but why, I don't know).

- sorry for inadvertently bumping this old one back up

---

