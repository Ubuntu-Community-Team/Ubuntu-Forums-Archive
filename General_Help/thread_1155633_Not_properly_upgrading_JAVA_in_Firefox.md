---
title: "Not properly upgrading JAVA in Firefox"
date: 2009-05-11
forum: General Help
---

### Post by phreaknite on 2009-05-11
Hi all and thanks for helping.  I apologize if this has been posted but a search provided no results relevant to what I need.

I am trying to fully install the JRE into my firefox so that I can play lexulous (formerly scrabulous).  The game runs as it is now but I don't have sound in the game which is important to me.  Sounds on other applications work just fine but not the sounds from Lexulous.

To fix this problem I wanted to make sure my java was up to date.  When I run a verification test [here]("http://www.java.com/en/download/installed.jsp") i get the following response:
> Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation. 

I should be on 1.6.0_13.  I have gone through the upgrade process a few times already to try and fix this.  My firefox plugins screen (about:plugins) says I am using version 1.6.0_13:

> Java(TM) Plug-in 1.6.0_13-b03

If I try to disable IcedTea it automatically disables Java, as well.  I am thinking that maybe I can uninstall IcedTea and that may fix the problem, but I don't know how to do that (and I don't know why I think that will work, either...)

Hopefully someone can help!  thanks!

---

### Post by pastalavista on 2009-05-11
The best Java is from Sun.. it's in Synaptic Package manager (if you have third party sources enabled)... search for sun-java6-jre in Synaptic or in terminal type:```
sudo apt-get install sun-java6-jre
``` and also ```
sudo apt-get install sun-java6-plugin
``` I don't remember if they're packaged together or not.

That's all I have and everything works great.

edit: I looked and I also have java-common which may be the "meta-package" that covers them all.

---

