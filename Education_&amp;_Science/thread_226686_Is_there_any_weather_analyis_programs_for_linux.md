---
title: "Is there any weather analyis programs for linux?"
date: 2006-07-31
forum: Education &amp; Science
---

### Post by dmb on 2006-07-31
I was just wondering if there is any weather programs for linux. It seems like theres a handfull for windows, but not linux.  I just want a program that i can play that deals with NOAA data. Does one exists?

---

### Post by s_h_a_d_o_w_s on 2006-08-01
Not sure what noaa is, but gdesklets has some desklets. So does superkaramba, if you're running kde

---

### Post by mips on 2006-08-01
As far as I know the NOAA runs on a massive linux cluster.

Linux has a lot of scientific software so if you can tell us a bit more about what you want to do maybe we can point you in the right direction.

You could also contact noaa or do a google search for linux weather software as it has lots of hits.

[http://www.weather-display.com/index.php](http://www.weather-display.com/index.php) and I'm sure there are countless others.

Also maybe post here:
[http://www.ubuntuforums.org/showthread.php?t=29919](http://www.ubuntuforums.org/showthread.php?t=29919)
See associated thread: [http://www.ubuntuforums.org/showthread.php?t=142557](http://www.ubuntuforums.org/showthread.php?t=142557)

---

### Post by RAV TUX on 2006-08-01
> **s_h_a_d_o_w_s said:**
> Not sure what noaa is, but gdesklets has some desklets. So does superkaramba, if you're running kde

NOAA

National Oceanic and Atmospheric Administration

[http://www.weather.gov/](http://www.weather.gov/)

> **National Weather Service Mission Statement**                                

            **" * The National Weather Service (NWS) provides weather, hydrologic,                and climate forecasts and warnings for the United States, its territories,                adjacent waters and ocean areas, for the protection of life and                property and the enhancement of the national economy. NWS data and                products form a national information database and infrastructure                which can be used by other governmental agencies, the private sector,                the public, and the global community.* "**
 
NOAA's National Service:

> **NWS STRATEGIC PLANNING AND POLICY**

  The Strategic Planning and Policy Office provides support to the Assistant Administrator for Weather Services and Deputy Assistant Administrator through the development and implementation of an integrated approach to NWS policy,  strategy, and long-range planning processes. The Office develops NWS-wide  long-range policy objectives and develops and manages the NWS strategic planning process through implementation. The Office develops and recommends policy on NWS and private sector roles, activities, and relationships. 

 
now with that cleared up I am still unsure what you are looking for?

---

### Post by YukonGuy on 2006-09-05
Hello,

Like dmb, I am looking for weather analysis (Similar to Digital Atmosphere) programs or suites.  Are there any Debian packages containing such software?  I am not looking for an applet, desklet, Firefox extenstion or any other such that shows local weather conditions.  I can't seem to locate any in all of the repositories that I have checked.

This next statement may cause shock for serious Linux users but, what's life without excitement? [-(  *I don't want to have to learn how to compile, make, build or what other types of commands there are out there*. ](*,)  I guess I will if I have to but, my interests in using Linux and in particular Ubuntu Linux are not as a developer of weather software but as a user.  ;) 

I am enjoying Ubuntu 6.06 LTS.  I was one of the victims of the X window update.  That was a pain! :eek:  I'd like to avoid those kinds of problems as I find them distracting and time consuming.  I'm looking for something that works.  That's why I'm using Ubuntu.

Regards,

YukonGuy

---

### Post by mips on 2006-09-05
I'm sure there are lots but just elusive to find.

I found this, [http://strc.comet.ucar.edu/index.htm](http://strc.comet.ucar.edu/index.htm)

[http://www.unidata.ucar.edu/software/gempak/](http://www.unidata.ucar.edu/software/gempak/) Gempak is free and the DA crowd seem to recommend it for Linux.
[http://sky.radioweather.us/gempak.html](http://sky.radioweather.us/gempak.html)
[http://www.weathergraphics.com/forum/index.php](http://www.weathergraphics.com/forum/index.php) might point you in the right direction. Saw something there that there might be a DA port for Linux. Just do a search for 'linux' in their forums'
[http://www.stormlab.net/meteos/meteos.html](http://www.stormlab.net/meteos/meteos.html)


I also found a few commercial apps. Some so advanced you will need a cluster to run it on.

---

### Post by YukonGuy on 2006-09-06
Hi mips,

Thank you for the research that you've done.  I'll take a look at the links that you've suggested.  A cluster would be nice!  I'm looking for something that will run on a single PC.

Thank you again for your assistance.

Regards,

YukonGuy

---

### Post by P_Badger on 2006-10-16
> **mips said:**
> I'm sure there are lots but just elusive to find.

I found this, [http://strc.comet.ucar.edu/index.htm](http://strc.comet.ucar.edu/index.htm)

[http://www.unidata.ucar.edu/software/gempak/](http://www.unidata.ucar.edu/software/gempak/) Gempak is free and the DA crowd seem to recommend it for Linux.
[http://sky.radioweather.us/gempak.html](http://sky.radioweather.us/gempak.html)
[http://www.weathergraphics.com/forum/index.php](http://www.weathergraphics.com/forum/index.php) might point you in the right direction. Saw something there that there might be a DA port for Linux. Just do a search for 'linux' in their forums'
[http://www.stormlab.net/meteos/meteos.html](http://www.stormlab.net/meteos/meteos.html)


I also found a few commercial apps. Some so advanced you will need a cluster to run it on.


Well, I've spent well near the past week tearing up the 'net looking for good weather forecast apps, and I haven't done too well in my search. The crown jewel of forecast apps, Gempak, requires you be a computer engineer to install. ; P Probably why there's a small handful of people who charge a pretty penny to install gempak on your system, and one of them is in the UAE. 

I found one nifty little NEXRAD viewer called PyRadar, but the programmer abandoned the proggy when the NOAA changed the format of how their site handles their weather data.

The NOAA has a java weather viewer, but it's a bit of a mess to use.

---

### Post by mips on 2006-10-16
I've never tried to install Gempak. Don't they have a .deb available ?

---

### Post by P_Badger on 2006-10-16
> **mips said:**
> I've never tried to install Gempak. Don't they have a .deb available ?

Nope, not that I could see. All I found was a "linux" distro in .tar format. And the installation instructions were pretty weak.

---

### Post by kleeman on 2006-10-16
Why do you need an application? Have a look at this site:

[http://weather.unisys.com/index.html](http://weather.unisys.com/index.html)

It is pretty comprehensive from a technical viewpoint.
What exactly are you trying to do? I am a climate/weather scientist so use a huge variety of such software but you need to be more specific.....

---

### Post by baslin6 on 2007-02-12
> **P_Badger said:**
> Well, I've spent well near the past week tearing up the 'net looking for good weather forecast apps, and I haven't done too well in my search. The crown jewel of forecast apps, Gempak, requires you be a computer engineer to install. ; P Probably why there's a small handful of people who charge a pretty penny to install gempak on your system, and one of them is in the UAE. 

I found one nifty little NEXRAD viewer called PyRadar, but the programmer abandoned the proggy when the NOAA changed the format of how their site handles their weather data.

The NOAA has a java weather viewer, but it's a bit of a mess to use.

I am a ham operator and act as net control operator for Skywarn nets.  This puts me in the same room with the NWS forecasters, and I get to view their workstations.  Our local NWSFO runs linux on their workstations, but I don't know if the apps are running remotely or are installed on each workstation.  I will ask some of the guys in the local office for the lowdown and I'll pass along my findings.

---

### Post by mips on 2007-02-12
> **baslin6 said:**
> I will ask some of the guys in the local office for the lowdown and I'll pass along my findings.

That would be nice, thx.

---

### Post by ShirishAg75 on 2007-02-16
As a casual user, I use this FF extension  [http://users.rcn.com/shoofy/forecastfox_enhanced/](http://users.rcn.com/shoofy/forecastfox_enhanced/) & it works for me :)

---

### Post by mips on 2007-02-16
> **shirishag75 said:**
> As a casual user, I use this FF extension  [http://users.rcn.com/shoofy/forecastfox_enhanced/](http://users.rcn.com/shoofy/forecastfox_enhanced/) & it works for me :)

Thats for the average joe but cannot be classified a 'weather analysis' application.

---

### Post by mips on 2008-08-28
Any more suggestions?

---

### Post by xadder on 2008-09-01
As Kleeman said, you have to be specific. The NCAR site for example lists 10s of sites with free software for looking at met data. It is hard to recommend anything though until we know what you want.

---

### Post by chrisjmyers1204 on 2008-12-11
I've been looking for something similar to Weather Watcher Live, but i guess i don't really know the right terms or words to use during a search.
[http://www.singerscreations.com/Weather-Watcher-Live.asp]("http://www.singerscreations.com/Weather-Watcher-Live.asp")

---

