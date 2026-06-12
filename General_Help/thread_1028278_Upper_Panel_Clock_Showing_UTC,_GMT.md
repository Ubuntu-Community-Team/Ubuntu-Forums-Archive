---
title: "Upper Panel Clock Showing UTC, GMT"
date: 2009-01-02
forum: General Help
---

### Post by PBK on 2009-01-02
On a previous Ubuntu Gnome version I have added a second clock to my upper panel and changed it to show the time in GMT (or UTC) via the Preferences sub menu. That way I had two clocks; One to show local time, one for UTC. I seem to remember having a check box option in Preferences to show GMT time, but haven't seen that option for at least the past two releases after a fresh install. The one computer where I upgraded from older versions to the next version still has the one clock indicating GMT but no option found to change it.

  Am I just not looking in the right place, or is this a lost feature? Thanks for your time!

Paul

OK - In case anyone else may want to do this, I found the file which can be manually edited. I guess a GUI selection is missing or something. Look in this directory:

/home/~/.gconf/apps/panel/applets

  ...and depending on when the clock was added, you can go into applet_1, applet_2, etc to see if it contains the config directory for the clock's %25gconf.xml file and change the line:

<entry name="gmt_time" mtime="1231016427" schema="/schemas/apps/clock_applet/prefs/gmt_time"/>

to

<entry name="gmt_time" mtime="1231016427" schema="/schemas/apps/clock_applet/prefs/gmt_time" type="bool" value="true"> </entry>

  At least modify the end of the line to enable the GMT option. I'll say at least mtime will be different from what you see above. You may need to restart your session.

HTH

---

### Post by kokkus on 2009-01-02
Take a look under Administrator > time and date

---

### Post by PBK on 2009-01-02
Thanks Kokkus. I believe the admin/Date-time might change all clocks. I need one clock showing local time, second clock showing UTC. When I look at the help file for the clock, it references UTC:

<QUOTE>
Show seconds
    Select this option to display seconds in the applet.
Show date
    Select this option to display the date in the applet.
Use UTC
    Select this option to display Universal Coordinated Time, also known as Greenwich Mean Time, in the applet.
</QUOTE>

  There are other options, too, that don't show up; UNIX, Internet time, But these options are not on my preferences window.

---

### Post by PBK on 2009-01-02
.

---

### Post by -kg- on 2009-01-02
Well, lacking the checkbox to set one of the clocks to GMT, you could alternatively pull up the Preferences, click on the Locations tab, click on "Add" and then select a city that is in the GMT timezone.  That would effectively set that clock to GMT time.

<edit>

> Show seconds
Select this option to display seconds in the applet.
Show date
Select this option to display the date in the applet.
Use UTC
Select this option to display Universal Coordinated Time, also known as Greenwich Mean Time, in the applet.

I just read that section in the help files also.  It fits absolutely *nothing* in the actual Preferences window!  I don't know what's going on, but it seems that someone upgraded the software without upgrading the help files.

---

### Post by PBK on 2009-01-03
> **-kg- said:**
> Well, lacking the checkbox to set one of the clocks to GMT, you could alternatively pull up the Preferences, click on the Locations tab, click on "Add" and then select a city that is in the GMT timezone.  That would effectively set that clock to GMT time.
>>>>


  Thanks KG. When I add a GMT timed location, it doesn't change the time, but if I left-click on that clock and then click on "Locations", I can see the GMT time in the lower window. I can click on the icon in that lower right window location, but that assumes the whole system is at that location and changes both clocks to GMT.

 I think I am going to try locate the clock's config file on the one system that grandfathered in the GMT time selection.

---

