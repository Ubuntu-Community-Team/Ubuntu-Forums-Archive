---
title: "Wallpaper SlideShow/Stack Creation Question"
date: 2010-02-10
forum: Desktop Environments
---

### Post by ngrieb on 2010-02-10
I recently have been trying to create a wallpaper slide show like the cosmos wallpaper, but am running into some problems. I have copied the xml format of the cosmos wallpaper and loaded it into the wallpaper manager. The stack/slide show appears there, and looks fine. When I click it I get the first background in the stack, but nothing else ever happens. I have tried to set the delay to very small values in order to quickly see if it is working, but I don't get anything. 

My question is does the xml file need to somehow get compiled in order for this to run? I tried editing the cosmos one (which works btw) by setting the delays to smaller numbers, but it still seemed to change only every 30 min which is the default 1795.0 sec., so it didn't seem to change?

Anyone know what I need to do to get this to work? 

Thanks.

Oh here is the wallpaper code btw:

<background>
  <starttime>
    <year>2010</year>
    <month>01</month>
    <day>00</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <static>
    <duration>60.0</duration>
    <file>/usr/share/backgrounds/DarkLightning/ReflectionsDark.jpg</file>
  </static>
  <transition>
    <duration>0.5</duration>
    <from>/usr/share/backgrounds/DarkLightning/ReflectionsDark.jpg</from>
    <to>/usr/share/backgrounds/DarkLightning/ReflectionsDarkBlue.jpg</to>
  </transition>
  <static>
    <duration>0.5</duration>
    <file>/usr/share/backgrounds/DarkLightning/ReflectionsDarkBlue.jpg</file>
  </static>
  <transition>
    <duration>0.5</duration>
    <from>/usr/share/backgrounds/DarkLightning/ReflectionsDarkBlue.jpg</from>
    <to>/usr/share/backgrounds/DarkLightning/ReflectionsDark.jpg</to>
  </transition>
  <static>
    <duration>60.0</duration>
    <file>/usr/share/backgrounds/DarkLightning/ReflectionsDark.jpg</file>
  </static>
</background>

---

### Post by ydristi on 2010-02-11
if u want wallpaper slideshow then just install desktop drapes .it can be installed via ubuntu software centre

---

### Post by nilarimogard on 2010-02-11
There's an app which does this automatically: [XML Slideshow Creator]("http://www.webupd8.org/2010/02/easily-create-xml-wallpapers-with-xml.html")

---

### Post by ngrieb on 2010-02-11
Why would an editor be any different than what I currently have? I want some durations to be a lot shorter than others on purpose.

I have created/edited the cosmos file and am not worried about user friendliness (it seems like this is just a way to auto-generate the lines of code already available to me). I easily figured out the XML code, and by the looks of it correctly added the wallpaper to the desktop manager. 

I'm just wondering if there is something else I need to do to make the slide show transition at this point.

I attempted to try recompiling libgnome-desktop-2-11 as suggested on another thread, but it seems that I can not because of an unfulfillable dependency. I have noticed that desktop drapes is not able to pick up on the stack I created, but does see cosmos. 

Is there a way reload the desktop images, similar to when you want to load new fonts. A config/reload backgrounds line of some sort?

---

### Post by ngrieb on 2010-02-14
Here is the full stack. I hope that this works for other people, and that you all enjoy it. If you want to change the time between animations all that you would have to change would be the first time setting in the XML file, but feel free to tweak XML files in any other way. (btw, the XML file is set to read from /usr/share/backgrounds/ , so just untar it there). Get back to me if it works for you. 

Thanks.

On another note...does any one know if Windows 7 allows for XML backgrounds? Perhaps I can test it there.

Or not. Sorry, the file is too big. Is there any way to decrease the size of a tar.gz file any more, or split it into chunks of 997 kB or whatever the ridiculous size limit is?

Ok, just grab them here then:

[http://s227.photobucket.com/albums/dd217/gforce6point0/Art%20and%20Photography/UbuntuDarkXMLBackgrounds/](http://s227.photobucket.com/albums/dd217/gforce6point0/Art%20and%20Photography/UbuntuDarkXMLBackgrounds/)

I hope you can get this to work, cause I can do so much with this variable slide time if it does. Feel free to rearrange the stack or make changes to anything.

---

### Post by williamts99 on 2010-12-06
I am using [Cortina Wallpaper Slideshow]("https://help.ubuntu.com/community/Cortina") which uses an FS watcher so any new files added automatically get added.

It works great and doesn't get much easier, oh and you can sync your folders using the likes of ubuntuOne or Dropbox.

---

