---
title: "Desktop Background no longer working on Intrepid"
date: 2008-12-14
forum: General Help
---

### Post by mholland on 2008-12-14
I am fairly new to Ubuntu and recently when from 8.04 (Hardy) to 8.10 (Intrepid) to resolve some conflicts I was having with some of my hardware not working. Creative sound card and ATI video... Fortuneately they work great now except for one caveat. When ubuntu opens and accepts my logon credetials I see the background I have selected for a very brief period then the desktop reverts  back to a solid color or gradient.. Depending on how the colors were set up for a specific background. Really strange it is. I can bring up the change background dialog and select different backgrounds. The only thing that changes is the background color and a picture is never displayed.. I doubt its the graphics card cause I can set the appearance effects to extra and run 3D applications with no issues.

Any help would be much appreciated.. Thanks

---

### Post by blazemore on 2008-12-14
One hack that could work is to make a new user, then copy your files across.

For a proper route, Nautilus is the program in charge of drawing the wallpaper by default. it sounds as if it isn't loading properly. Can you browse your computer with the file manager ok?

If not, then open a terminal, type nautius and hit Enter. Then post the results here.

---

### Post by mholland on 2008-12-14
Upon typing nautilus in the terminal it opened up my home directory in File Browser.

---

### Post by Therion on 2008-12-14
If you right-click on a blank space on your desktop and click on one of the wallpapers shown, to set it as the new default, does the problem persist?

It sounds like the wallpaper you've chosen may have been moved from it's original location.

---

### Post by mholland on 2008-12-14
Problem still persists. Removed the pictures and re-added. When the computer boots and ubuntu first logs in it shows the picture for a brief period before the panels appear. As soon as panels appear the background disappears... Weird.

---

### Post by sedawk on 2008-12-14
I had some trouble with the background being black instead of
showing my wallpaper in approx. 90% of the time (Ubuntu 8.04).

Does changing the wallpaper to some other picture help?
What about using gimp and resizing or reformating
the picture (e.g. to fit exact screen size in pixel).

(I used the default wallpaper of 8.04 and now the
 new one from 8.10 - I'm not sure I ever got a black
 background with the image from 8.10 ...)

---

### Post by mholland on 2008-12-14
Scaled image in gimp to 1680x1050 .. What my current resolution is. Same issue, is there a way to assign the background via console?

---

### Post by blazemore on 2008-12-15
```
sudo gconf-editor
```
Have a look in there for desktop background related tomfoolery.
I still think making a new user acc is the way to go.

---

### Post by dawbomb on 2008-12-23
I have the same problem, and am unwilling to create a new user profile, because then I have to reconfigure pidgin, amarok, thunderbird, firefox, sunbird etc from scratch...

---

### Post by WebBuddha on 2008-12-28
Hi there,

I want to let you know that I've got exactly the same issues on my side.
My resolution is also 1680x1050.
I can't find the solution myself.

Regards
WebBuddha

---

### Post by WebBuddha on 2009-01-04
nobody here with any solutions on this issue?

---

### Post by freedryk on 2009-01-08
Same problem here.  I managed to fix it by manually editing the .gconf/desktop/gnome/background/%gconf.xml file and changing the line:

<entry name="draw_background" mtime="1231222661" type="bool" value="false">

to value="true".  Then I rebooted and it was fixed, though I expect logging out or killing nautilus would work as well.  The strange thing was that when I used gconf-editor to look at the desktop/gnome/background settings, the "draw background" setting was checked, even though it was set to "false" in the xml file.  gconf-editor bug?

---

### Post by WebBuddha on 2009-01-09
thanks for the hind.
I've tried the change that you've discribed, but it wasn't for me.
my gconf.xml looks like this:
> <?xml version="1.0"?>
<gconf>
        <entry name="secondary_color" mtime="1231523065" type="string">
                <stringvalue>#dadab0b08282</stringvalue>
        </entry>
        <entry name="color_shading_type" mtime="1231523065" type="string">
                <stringvalue>solid</stringvalue>
        </entry>
        <entry name="primary_color" mtime="1231523065" type="string">
                <stringvalue>#afdc9227719c</stringvalue>
        </entry>
        <entry name="draw_background" mtime="1230064565" type="bool" value="true">
        </entry>
        <entry name="picture_filename" mtime="1231529024" type="string">
                <stringvalue>/home/maggus/Pictures/Wallpapers/katie-holmes-1680x1050-29998.jpg</stringvalue>
        </entry>
        <entry name="picture_options" mtime="1231523065" type="string">
                <stringvalue>none</stringvalue>
        </entry>
</gconf>

---

### Post by WebBuddha on 2009-01-16
I've logged in with an different user and that is still working fine. I'm able to change my backgrounds all night long ;-)
So it must be an "user" problem.

Any ideas from your side...creating an new one is not really an idea.

---

### Post by fishz on 2009-02-10
I had the same issue on a 1280x600 resolution netbook. I'm guessing that resolution and graphics drivers aren't the issue. Changing specific background pictures didn't help. Only the solid colour was drawn.

I fired up gconf-editor and found the draw background checkbox unchecked. Checking  it seems to have done the trick immediately.

I've shutdown and restarted and the setting remains in place so it looks like things are back to normal.

---

