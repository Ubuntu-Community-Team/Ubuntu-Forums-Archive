---
title: "Can I show the time in another time zone?"
date: 2008-08-25
forum: Desktop Environments
---

### Post by andrewkk on 2008-08-25
The Clock applet for the Gnome Panel has the ability to store "Locations" and display other timezones in a drop-down window, but not on the panel itself so it doesn't fulfill the role of a clock I can look up at.

Is there a way to display the time in another time zone without having to change the date/time settings for my entire system?

Is there perhaps another program I can use to accomplish this?

---

### Post by TCSnyder on 2008-08-25
There is a screenlets widget that will do that. 

You can get screenlets from GetDeb.net. 
it might not come in the package but any kind of widgets (like google widgets) work in it.

---

### Post by andrewkk on 2008-08-27
Thanks, that looks promising. I haven't found a suitable widget yet, but I'll keep looking. There seems to be an endless supply of these. :)

I wonder, though, if it should really be necessary to run an entire widgets engine just to show the time. It seems like overkill, don't you think?

---

### Post by kaivalagi on 2008-08-27
> **andrewkk said:**
> Thanks, that looks promising. I haven't found a suitable widget yet, but I'll keep looking. There seems to be an endless supply of these. :)

I wonder, though, if it should really be necessary to run an entire widgets engine just to show the time. It seems like overkill, don't you think?

You could use Conky, it's a text outputting tool that "draws" the text onto your desktop as a transparancy. I've attached an example conkyrc file to use with conky which holds part of what I display on my desktop. Also attached a screenshot to give you an idea.

Quick steps to sort it would be something like:

1) install it using: "sudo apt-get install conky"
2) save the attached conkyrc-time.txt file to ~/.conkyrc
3) run conky

Timezones can be found here: [http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones](http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones)

You can edit the conkyrc file to do all sorts but it is limited to font based output, no pictures here...you can alos run multiple instances of conky with multiple conkyrc files.

You can find a heap of knowledge on Conky in the forums, a couple of good places to start are:

[LIST]
[*][HOW TO: A Beginners Guide to Setting up Conky]("http://ubuntuforums.org/showthread.php?t=867076")
[*][Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")
[*][~.conkyrc settings]("http://conky.sourceforge.net/config_settings.html")
[*][Conky Variables]("http://conky.sourceforge.net/variables.html")
[*][Conky Manual]("http://conky.sourceforge.net/docs.html")
[/LIST]

If you get into it you can do other things, take a look at the links in my sig...

Have fun

---

### Post by cinajohn on 2009-10-30
Thanks kaivalagi,

Didn't know how to get conky to display different time zones, the tztime works perfectly.

Thanks again!

---

### Post by Xqua on 2010-10-02
thank you man !

really usefull !

---

### Post by akxiii on 2010-12-27
I am not sure if this addresses your issue but...
on the clock applet it sounds like you have figured out how to add locations, but not display them. This can be accomplished fairly easily.

From the start:
[LIST=1]
[*]*Left* click on the clock
[*]*Right* click on the clock, select **Preferences**
[*]Navigate to the **Locations** tab
[*]Use the **Add** button to add locations
[*]Hit Close when you are finished adding locations
[*]Below the calendar in your clock are the words "Locations" to the left is a plus sign. If you click the plus it will give you a drop down map and current time for cities
[/LIST]

You can set one of the locations as your current time by hover over the right side of the location name and clicking the "set" button that appears.

I hope this helps.
-Knoxy

---

### Post by Dogmatictea on 2011-03-01
Thank you, good sir, for the tztime command! I have a girlfriend in Hawaii and I'm in Korea. Bottom Left and Top Right Conkies contain digital and analog times respectively while the Top Left contains Hawaii time and date.

---

