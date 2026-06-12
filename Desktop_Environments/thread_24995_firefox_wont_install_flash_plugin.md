---
title: "firefox wont install flash plugin"
date: 2005-04-08
forum: Desktop Environments
---

### Post by roadrash on 2005-04-08
I just installed mozilla firefox 1.02 with kynaptic but when i went to a website with macromedia flash content, mozilla gave the usual symbols with the "click here to download plugin".  but when you click on the link, firefox opens a window saying "firefox is now cheking for available plugins" and just locks upp.

is this a bug?

---

### Post by Jagasian on 2005-04-08
I had similar problems with Firefox under Fedora Core 3, but haven't gotten around to using it under Kubuntu.  Konqueror is keeping me satisfied right now.  I would say that yes it is a bug.  Hopefully another forum reader has more info and advice.

---

### Post by roadrash on 2005-04-08
Yep its a bug......

I just downloaded firefox from the mozilla website & installed it & evrything works fine & it installed the flash plugin.  So it must be a bug..

---

### Post by Jagasian on 2005-04-08
[QUOTE=roadrash]I just installed mozilla firefox 1.02 with kynaptic but when i went to a website with macromedia flash content, mozilla gave the usual symbols with the "click here to download plugin".  but when you click on the link, firefox opens a window saying "firefox is now cheking for available plugins" and just locks upp.

is this a bug?[/QUOTE]
 I forgot to ask, are you running Kubuntu from a live CD, or a hard drive install?

---

### Post by roadrash on 2005-04-08
Its installed on my hard disk...

I just submitted a bug report in bugzilla.

---

### Post by denzilla on 2005-04-08
It installed fine for me using Kynaptic.

*Oops, my bad. I had it in my head that you couldn't get FF to install, sorry. I just followed the directions that came with flash and it worked ok.

---

### Post by roadrash on 2005-04-08
but has it been able to install the flash plugin?   if your not sure go here: [http://www.motograndprix.com/en/motogp/index.htm](http://www.motograndprix.com/en/motogp/index.htm) & see if it will display the page correcy or install the flash plugin on demand..

---

### Post by bittner on 2005-08-06
I have succeeded to install the Flash plugin for Firefox. The problem is, writing to /usr/lib/mozilla-firefox requires root privileges. We need to install the plugin manually using sudo on the command line.

1. First download the Macromedia Flash Player installer from [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

2. Make sure you have the packages gsfonts and gsfonts-x11 installed: (the installer will remind you later in any case)
```
sudo apt-get install gsfonts gsfonts-x11
``` 
3. Unpack it and execute the installer as root:
```
sudo ./flashplayer-installer
```
4. When prompted for the installation path of the Mozilla, etc. enter:
```
/usr/lib/mozilla-firefox
```
5. You're done. Run firefox and browse a flash site to ensure you everything worked out!

What I have not been able to do so far is installing the flash plugin for konqueror. I have not been able to understand where it looks for the plugins (ns-plugins) thus I dunno what installation path (see above) I have to enter.   :?

---

### Post by arjaybe on 2005-08-06
Konqueror plugins are configured in Settings - Configure Konqueror - Plugins.  You could just add /usr/lib/mozilla-firefox there.

---

### Post by bittner on 2005-08-06
Okay, now I know (again! - I'm getting old) how to make Mozilla plugins available for Konqueror:

- Go to *Konqueror -> Settings -> Configure Konqueror... -> Plugins* and add the path of the Mozilla plugin directory to the "Netscape Plugins" list box. For (K)Ubuntu this should be ```
/usr/lib/mozilla-firefox/plugins/
```
All plugins you install for Mozilla Firefox will then automatically be available for Konqueror.

---

### Post by bittner on 2005-08-06
arjaybe, you were faster posting it - for a second! :-)

Can you check though: When you browse to [http://www.rds.it](http://www.rds.it) this site works with Firefox, but Konqueror still asks for the plugin. Why? (Shockwave? Then it should not work in Firefox either, should it?)
Another italian radio site, [http://www.rtl.it](http://www.rtl.it), works with both browsers (at least for the flash stuff). Strange.

Can I fix this Konqueror problem? How?

---

### Post by az on 2005-08-06
You can install flash hassle-free by installing flashplugin-nonfree and gsfonts-x11 from universe.  
Flashplugin-nonfree downloads the latest flash and install it for you.  No fuss.

---

### Post by arjaybe on 2005-08-07
[QUOTE=bittner]arjaybe, you were faster posting it - for a second! :-)

Can you check though: When you browse to [http://www.rds.it](http://www.rds.it) this site works with Firefox, but Konqueror still asks for the plugin. Why? (Shockwave? Then it should not work in Firefox either, should it?)
Another italian radio site, [http://www.rtl.it](http://www.rtl.it), works with both browsers (at least for the flash stuff). Strange.

Can I fix this Konqueror problem? How?[/QUOTE]

Both of those sites worked for me in Konqueror.  But the first one failed in Firefox, maybe because I have the Flashblock extension.

---

