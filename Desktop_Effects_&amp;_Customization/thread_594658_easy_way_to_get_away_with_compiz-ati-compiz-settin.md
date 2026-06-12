---
title: "easy way to get away with compiz-ati-compiz-settings problem"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by bhati-ubu on 2007-10-28
well i had same problem and when i tried to get help from forums every information was scattered so it can be useful for those who have ATI graphics card and want to enable desktop effects ......

well whole thing is like this    
ATI graphics card use fglrx driver and this in turn do not recognize compiz hence we cant use AIGLX we  have following options 
>use some other driver        //bad idea 
if u did then better go to restricted drivers and enable fglrx
>add compiz option in /etc/x11/xorg.conf and try..   //again a bad idea didn't work in my case 


there is simple way to do this is 

>install xserver-xgl  using
sudo apt-get install xserver-xgl 

>restart xserver using <control> <alt>backspace 

>now enable desktop effects
system->preferences->appearance->visual effects

>now if u want to change settings for compiz download ccsm its really easy to configure
sudo apt-get install  compizconfig-settings-manager

>go  to system->preferences->advanced desktop settings

>to know about various settings and how to work with compiz go to 
  [http://wiki.compiz-fusion.org/Plugins/](http://wiki.compiz-fusion.org/Plugins/)

now go and enjoy compiz -fusion .........:lolflag:

---

### Post by lavinog on 2007-10-28
> **bhati-ubu said:**
> well i had same problem and when i tried to get help from forums every information was scattered so it can be useful for those who have ATI graphics card and want to enable desktop effects ......

well whole thing is like this    
ATI graphics card use fglrx driver and this in turn do not recognize compiz hence we cant use AIGLX we  have following options 
>use some other driver        //bad idea 
if u did then better go to restricted drivers and enable fglrx
>add compiz option in /etc/x11/xorg.conf and try..   //again a bad idea didn't work in my case 


The new proprietary ATI driver has AIGLX support
here is a link to set it up:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

The thing is that compiz has this driver blacklisted still because AIGLX support is only available in the latest driver (released last week)
apparently the next version of compiz-fusion will un-blacklist it

when you run compiz from the command line it should give you an identifier saying that it is blacklisted
> Blacklisted PCIID '1002:5955' found 


to override the blacklist
```
echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```


another thing you may need to do (because i did) is to enable aiglx and composite in xorg.conf
they were disabled from previous drivers.
I just removed these sections
```

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

After that you should be able to enable desktop effects

---

### Post by knuutsen on 2007-11-02
> **lavinog said:**
> The new proprietary ATI driver has AIGLX support
here is a link to set it up:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

The thing is that compiz has this driver blacklisted still because AIGLX support is only available in the latest driver (released last week)
apparently the next version of compiz-fusion will un-blacklist it

when you run compiz from the command line it should give you an identifier saying that it is blacklisted


to override the blacklist
```
echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```


another thing you may need to do (because i did) is to enable aiglx and composite in xorg.conf
they were disabled from previous drivers.
I just removed these sections
```

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

After that you should be able to enable desktop effects

Thank you very much.
It was very helpful, dont need Xserver.xgl anymore. But i have a little difficulties enabling videos or dvb-t or other video - modes while im running compiz. If i quit it, all goes well..if i change again to compiz it wont work. Do you have an idea? How can i fix it?

---

### Post by lavinog on 2007-11-11
I think I remember seeing this being due to the new ati driver, but i would expect it to be fixed soon.
I am looking into it myself. But my laptop is the only ati machine i have, and i am not running compiz that often to conserve battery life.

---

### Post by jimerickso on 2007-11-11
if i understand you correctly and you are using mplayer try:

mplayer -vo x11 /path/ to/file

if using vlc try setting video driver to xshm.

---

### Post by hebetude on 2007-11-11
> **lavinog said:**
> The new proprietary ATI driver has AIGLX support
here is a link to set it up:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

another thing you may need to do (because i did) is to enable aiglx and composite in xorg.conf
they were disabled from previous drivers.
I just removed these sections
```

Section "ServerFlags"
    Option        "AIGLX" "off"
EndSection

Section "Extensions"
    Option        "Composite" "Disable"
EndSection

```After that you should be able to enable desktop effects

Thanks that fixed me right up.  It writes a new xorg.conf, why would it not set itself up with settings as basic as this :/.  5400fps in glxgears now

---

