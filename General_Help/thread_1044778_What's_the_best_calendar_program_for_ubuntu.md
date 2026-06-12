---
title: "What's the best calendar program for ubuntu?"
date: 2009-01-19
forum: General Help
---

### Post by tegnoto89 on 2009-01-19
Preferably a program that allows me to just make notes for a given date as opposed to "appointments".  I tried sunbird which was alright, but does anyone have other suggestions?

---

### Post by adamlau on 2009-01-19
Best means fast and lightweight while remaining usable: Osmo and Orage both fit the description.

---

### Post by Joeb454 on 2009-01-19
> **adamlau said:**
> Best means fast and lightweight while remaining usable: Osmo and Orage both fit the description.

For you possibly.

Best means different things to different people ;)

@OP - I quite like sunbird myself, I've been meaning to give it a try again, I haven't used it properly for a while

---

### Post by OrangeCrate on 2009-01-19
Sunbird is good, and getting better, but I still opt for Google Calendar for day-to-day use.

---

### Post by MikeBrown on 2009-01-23
Perhaps this has been addressed on another forum page (which I haven't found yet), but is it possible to sync Google Calendar with the default calendar (the one on the top panel where it displays the time and weather) in Ubuntu 8.10?

---

### Post by LowSky on 2009-01-23
I actually use Tomboy Notes for all my note taking. I can name them with the date, create subfolders for catagories, and its really easy to use.

---

### Post by TenPlus1 on 2009-01-23
Am using a simple calendar program called Dates that is available in the repo's...  It lets you  setup you own calendar, zoom in and out (hours,days, weeks, months) and displays important dates on the gnome panel calendar...

---

### Post by zvilikestv on 2009-01-31
[Bryan Clark gives directions for subscribing to your Google calendar as a webcalendar]("http://clarkbw.net/blog/2006/12/08/mashing-google-calendar-and-gnome/"). It will appear in the panel, as you want, BUT it is read only. It has been suggested that [gcaldaemon]("http://gcaldaemon.sourceforge.net/usage16.html") will give you the ability to write, but it may require the use of Evolution. I haven't tried it myself.

---

### Post by fragos on 2009-02-01
My favorite light weight calendar is gpe-calendar. Dates uses the Evolution DB so both aps work together. Gpe-calendar uses an sqlite DB that is file compatable with gpe-calendar running on my Nokia N810. On the N810 there is a Google Calendar synchronization package called erminig.

---

### Post by mikjp on 2009-02-02
Emacs can do anything :-)

mikko

---

### Post by 666f6f on 2010-03-13
> **TenPlus1 said:**
> Am using a simple calendar program called Dates that is available in the repo's...  It lets you  setup you own calendar, zoom in and out (hours,days, weeks, months) and displays important dates on the gnome panel calendar...

I just installed [Dates]("http://www.pimlico-project.org/dates.html") and I think it's fantastic, thank you for the suggestion! Some remarks..
[LIST=1]
[*]It's very very light, as it is designed for hand-held devices.
[*]It integrates into Gnome, as it uses the [Evolution Data Server Architecture]("http://www.google.com/search?q=Evolution+Data+Server+Architecture").
[/LIST]

There also exist [Tasks]("http://www.pimlico-project.org/tasks.html"), [Contacts]("http://www.pimlico-project.org/contacts.html") and [Sync]("http://www.pimlico-project.org/sync.html") in the same spirit.

P.S. just discovered that version 0.4.8 does not support recurring events..

---

### Post by 666f6f on 2010-04-29
I just noticed that you can change the calendar/tasks application that launches after you click on the Edit button in the gnome-clock (part of the gnome-panel package).

```

gconftool -t stirng -s /desktop/gnome/applications/tasks/exec "tasks"
gconftool -t stirng -s /desktop/gnome/applications/calendar/exec "dates"

```

Not sure how to do it via the GUI (a preferences dialog or something similar).

---

### Post by fragos on 2010-04-29
> **666f6f said:**
> 
Not sure how to do it via the GUI (a preferences dialog or something similar).

Right click the time display in the applet bar and select Preferences, as you thought. The rest is self explanatory. You'll also find you can display the weather and a set of location times.

---

### Post by 666f6f on 2010-04-29
> **fragos said:**
> Right click the time display in the applet bar and select Preferences, as you thought. The rest is self explanatory. You'll also find you can display the weather and a set of location times.

I must be missing something here. I have already setup weather information but did not find a way to change the calendar/tasks programs. To find this *trick* I had a quick look at the code in gnome-applet package (after I stumbled up on [Bug#384783]("https://bugzilla.gnome.org/show_bug.cgi?id=384783")). Have you actually done this? If so, how exactly?

---

### Post by fragos on 2010-04-29
double click on any day in the month calendar displayed by the applet and you get an Evolution window to set appointments. In the bottom left of that window are icons for mail, tasks and etal.

---

### Post by golanbatrac on 2010-04-29
I'll second osmo.  Great little program.

---

### Post by 666f6f on 2010-04-29
> **fragos said:**
> double click on any day in the month calendar displayed by the applet and you get an Evolution window to set appointments. In the bottom left of that window are icons for mail, tasks and etal.

Great, thanks! My original point, which I didn't manage to explain it properly, was that **you can use whatever app you want to edit appointments/tasks** from the clock applet and not just evolution. For example you can use the dates and tasks programs (yes they are programs!) or osmo.

---

