---
title: "Realplayer in Firefox 1.5"
date: 2006-01-09
forum: General Help
---

### Post by rplantz on 2006-01-09
I had trouble installing the Realplayer plugin in Firefox 1.5. When I followed the instructions at [www.real.com](www.real.com), I got a stand alone version.

I was able to get the stand alone version linked to my Firefox in Edit->Preferences->Downloads->View & Edit Actions area. But some websites, for example allclassical.org, require a plugin.

Going to ```
about:plugins
``` provides a link to plugindoc.mozdev.org. There is a PluginDoc link to Linux and thence to RealPlayer 10. The instructions show where the nphelix.so and nphelix.xpt files need to be copied in order to get the plugin to work.

I'm still having problems with the RealPlayer display. It's garbled in such a way that I cannot use the controls. Fortunately, I'm still able to use the global volume control.

By the way, I'm running a 64-bit Ubuntu on an AMD64. I followed the instructions at [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) to install the 32-bit Firefox 1.5 on my system. These instructions include getting java and flashplayer working.

I'm sitting here with a cat nestled in my lap, listening to some very nice music from allclassical.org.  :-)

---

### Post by dcstar on 2006-01-09
[QUOTE=rplantz]I had trouble installing the Realplayer plugin in Firefox 1.5. When I followed the instructions at [www.real.com](www.real.com), I got a stand alone version.
......
I'm still having problems with the RealPlayer display. It's garbled in such a way that I cannot use the controls. Fortunately, I'm still able to use the global volume control.

By the way, I'm running a 64-bit Ubuntu on an AMD64. I followed the instructions at [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) to install the 32-bit Firefox 1.5 on my system. These instructions include getting java and flashplayer working.

I'm sitting here with a cat nestled in my lap, listening to some very nice music from allclassical.org.  :-)[/QUOTE]
Try installing mozplugger.

---

### Post by encompass on 2006-01-10
You should be able to link the pluggins from the /opt/RealPleardi/mozilla to your dir in /opt/firefox/Pluggins/ directory... I did it along time ago and am trying now... let find out if I can get it working...

---

### Post by encompass on 2006-01-10
Well there we go!  I got it....
> sudo ln -s /opt/Realplayer/mozilla/nphelix.* /opt/firefox/plugins/

that sould do it... but just make sure to make the proper chages of where your firefox and realplayer directories are.
How that works... Tell me if it does.

---

### Post by rplantz on 2006-01-11
[QUOTE=encompass]Well there we go!  I got it....

that sould do it... but just make sure to make the proper chages of where your firefox and realplayer directories are.
How that works... Tell me if it does.[/QUOTE]

RealPlayer works okay on my system. It's just that the RealPlayer display is somewhat garbled, which prohibits me from doing things like change volumn, pause, etc.

I think it probably is due to my running 32-bit Firefox 1.5 on a 64-bit system.

The 64-bit system is very "interesting."  ;-) To be honest, if I had to rely on my system to get work done for somebody else, I would run 32-bit.

---

