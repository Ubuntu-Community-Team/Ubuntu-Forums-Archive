---
title: "Gnome Time/Date applet"
date: 2008-12-25
forum: General Help
---

### Post by IceReaver75 on 2008-12-25
I want to change the look of the time/date applet on the gnome panel.  I know how to edit the string for the format in the configuration editor but not sure how to edit it for what I want to achieve.  I want to have it so the date is on the top line with the time underneath the date.  If anyone can help with how to edit the string to achieve this your help will be appreciated.  Thank you.

I want it to look something like this

Thu Dec 25
 3:00 pm

---

### Post by IceReaver75 on 2008-12-26
Well I didn't get it exactly the way I wanted but I got it to go the other way time on top and the date underneath so I'm happy with that.  I just did a bunch of goggle search and did some reading.

---

### Post by kostkon on 2008-12-26
> **IceReaver75 said:**
> Well I didn't get it exactly the way I wanted but I got it to go the other way time on top and the date underneath so I'm happy with that.  I just did a bunch of goggle search and did some reading.
Could you please share with us how you did it or at least post some source? It looks really nice.

---

### Post by IceReaver75 on 2008-12-26
This is how I did it.  The 2 websites I got the info from are alittle outdated so you don't need the patch they talk about on the one page anymore. The 2 web pages are here:

[http://snuxoll.com/post/2008/11/16/custom-time-format-gnome-panel-clock](http://snuxoll.com/post/2008/11/16/custom-time-format-gnome-panel-clock)
[http://pijulius.blogspot.com/2006/05/gnome-panel-clock-applet-with-markup.html](http://pijulius.blogspot.com/2006/05/gnome-panel-clock-applet-with-markup.html)

the steps i followed were: 

1)first open up the configuration editor and under apps/panel/applets/you will have to find your clock applet its different numbers based on how your panel is set-up

2)when you find the gnome clock applet listing go under that folder and click prefs - right click custom_format and click edit key.  In the value window is were you would type the string for the new format.  My clock is sets as:

<span font_desc="Sans 8" >%I:%M <span font_desc="Sans 8" rise="0">%p</span><span rise="0"> </span>%n<span font_desc="Sans 8" foreground="#999999" ><sup>%a, %d %b '%g</sup></span></span>

then click ok

3)then right click the format listing and click edit key.  Under the value window change it to custom and it shopuld change the look of the clock to the new value you set in step 2

Hopefully this is easy to understand and it helps others who want to do the same

---

### Post by eluminx on 2008-12-28
thats a pretty nice little hack, how did big is your panel tho, because i just tried it on mine and my panel has to be at least 29px for it to display it right.  Now this becomes a problem for those who use a bg for the panel (like i am using).  Nevertheless it is a nice little tutorial, thanks...

---

### Post by IceReaver75 on 2008-12-28
Yeah I have my panel bar set at 30 right now.  

I suppose there is a couple of things you can try in order to use the panel bg that you are using.  Either try a different font size just change the "Sans 8" to like a "Sans 6" and see if you lower the panel size and see if it shows correctly, or you can try to use a different font type and see if it helps just replace the "Sans" with any other type of font you have installed on your system.

The other thing you could do is adjust the bg pic your using for you panel in gimp to the new panel size.  If the bg is scaled for a 24 pix panel just scale the bg in gimp to the new 29 pix height.

---

