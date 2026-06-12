---
title: "Cannot see the wheather and temperature in the gnome top bar"
date: 2008-12-08
forum: General Help
---

### Post by fjf on 2008-12-08
..You know, just before the date and time.  It got lost when I installed Ibex (ubuntustudio flavor) and never got it back.  Anyone knows the trick?.

Edit:  OMG I misspelled the title, but I cannot change it to weather! ;)

---

### Post by DieB on 2008-12-08
might be due to the city-namings changed a bit.

You are sure u set up a correct place? (as for me it didn't tfind the place so i had to go top down, like typing Germany,... to get a list of towns)

---

### Post by eternalnewbee on 2008-12-08
How about right-clicking on the panel and choosing Add to Panel?

---

### Post by fjf on 2008-12-08
I have the clock and calendar applet.  It just does not displays the weather and temperature.  I just tried to change location.  Nothing.

---

### Post by DieB on 2008-12-08
sorry for dumbass question, but u enabled show weather? and got your town/place from list of offer ones that pop up if u start typing letters?

---

### Post by eternalnewbee on 2008-12-08
> I have the clock and calendar applet. It just does not displays the weather and temperature. I just tried to change location. Nothing
You mean Clock Preferences doesn't appear?

---

### Post by AndyCooll on 2008-12-08
Right click on the applet and under options select your hometown from those listed (if you've got some settings already in place, remove them). If you are choosing more than one, set one of them as default. 

For me I found that only having a hometown from those pre-listed brought up weather details. Even though there is an option to input your own details, and this function works, I then didn't have any weather details. So I restarted from scratch and selected the nearest location.

:cool:

---

### Post by fjf on 2008-12-08
I have enabled it in preferences, choosing ine of the alternative cities offered in my country.  Nothing appears!.

---

### Post by frankleeee on 2008-12-08
You have to set the time and date to your closest area/ or time zone in administration, (you don't have to set the synchronization with the web) if I remember correctly this is what synced the information with the clock information for me.

---

### Post by fjf on 2008-12-08
Done that, no luck!

---

### Post by hwttdz on 2008-12-08
I experienced this too.  I found that if you add a weather applet, separate from the clock applet it worked.  Know it's not what you're looking for (or what I was), but I found it a rather acceptable workaround.

So I turned off weather in the clock applet.  Then select add to panel, weather applet.  And set that up as you would expect.

---

### Post by frankleeee on 2008-12-08
> **fjf said:**
> Done that, no luck!

After setting the time date did you go back to the clock and set the city again in preferences-location, mine reads as the city I am in and the closest time zone
Portland America/Los-Angeles.

---

### Post by fjf on 2008-12-08
Yes.  When I unset it and then set it again, the width of the applet increases a bit, as if it tries to display it, but it cant.
If there is no other way, I will install the weather applet.

---

### Post by frankleeee on 2008-12-08
> **fjf said:**
> Yes.  When I unset it and then set it again, the width of the applet increases a bit, as if it tries to display it, but it cant.
If there is no other way, I will install the weather applet.

The add to panel applet works fine try a restart to sync the set up it does need a short time to update I think your home free it will probably show shortly but a restart may kick it in. Make sure you tick the show weather/temp in the preferences of the clock on off on, I have noticed with the Intrepid upgrade on my desktop that if I add a new program say like the opera browser that it showed as being in the menu edit as being installed but not in the drop down until I ticked it off then on in menu edit.

---

### Post by hwttdz on 2009-02-05
Another possible solution:

sudo dpkg-reconfigure tzdata
killall gnome-panel

The gnome-panel auto restarts so that's all you need to do. The first command reconfigures the timezone data, don't know how exactly that's linked to the weather. Principally posting so that when I change my location and break it again, I can find the solution!

---

