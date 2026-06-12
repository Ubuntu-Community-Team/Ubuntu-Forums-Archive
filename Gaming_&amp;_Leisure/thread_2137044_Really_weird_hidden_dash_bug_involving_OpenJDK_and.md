---
title: "Really weird hidden dash bug involving OpenJDK and Minecraft"
date: 2013-04-19
forum: Gaming &amp; Leisure
---

### Post by CalvinCopyright on 2013-04-19
All right, since this is related to Minecraft, I thought I'd post this here, in the Gaming and Leisure subforum.  I'm pretty sure my problem is unique.

I'm using OpenJDK 7 to play Minecraft, in order to avoid wrangling with Wine.  Recently, this setup has started to give me problems.

I am getting "System program problem detected" error dialogs, and prompts to send error reports to Apport.  This happens even when I'm not playing MC - I'll see it at startup, for example - but I get one of these dialogs several times an hour when I play.  Moreover, every so often, the game will freeze.  Sometimes the event will be identical to a lag spike, but some of the time, something really weird will happen to my computer:

It briefly flashes through all the windows that I have up, and then settles on a single one - Google Chrome, usually - and both the dashboard and the info-bar along the top of the screen will vanish.  I'll still be able to use whatever window it settles on, but I won't be able to switch between windows, or do anything that involves the dash, and the only way to restart my computer is to hard-reboot by holding down the power button.  I don't know if keyboard shortcuts for switching windows, etc. work, mostly because I don't know the keyboard shortcuts.  This has not happened so far when I'm NOT playing Minecraft.

I have been trying to use several mods, listed below, and installing them using MCPatcher 3.0.3; I'm pretty sure that the problems started when I used MCPatcher to install Optifine and ModLoader at the same time, and had a file conflict.  It happens even after I removed all mods from the jar, and after "force updating"; I'm currently experimenting with using MCPatcher to completely un-patch the game.  If that doesn't work, I'll try getting a fresh jar file.  I will provide updates as they come by editing the post.

Mods:
Single Player Commands - version 4.6 (I don't know if this can actually be installed with MCPatcher.)
TooManyItems for 1.5.1 (includes Mar 23, 2013 as a date; I don't remember if that's when I downloaded it or if it's something else, although it's probably the former)
Timber! (1.5.1)
ModLoader (as far as I know, it's for 1.5.1.  I should make sure of that.)
Optifine 1.5.1 HD B3

Does anyone have any idea what is happening to me?

---

### Post by carolin3 on 2013-04-19
maybe you should use the oracle's JDK?

---

### Post by Horbo on 2013-04-22
MC doesn't like Oracle Java 7, so perhaps (I am only guessing, I haven't used OpenJava myself) it also dislikes Open Java 7.

Try installing Oracle or Open Java 6 and see if running MC with that instead fixes your problem.

```
[COLOR=#000000][FONT=Verdana]sudo add-apt-repository ppa:webupd8team/java
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get update && sudo apt-get install oracle-java6-installer[/FONT][/COLOR]
```

---

