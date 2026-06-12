---
title: "Programmatically finding out the Application font"
date: 2011-01-10
forum: Desktop Environments
---

### Post by Gareth Shapiro on 2011-01-10
Hello,

I am writing an Air application and I would like to have the app use the font indicated in Appearance Preferences.
 
A similar problem to this one : 

[http://ubuntuforums.org/showthread.php?t=1643913&highlight=default+system+font](http://ubuntuforums.org/showthread.php?t=1643913&highlight=default+system+font)

I do not have Gtk::Settings and I have looked in ~/.gconf/desktop/gnome/ but I do not have an interface folder and none of the others I opened have any font details.

I have tried simply not setting a font within my application but it is using a font not specified in the Appearance Preferences at all.  It looks like Times.

Ideally I would like to be able to get this information from Ubuntu using a native process :

[http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeProcess.html](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeProcess.html)

Does anyone know of such a process that might help me get the font name of the Application font or would I have to write a script and call that from inside Air?

I have a default installation of Ubuntu 10.4 with Unity running on top of Gnome. (I think this is correct.  I certainly can get Nautilus running quite easily and as I mentioned earlier I have  ~/.gconf/desktop/gnome/ folders).

The brief is to get the application working on the default installation so I cannot install anything but the target machine I am using has got 'gconftool'.  Can this help?  Am I even looking in the right direction?

I am not a complete Ubuntu noob but this is certainly past my current knowledge and grateful for any assistance.

---

### Post by stinkeye on 2011-01-10
Font and size
```
gconftool-2 --get /desktop/gnome/interface/font_name
```


Just the font name
```
gconftool-2 --get /desktop/gnome/interface/font_name | awk '{$NF=""; print $0}'
```


Just the font size
```
gconftool-2 --get /desktop/gnome/interface/font_name | awk '{print $NF}'
```

---

### Post by Gareth Shapiro on 2011-01-11
Thanks very much stinkeye, I appreciate that.

For any other Air devs reading this.  In order to use something like this your Air application needs to be packaged as a native application.

[http://help.adobe.com/en_US/air/build/WS789ea67d3e73a8b22388411123785d839c-8000.html](http://help.adobe.com/en_US/air/build/WS789ea67d3e73a8b22388411123785d839c-8000.html)

---

