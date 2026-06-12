---
title: "Gdesklet Weather Sensor Problem?

I'm getting"
date: 2006-07-14
forum: Desktop Environments
---

### Post by T_W on 2006-07-14
I'm running GDesklets 0.35.3 on Ubuntu 6.06 (Dapper).  Everything was installed via apt-get (GDesklets and GDesklets-Data)

I'm getting "Retrieval Failed" on the lt Weather display.

I took a look at the Weather sensor source code. It look like the format of the Yahoo weather page changed in a way that broke the sensor.  A "view source" on the Yahoo weather page looks diferent than the regexs in the sensor. For example the sensor has font tags througout it and it looks like the Yahoo page is using CSS.

This used to work but broke within the last few days. Anyone else having problems with the Weather sensor?

---

### Post by jordilin on 2006-07-14
Me too. I can't get updates, it says Retrieval Failed :( but I don't know the solution to solve it. The problem I think comes from the weather server

---

### Post by lobstaj on 2006-07-16
Hi there,

I have the same problem. I haven't looked at the page source yet, but have also thought that that kind of problem is the most likely. (And if you have even checked that, we are half way at the solution.)

If somebody who's good at regexps reads this and also misses the weather situation on his/her desktop, please help!

If one day I have time, I can also take a look at it. But it'll take some time, also because I'm not very good at regexps.

Let's hope it'll be fixed soon!

---

### Post by orb9220 on 2006-07-16
gDesklets that have been using weather use yahoo weather for info a few days ago it seems yahoo changed thier layout which also broke the widgets.

You just have to wait to see if gdesklets can and will fix and release new affected widgets.

---

### Post by ayoli on 2006-07-16
i use iWeather desklet and i works nice, but i've downloaded it from old gdesklets site (gdesklets.gnomedesktop.org) which is closed and this desklet isn't listed on the gdesklets.org site.

i 'll post the tarball if i find it.
regards.

---

### Post by cbudden on 2006-07-16
> **ayoli said:**
> i use iWeather desklet and i works nice, but i've downloaded it from old gdesklets site (gdesklets.gnomedesktop.org) which is closed and this desklet isn't listed on the gdesklets.org site.

i 'll post the tarball if i find it.
regards.

Could you please post the tarball you got of it please.

---

### Post by orb9220 on 2006-07-16
Yes ! Yes! ayoli Please

Everyone Chant Now: 

"Post the Tarball!","Post the Tarball!","Post the Tarball!"

"I sacrficed one Microsoft Employee to the Goddess Ubuntu"

"Did it Work?"

---

### Post by ayoli on 2006-07-16
ok :)
i didnt find the orignal tarball, and its not available on gdesklets.org so here is my iweather Display and Sensor picked fom my ~/.gdesklets dir.
so grab the [**tarball**]("http://ayozone.org/files/iWeather_0.1-ayo.tar.gz") then,
```
cd ~/.gdesklets
tar xzvf /path/where/you/download/tarball
```
then have a look in the gdesklets shell.
hope it helps (and works),
regards.

---

### Post by orb9220 on 2006-07-16
Thanks I installed with gDesklets shell said it installed correctlly then when I double-click iWeather or iWeatherBig I get 

Could not find sensor 'iWeather'
/home/orb/.gdesklets/Displays/iWeather/iWeather.display

even tho I looked and it is there.

I'll keep trying and thanks for the tarball

---

### Post by ayoli on 2006-07-16
hmm, maybe a pb of permissions, owner ? it says it couldn find sensor, does the .py ssripts are executables ?
```
[23:42:36@ayoli.zone]:~ >$ ll .gdesklets/Sensors/iWeather/*.py
total 60K
-rwxr-xr-x 1 ayoli users 9,7K 2004-05-26 18:49 __init__.py
-rwxr-xr-x 1 ayoli users  12K 2004-05-24 21:16 xmltramp.py
```
regards.

---

### Post by cbudden on 2006-07-16
Works great for me thanks.  Now I need to find my location code!

---

### Post by orb9220 on 2006-07-16
Not me have installed by tar method then by gdesklets intall package and always get this errot after everything installs and says succesufully.

Runtime Error
/home/orb/.gdesklets/Displays/iWeather/iWeather.display


list index out of range                                                              
/usr/lib/gdesklets/utils/ErrorFormatter.py                                           
   37                   hasattr(exc_value, "lineno")):                               
   38                 filename = exc_value.filename                                  
   39                 lineno = exc_value.lineno                                      
   40             else:                                                              
   41                 tbs = traceback.extract_tb(exc_tb)                             
>  42                 filename = tbs[-1][0]                                          
   43                 lineno = tbs[-1][1]                                            
   44                 del tbs                                                        
   45                                                                                
   46         # print error message                                                  
   47         out = "\n"                                                             
   48         out += "[EXC]%s\n" % str(exc_value)

---

### Post by ayoli on 2006-07-17
maybe i missed a file or something, i'll check later.
edit: strange that it works for one, not for the other ....hmm
regards.

---

### Post by ayoli on 2006-07-17
> **cbudden said:**
> Works great for me thanks.  Now I need to find my location code!
go to weather.com enter your town,vcountry and ok, then you'll see your code in the URL
regards.

---

### Post by l080 on 2006-07-20
-argh-
deleted

---

### Post by shane2peru on 2006-07-22
Worked for me, HOWEVER it is **NOT** under the weather.  It is under the uncategorized.  If you look you will find it.  Thanks!

Shane

---

### Post by raja on 2006-07-25
Great to have weather back on my desktop. Thanks for the tarball.

---

### Post by Rich3077 on 2006-07-28
Thanks, works great! :)

---

### Post by yetanothersteve on 2006-07-29
My solution, since I only wanted a weather desklet to view the weather forecast from where I want to live, was to install adesklets and the weather forecast desklet. adesklets weather forecast is using weather.com as the source.

I already have Weather Report added to my Panel and I use that for local weather.

If I was interested in additional desklets, I would probably look into installing a newer or updated version of gdesklet via checkinstall.

Just my $.02, I am not trying to start an adesklet versus gdesklet argument.

---

### Post by endlesssnowfall on 2006-08-03
> **orb9220 said:**
> Thanks I installed with gDesklets shell said it installed correctlly then when I double-click iWeather or iWeatherBig I get 

Could not find sensor 'iWeather'
/home/orb/.gdesklets/Displays/iWeather/iWeather.display

even tho I looked and it is there.

I'll keep trying and thanks for the tarball

I'm having the same problem...how do I fix this?  Thanks.

---

### Post by jordi122 on 2006-08-03
Hello to everybody, sorry about my english

This problem happened to me, and I have been succesful doing this.

1-Extract the tarball to /home/user/.gdesklets (be careful with the automatic folder that file-roller creates)

2-Install the tarball with Gdesklets shell

and... it worked
I am sure that this is not the best way, but if anybody understands what is the problem now...
I think that the forlder "Sensors" was not there when I installed only by the gdesklet shell..

I hope it helps, Fins un altre (See you)

---

### Post by endlesssnowfall on 2006-08-03
Thank you for the help, it works perfectly now!

---

### Post by endlesssnowfall on 2006-08-03
Thank you for the help, it works perfectly now!

---

### Post by Servus on 2006-08-30
It works! For europen cities you have to: 
open [www.weather.com](www.weather.com)
search for your town
look on the address bar: there should be something like ITX0084 or FTX03345. That is the code you have to insert in the box of the desklets.

---

### Post by eeefresh on 2006-09-16
> **jordi122 said:**
> Hello to everybody, sorry about my english

This problem happened to me, and I have been succesful doing this.

1-Extract the tarball to /home/user/.gdesklets (be careful with the automatic folder that file-roller creates)

2-Install the tarball with Gdesklets shell

and... it worked
I am sure that this is not the best way, but if anybody understands what is the problem now...
I think that the forlder "Sensors" was not there when I installed only by the gdesklet shell..

I hope it helps, Fins un altre (See you)

This doesn't seem to be working for me. Any suggestions?

Could not find sensor 'iWeather'
/home/doug/.gdesklets/Displays/iWeather/iWeatherBig.display



A sensor could not be found. This usually means that it has not been installed.

---

### Post by ayoli on 2006-09-16
all is in the tarball, how did you extract it ? i recommend this method in a terminal, do:
```
cd ~/.gdesklets
```
then:
```
tar xzvf /path/where/you/download/iWeather_0.1-ayo.tar.gz
```
then maybe restart gdesklets, and have a look under "uncategorized", should be here and should work(tested few weeks ago on my wife's laptop).

---

### Post by eeefresh on 2006-09-16
Okay, I am still an Ubuntu noob, so please bear with me...

I downloaded the tarball to my desktop, then extracted it with archive manager to /home/doug/.gdesklets, where "doug" is my user name.  The folder didn't exist until I created it.  

Then I ran this in terminal:

cd ~/.gdesklets
tar xzvf /home/doug/.gdesklets/iWeather_0.1-ayo.tar.gz

and got this:

[email]doug@ubuntu-laptop:~/.gdes[/email]klets$ tar xzvf /home/doug/.gdesklets/iWeather_0.1-ayo.tar.gz
tar: /home/doug/.gdesklets/iWeather_0.1-ayo.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Inside the /home/doug/.gdesklets directory I have both a copy of the tarball and the unzipped files contained with in it...but neither seems to work.

I'm certain it's a rookie mistake, since I an still getting used to terminal and Ubuntu file system...

---

### Post by ayoli on 2006-09-16
if the tar.gz is on your Desktop the right command to run will be

1:
```
cd ~/.gdesklets
```
2:
```
tar xzvf ~/Desktop/iWeather_0.1-ayo.tar.gz
```

---

### Post by eeefresh on 2006-09-16
That worked!  Thans ayoli!

---

### Post by ayoli on 2006-09-16
> **eeefresh said:**
> That worked!  Thans ayoli!
youre welcome :)

---

### Post by jazzhaus on 2006-09-19
Is who sloved this problem by anyother method??
I could use iweather sensor by upper advice but, i want use other simply weather widget !!!
Isn't it sloving method by using [www.yahoo.com](www.yahoo.com) weather sourse for Weather sensor or
Lt candy weather sensor inside Gdesklets Package ?
please help me~~

---

### Post by T_W on 2006-09-22
[SIZE="4"]A solution!!!!!![/SIZE]

[URL="http://www.gdesklets.org/?mod=project/uview&pid=49"]
http://www.gdesklets.org/?mod=project/uview&pid=49[/URL]

levellord updates the Yahoo Weather Sensor.

Download and untar into your home dir (the archive contains the .gdesklets dir).

---

### Post by jason.b.c on 2006-09-22
> **T_W said:**
> [SIZE="4"]A solution!!!!!![/SIZE]

[URL="http://www.gdesklets.org/?mod=project/uview&pid=49"]
http://www.gdesklets.org/?mod=project/uview&pid=49[/URL]

levellord updates the Yahoo Weather Sensor.

Download and untar into your home dir (the archive contains the .gdesklets dir).

Awesome.! , But uh.? How do you install it then..? , You didn't mention that part..:confused:

---

### Post by T_W on 2006-09-22
[LIST=1]
[*]Click on link
[*]Right click on "Download latest Release"
[*]Select "Save Link As" and save to desktop
[*]After download, double click to open with file-roller (aka "Archive Manager")
[*]Extract contents to your home directory (all the files will go into your .gdesklets dir in your home dir)
[*]Restart the broken weather desklet
[/LIST]

Weather should be working again.

---

### Post by nwgray on 2006-09-22
Works like a champ now!

Thx

---

### Post by jason.b.c on 2006-09-22
> **T_W said:**
> [LIST=1]
[*]Click on link
[*]Right click on "Download latest Release"
[*]Select "Save Link As" and save to desktop
[*]After download, double click to open with file-roller (aka "Archive Manager")
[*]Extract contents to your home directory (all the files will go into your .gdesklets dir in your home dir)
[*]Restart the broken weather desklet
[/LIST]

Weather should be working again.

Just **/home** directory..?? Or **/home/jason/** *"something specific"*

I'm worried that it's going to extract there and do nothing but take up space..

---

### Post by jason.b.c on 2006-09-22
> **T_W said:**
> [LIST=1]
[*]Click on link
[*]Right click on "Download latest Release"
[*]Select "Save Link As" and save to desktop
[*]After download, double click to open with file-roller (aka "Archive Manager")
[*]Extract contents to your home directory (all the files will go into your .gdesklets dir in your home dir)
[*]Restart the broken weather desklet
[/LIST]



> **Weather should be working again.**

Nope..

How did you get it to work..??  Here's the error message i get:

**COULD NOT FIND SENSOR** *"Weather"* */home/jason/.gdesklets/display's/lt-desklet/weather.display*
*A sensor could not be found.! Usually this means it is not installed.*

But i did install it , I extracted the files exactly the way described above...

What did i do wrong..?

---

### Post by T_W on 2006-09-23
The **/home/jason/** directory.

If you take a look in **/home/jason/.gdesklets/Sensors**, you should see a directory named **Weather**.  Look in that directory and you should see a file named **ChangeLog.**  The top of the **ChangeLog** should say:

```

2006-08-09 Levellord <l8er@gmx.de>

        * __init.py:
        adjusted to the new Yahoo site layout.
```

---

### Post by jason.b.c on 2006-09-24
> **T_W said:**
> The **/home/jason/** directory.

If you take a look in **/home/jason/.gdesklets/Sensors**, you should see a directory named **Weather**.  Look in that directory and you should see a file named **ChangeLog.**  The top of the **ChangeLog** should say:

```

2006-08-09 Levellord <l8er@gmx.de>

        * __init.py:
        adjusted to the new Yahoo site layout.
```


Well that changelog does exist , It has all of that you showed me above...

But it still dosen't work...:mad: 

I'm still getting that same error message:

```
**COULD NOT FIND SENSOR "Weather"** [I]/home/jason/.gdesklets/display's/lt-desklet/weather.display
A sensor could not be found.! Usually this means it is not installed.[/I]
```


And when i check that to see what's in it this is what i see , Wich i assume is correct..:
```
<?xml version="1.0" encoding="UTF-8"?>
<display window-flags="below, sticky" anchor="ne">
  <meta author="Brian Kerrick Nickel" category="Weather/Current Conditions" dependancy="Weather, LTVFontSelector, LTVBorder" name="LTCandy Weather Desklet" version="0.26" />
  <sensor id="weather" module="Weather"/>
  <sensor id="font" module="LTVFontSelector,City|Sans  14|NULL|35||Temperature|Sans  10|NULL|55||Weather Condition|Sans  9|NULL|69"/>
  <sensor id="border" module="LTVBorder,0,15,91,1,gfx/bg/%b.png,none w-top w-bottom w-both"/> 
<!--  <sensor id="border" module="LTVBorder,0,15,91,1,gfx/bg/%b.png,none w-top w-bottom w-both"/> -->
  <group width="185" height="50" x="20" bg-uri="gfx/bg/w-top.png" watch="height=border:height, bg-uri=border:background"/>
  <image x="0" y="0" watch="uri=weather:icon"/>
  <group x="20" y="0">
     <label x="114" anchor="n" font="Sans  14" color="white" watch="value=weather:location, font=font:font0, y=font:offset0"/>
     <group x="114" anchor="n" y="20" watch="y=font:offset1">
        <label id="temp" font="Sans  10" color="white" watch="value=weather:temperature, font=font:font1"/>
        <label id="unit" relative-to="temp, x" font="Sans  10" color="white" watch="value=weather:unit_temp, font=font:font1"/>
     </group>
     <label x="114" anchor="n" y="34" font="Sans  9" color="white" watch="value=weather:sky, font=font:font2, y=font:offset2"/>
  </group>
</display>
```

So what's wrong with this thing...???

---

### Post by jason.b.c on 2006-09-26
:confused: :-k

---

### Post by MKR. on 2006-09-26
I found it in /usr/share/gdesklets/Sensors, not in my home folder. ](*,) 

It works fine now. :P

---

### Post by armalite on 2006-10-31
> Fatal error: Call to undefined function mime_content_type() in /home/pycage/public_html/modules/dlf.module on line 11

This is the message that appears when trying to download the Yahoo Weather Sensor.

IMHO gdesklets is the only program that go worse and worse every year passes. I used desklets since a long time ago, many good desklets (LT Variation), and some kind of support. Every new release throwed away some desklet. Now, see the official website, very poor categorization, very poor support, not so many desklets, and so many little errors like the one above... i remember the good old gdesklets.gnomedesktop.org, a good site. 

To me, gdesklets was a good program that lost a chance to become a *great* (maybe killer-app) one.

---

### Post by ashek on 2006-11-10
Thank you very much. Works perfectly. Now I understand how I missed the iWeather desklet!!!:mrgreen:

---

### Post by clyde9999 on 2006-11-27
Here is an easy solution to the problem. Right click on the gdesklet icon in the system tray, Click on “Manage Desklets”. Leave it to the side. Then open your browser. Go to [http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/) Then scroll down to the “GoodWeather” desklet and drag the checked desklet to your opened desklet manager. It will probably store in the “uncategorized” folder. But will show up for you to double click it to install it to your desktop. It is very easy. Then to configure it, right click on the desklet, then enter your zipcode where it says “location code” choose how often, in minutes, you wish for it to hit the weather site, choose C or F. done!

Have Fun.

Jack

---

### Post by mbslrm on 2006-12-07
I installed it, and whenever I try to enable it, this error comes up:

```
list index out of range                                                              
/usr/lib/gdesklets/utils/ErrorFormatter.py                                           
   37                   hasattr(exc_value, "lineno")):                               
   38                 filename = exc_value.filename                                  
   39                 lineno = exc_value.lineno                                      
   40             else:                                                              
   41                 tbs = traceback.extract_tb(exc_tb)                             
**>  42                 filename = tbs[-1][0]  **                                        
   43                 lineno = tbs[-1][1]                                            
   44                 del tbs                                                        
   45                                                                                
   46         # print error message                                                  
   47         out = "\n"                                                             
   48         out += "[EXC]%s\n" % str(exc_value)
```

---

### Post by s_h_a_d_o_w_s on 2006-12-07
You untar'd it?

Once you untar it and copy it to the gdesklets directory, open up gdesklets, and it should be in the "Uncategorized" area.

This is what you have to do:

cd ~/.gdesklets
tar xzvf /path/where/you/download/tarball
and then you'll the the output be like:

giga@ubuntuzilla:~$ tar xzvf /home/giga/Desktop/iWeather_0.1-ayo.tar.gz
Sensors/iWeather/xmltramp.py
Sensors/iWeather/__init__.py
Sensors/iWeather/__init__.pyc
Sensors/iWeather/xmltramp.pyc
Sensors/iWeather/um/large_icons/5.png
Sensors/iWeather/um/large_icons/35.png
Sensors/iWeather/um/large_icons/47.png
Sensors/iWeather/um/large_icons/20.png
Sensors/iWeather/um/large_icons/6.png
Sensors/iWeather/um/large_icons/31.png
Sensors/iWeather/um/large_icons/13.png
Sensors/iWeather/um/large_icons/1.png
Sensors/iWeather/um/large_icons/30.png
Sensors/iWeather/um/large_icons/38.png
Sensors/iWeather/um/large_icons/10.png
Sensors/iWeather/um/large_icons/3.png
Sensors/iWeather/um/large_icons/26.png
Sensors/iWeather/um/large_icons/12.png
Sensors/iWeather/um/large_icons/42.png
Sensors/iWeather/um/large_icons/15.png
Sensors/iWeather/um/large_icons/28.png
Sensors/iWeather/um/large_icons/29.png
Sensors/iWeather/um/large_icons/19.png
Sensors/iWeather/um/large_icons/33.png
Sensors/iWeather/um/large_icons/43.png
Sensors/iWeather/um/large_icons/32.png
Sensors/iWeather/um/large_icons/22.png
Sensors/iWeather/um/large_icons/37.png
Sensors/iWeather/um/large_icons/24.png
Sensors/iWeather/um/large_icons/14.png
Sensors/iWeather/um/large_icons/44.png
Sensors/iWeather/um/large_icons/25.png
Sensors/iWeather/um/large_icons/23.png
Sensors/iWeather/um/large_icons/16.png
Sensors/iWeather/um/large_icons/2.png
Sensors/iWeather/um/large_icons/8.png
Sensors/iWeather/um/large_icons/27.png
Sensors/iWeather/um/large_icons/36.png
Sensors/iWeather/um/large_icons/41.png
Sensors/iWeather/um/large_icons/39.png
Sensors/iWeather/um/large_icons/34.png
Sensors/iWeather/um/large_icons/7.png
Sensors/iWeather/um/large_icons/9.png
Sensors/iWeather/um/large_icons/17.png
Sensors/iWeather/um/large_icons/4.png
Sensors/iWeather/um/large_icons/18.png
Sensors/iWeather/um/large_icons/45.png
Sensors/iWeather/um/large_icons/40.png
Sensors/iWeather/um/large_icons/21.png
Sensors/iWeather/um/large_icons/11.png
Sensors/iWeather/um/small_icons/5.png
Sensors/iWeather/um/small_icons/35.png
Sensors/iWeather/um/small_icons/47.png
Sensors/iWeather/um/small_icons/20.png
Sensors/iWeather/um/small_icons/6.png
Sensors/iWeather/um/small_icons/31.png
Sensors/iWeather/um/small_icons/13.png
Sensors/iWeather/um/small_icons/1.png
Sensors/iWeather/um/small_icons/30.png
Sensors/iWeather/um/small_icons/38.png
Sensors/iWeather/um/small_icons/10.png
Sensors/iWeather/um/small_icons/3.png
Sensors/iWeather/um/small_icons/26.png
Sensors/iWeather/um/small_icons/12.png
Sensors/iWeather/um/small_icons/42.png
Sensors/iWeather/um/small_icons/15.png
Sensors/iWeather/um/small_icons/28.png
Sensors/iWeather/um/small_icons/29.png
Sensors/iWeather/um/small_icons/19.png
Sensors/iWeather/um/small_icons/33.png
Sensors/iWeather/um/small_icons/43.png
Sensors/iWeather/um/small_icons/32.png
Sensors/iWeather/um/small_icons/22.png
Sensors/iWeather/um/small_icons/37.png
Sensors/iWeather/um/small_icons/24.png
Sensors/iWeather/um/small_icons/14.png
Sensors/iWeather/um/small_icons/44.png
Sensors/iWeather/um/small_icons/25.png
Sensors/iWeather/um/small_icons/23.png
Sensors/iWeather/um/small_icons/16.png
Sensors/iWeather/um/small_icons/2.png
Sensors/iWeather/um/small_icons/8.png
Sensors/iWeather/um/small_icons/27.png
Sensors/iWeather/um/small_icons/36.png
Sensors/iWeather/um/small_icons/41.png
Sensors/iWeather/um/small_icons/39.png
Sensors/iWeather/um/small_icons/34.png
Sensors/iWeather/um/small_icons/7.png
Sensors/iWeather/um/small_icons/9.png
Sensors/iWeather/um/small_icons/17.png
Sensors/iWeather/um/small_icons/4.png
Sensors/iWeather/um/small_icons/18.png
Sensors/iWeather/um/small_icons/45.png
Sensors/iWeather/um/small_icons/40.png
Sensors/iWeather/um/small_icons/21.png
Sensors/iWeather/um/small_icons/11.png
Sensors/iWeather/weather.com/large_icons/5.png
Sensors/iWeather/weather.com/large_icons/35.png
Sensors/iWeather/weather.com/large_icons/47.png
Sensors/iWeather/weather.com/large_icons/20.png
Sensors/iWeather/weather.com/large_icons/6.png
Sensors/iWeather/weather.com/large_icons/31.png
Sensors/iWeather/weather.com/large_icons/13.png
Sensors/iWeather/weather.com/large_icons/1.png
Sensors/iWeather/weather.com/large_icons/na.png
Sensors/iWeather/weather.com/large_icons/30.png
Sensors/iWeather/weather.com/large_icons/38.png
Sensors/iWeather/weather.com/large_icons/10.png
Sensors/iWeather/weather.com/large_icons/3.png
Sensors/iWeather/weather.com/large_icons/26.png
Sensors/iWeather/weather.com/large_icons/12.png
Sensors/iWeather/weather.com/large_icons/42.png
Sensors/iWeather/weather.com/large_icons/15.png
Sensors/iWeather/weather.com/large_icons/28.png
Sensors/iWeather/weather.com/large_icons/29.png
Sensors/iWeather/weather.com/large_icons/19.png
Sensors/iWeather/weather.com/large_icons/33.png
Sensors/iWeather/weather.com/large_icons/43.png
Sensors/iWeather/weather.com/large_icons/32.png
Sensors/iWeather/weather.com/large_icons/22.png
Sensors/iWeather/weather.com/large_icons/37.png
Sensors/iWeather/weather.com/large_icons/24.png
Sensors/iWeather/weather.com/large_icons/14.png
Sensors/iWeather/weather.com/large_icons/44.png
Sensors/iWeather/weather.com/large_icons/25.png
Sensors/iWeather/weather.com/large_icons/23.png
Sensors/iWeather/weather.com/large_icons/16.png
Sensors/iWeather/weather.com/large_icons/0.png
Sensors/iWeather/weather.com/large_icons/2.png
Sensors/iWeather/weather.com/large_icons/8.png
Sensors/iWeather/weather.com/large_icons/27.png
Sensors/iWeather/weather.com/large_icons/36.png
Sensors/iWeather/weather.com/large_icons/41.png
Sensors/iWeather/weather.com/large_icons/46.png
Sensors/iWeather/weather.com/large_icons/39.png
Sensors/iWeather/weather.com/large_icons/34.png
Sensors/iWeather/weather.com/large_icons/7.png
Sensors/iWeather/weather.com/large_icons/9.png
Sensors/iWeather/weather.com/large_icons/17.png
Sensors/iWeather/weather.com/large_icons/4.png
Sensors/iWeather/weather.com/large_icons/18.png
Sensors/iWeather/weather.com/large_icons/45.png
Sensors/iWeather/weather.com/large_icons/40.png
Sensors/iWeather/weather.com/large_icons/21.png
Sensors/iWeather/weather.com/large_icons/11.png
Sensors/iWeather/weather.com/small_icons/5.png
Sensors/iWeather/weather.com/small_icons/35.png
Sensors/iWeather/weather.com/small_icons/47.png
Sensors/iWeather/weather.com/small_icons/20.png
Sensors/iWeather/weather.com/small_icons/6.png
Sensors/iWeather/weather.com/small_icons/31.png
Sensors/iWeather/weather.com/small_icons/13.png
Sensors/iWeather/weather.com/small_icons/1.png
Sensors/iWeather/weather.com/small_icons/na.png
Sensors/iWeather/weather.com/small_icons/30.png
Sensors/iWeather/weather.com/small_icons/38.png
Sensors/iWeather/weather.com/small_icons/10.png
Sensors/iWeather/weather.com/small_icons/3.png
Sensors/iWeather/weather.com/small_icons/26.png
Sensors/iWeather/weather.com/small_icons/12.png
Sensors/iWeather/weather.com/small_icons/42.png
Sensors/iWeather/weather.com/small_icons/15.png
Sensors/iWeather/weather.com/small_icons/28.png
Sensors/iWeather/weather.com/small_icons/29.png
Sensors/iWeather/weather.com/small_icons/19.png
Sensors/iWeather/weather.com/small_icons/33.png
Sensors/iWeather/weather.com/small_icons/43.png
Sensors/iWeather/weather.com/small_icons/32.png
Sensors/iWeather/weather.com/small_icons/22.png
Sensors/iWeather/weather.com/small_icons/37.png
Sensors/iWeather/weather.com/small_icons/24.png
Sensors/iWeather/weather.com/small_icons/14.png
Sensors/iWeather/weather.com/small_icons/44.png
Sensors/iWeather/weather.com/small_icons/25.png
Sensors/iWeather/weather.com/small_icons/23.png
Sensors/iWeather/weather.com/small_icons/16.png
Sensors/iWeather/weather.com/small_icons/0.png
Sensors/iWeather/weather.com/small_icons/2.png
Sensors/iWeather/weather.com/small_icons/8.png
Sensors/iWeather/weather.com/small_icons/27.png
Sensors/iWeather/weather.com/small_icons/36.png
Sensors/iWeather/weather.com/small_icons/41.png
Sensors/iWeather/weather.com/small_icons/46.png
Sensors/iWeather/weather.com/small_icons/39.png
Sensors/iWeather/weather.com/small_icons/34.png
Sensors/iWeather/weather.com/small_icons/7.png
Sensors/iWeather/weather.com/small_icons/9.png
Sensors/iWeather/weather.com/small_icons/17.png
Sensors/iWeather/weather.com/small_icons/4.png
Sensors/iWeather/weather.com/small_icons/18.png
Sensors/iWeather/weather.com/small_icons/45.png
Sensors/iWeather/weather.com/small_icons/40.png
Sensors/iWeather/weather.com/small_icons/21.png
Sensors/iWeather/weather.com/small_icons/11.png
Sensors/iWeather/weather.com/small_icons/.pics/large/5.png
Sensors/iWeather/weather.com/small_icons/.pics/large/35.png
Sensors/iWeather/weather.com/small_icons/.pics/large/47.png
Sensors/iWeather/weather.com/small_icons/.pics/large/20.png
Sensors/iWeather/weather.com/small_icons/.pics/large/6.png
Sensors/iWeather/weather.com/small_icons/.pics/large/31.png
Sensors/iWeather/weather.com/small_icons/.pics/large/13.png
Sensors/iWeather/weather.com/small_icons/.pics/large/1.png
Sensors/iWeather/weather.com/small_icons/.pics/large/na.png
Sensors/iWeather/weather.com/small_icons/.pics/large/30.png
Sensors/iWeather/weather.com/small_icons/.pics/large/38.png
Sensors/iWeather/weather.com/small_icons/.pics/large/10.png
Sensors/iWeather/weather.com/small_icons/.pics/large/3.png
Sensors/iWeather/weather.com/small_icons/.pics/large/26.png
Sensors/iWeather/weather.com/small_icons/.pics/large/12.png
Sensors/iWeather/weather.com/small_icons/.pics/large/42.png
Sensors/iWeather/weather.com/small_icons/.pics/large/15.png
Sensors/iWeather/weather.com/small_icons/.pics/large/28.png
Sensors/iWeather/weather.com/small_icons/.pics/large/29.png
Sensors/iWeather/weather.com/small_icons/.pics/large/19.png
Sensors/iWeather/weather.com/small_icons/.pics/large/33.png
Sensors/iWeather/weather.com/small_icons/.pics/large/43.png
Sensors/iWeather/weather.com/small_icons/.pics/large/32.png
Sensors/iWeather/weather.com/small_icons/.pics/large/22.png
Sensors/iWeather/weather.com/small_icons/.pics/large/37.png
Sensors/iWeather/weather.com/small_icons/.pics/large/24.png
Sensors/iWeather/weather.com/small_icons/.pics/large/14.png
Sensors/iWeather/weather.com/small_icons/.pics/large/44.png
Sensors/iWeather/weather.com/small_icons/.pics/large/25.png
Sensors/iWeather/weather.com/small_icons/.pics/large/23.png
Sensors/iWeather/weather.com/small_icons/.pics/large/16.png
Sensors/iWeather/weather.com/small_icons/.pics/large/0.png
Sensors/iWeather/weather.com/small_icons/.pics/large/2.png
Sensors/iWeather/weather.com/small_icons/.pics/large/8.png
Sensors/iWeather/weather.com/small_icons/.pics/large/27.png
Sensors/iWeather/weather.com/small_icons/.pics/large/36.png
Sensors/iWeather/weather.com/small_icons/.pics/large/41.png
Sensors/iWeather/weather.com/small_icons/.pics/large/46.png
Sensors/iWeather/weather.com/small_icons/.pics/large/39.png
Sensors/iWeather/weather.com/small_icons/.pics/large/34.png
Sensors/iWeather/weather.com/small_icons/.pics/large/7.png
Sensors/iWeather/weather.com/small_icons/.pics/large/9.png
Sensors/iWeather/weather.com/small_icons/.pics/large/17.png
Sensors/iWeather/weather.com/small_icons/.pics/large/4.png
Sensors/iWeather/weather.com/small_icons/.pics/large/18.png
Sensors/iWeather/weather.com/small_icons/.pics/large/45.png
Sensors/iWeather/weather.com/small_icons/.pics/large/40.png
Sensors/iWeather/weather.com/small_icons/.pics/large/21.png
Sensors/iWeather/weather.com/small_icons/.pics/large/11.png
Sensors/iWeather/liquid/large_icons/5.png
Sensors/iWeather/liquid/large_icons/35.png
Sensors/iWeather/liquid/large_icons/20.png
Sensors/iWeather/liquid/large_icons/6.png
Sensors/iWeather/liquid/large_icons/31.png
Sensors/iWeather/liquid/large_icons/13.png
Sensors/iWeather/liquid/large_icons/1.png
Sensors/iWeather/liquid/large_icons/30.png
Sensors/iWeather/liquid/large_icons/38.png
Sensors/iWeather/liquid/large_icons/10.png
Sensors/iWeather/liquid/large_icons/3.png
Sensors/iWeather/liquid/large_icons/26.png
Sensors/iWeather/liquid/large_icons/12.png
Sensors/iWeather/liquid/large_icons/42.png
Sensors/iWeather/liquid/large_icons/15.png
Sensors/iWeather/liquid/large_icons/28.png
Sensors/iWeather/liquid/large_icons/29.png
Sensors/iWeather/liquid/large_icons/19.png
Sensors/iWeather/liquid/large_icons/33.png
Sensors/iWeather/liquid/large_icons/43.png
Sensors/iWeather/liquid/large_icons/32.png
Sensors/iWeather/liquid/large_icons/22.png
Sensors/iWeather/liquid/large_icons/37.png
Sensors/iWeather/liquid/large_icons/24.png
Sensors/iWeather/liquid/large_icons/14.png
Sensors/iWeather/liquid/large_icons/44.png
Sensors/iWeather/liquid/large_icons/25.png
Sensors/iWeather/liquid/large_icons/23.png
Sensors/iWeather/liquid/large_icons/16.png
Sensors/iWeather/liquid/large_icons/2.png
Sensors/iWeather/liquid/large_icons/8.png
Sensors/iWeather/liquid/large_icons/27.png
Sensors/iWeather/liquid/large_icons/36.png
Sensors/iWeather/liquid/large_icons/41.png
Sensors/iWeather/liquid/large_icons/39.png
Sensors/iWeather/liquid/large_icons/34.png
Sensors/iWeather/liquid/large_icons/7.png
Sensors/iWeather/liquid/large_icons/9.png
Sensors/iWeather/liquid/large_icons/17.png
Sensors/iWeather/liquid/large_icons/4.png
Sensors/iWeather/liquid/large_icons/18.png
Sensors/iWeather/liquid/large_icons/40.png
Sensors/iWeather/liquid/large_icons/21.png
Sensors/iWeather/liquid/large_icons/11.png
Sensors/iWeather/liquid/small_icons/5.png
Sensors/iWeather/liquid/small_icons/35.png
Sensors/iWeather/liquid/small_icons/47.png
Sensors/iWeather/liquid/small_icons/20.png
Sensors/iWeather/liquid/small_icons/6.png
Sensors/iWeather/liquid/small_icons/31.png
Sensors/iWeather/liquid/small_icons/13.png
Sensors/iWeather/liquid/small_icons/1.png
Sensors/iWeather/liquid/small_icons/30.png
Sensors/iWeather/liquid/small_icons/38.png
Sensors/iWeather/liquid/small_icons/10.png
Sensors/iWeather/liquid/small_icons/3.png
Sensors/iWeather/liquid/small_icons/26.png
Sensors/iWeather/liquid/small_icons/12.png
Sensors/iWeather/liquid/small_icons/42.png
Sensors/iWeather/liquid/small_icons/15.png
Sensors/iWeather/liquid/small_icons/28.png
Sensors/iWeather/liquid/small_icons/29.png
Sensors/iWeather/liquid/small_icons/19.png
Sensors/iWeather/liquid/small_icons/33.png
Sensors/iWeather/liquid/small_icons/43.png
Sensors/iWeather/liquid/small_icons/32.png
Sensors/iWeather/liquid/small_icons/22.png
Sensors/iWeather/liquid/small_icons/37.png
Sensors/iWeather/liquid/small_icons/24.png
Sensors/iWeather/liquid/small_icons/14.png
Sensors/iWeather/liquid/small_icons/44.png
Sensors/iWeather/liquid/small_icons/25.png
Sensors/iWeather/liquid/small_icons/23.png
Sensors/iWeather/liquid/small_icons/16.png
Sensors/iWeather/liquid/small_icons/2.png
Sensors/iWeather/liquid/small_icons/8.png
Sensors/iWeather/liquid/small_icons/27.png
Sensors/iWeather/liquid/small_icons/36.png
Sensors/iWeather/liquid/small_icons/41.png
Sensors/iWeather/liquid/small_icons/46.png
Sensors/iWeather/liquid/small_icons/39.png
Sensors/iWeather/liquid/small_icons/34.png
Sensors/iWeather/liquid/small_icons/7.png
Sensors/iWeather/liquid/small_icons/9.png
Sensors/iWeather/liquid/small_icons/17.png
Sensors/iWeather/liquid/small_icons/4.png
Sensors/iWeather/liquid/small_icons/18.png
Sensors/iWeather/liquid/small_icons/45.png
Sensors/iWeather/liquid/small_icons/40.png
Sensors/iWeather/liquid/small_icons/21.png
Sensors/iWeather/liquid/small_icons/11.png
Displays/iWeather/iWeather.display
Displays/iWeather/iWeatherBig.display
Displays/iWeather/iWeather.display~
Displays/iWeather/gfx/bg-left.png
Displays/iWeather/gfx/bg-right.png
Displays/iWeather/gfx/bg-weather.png
Displays/iWeather/gfx/bg-bar.png
giga@ubuntuzilla:~$giga@ubuntuzilla:~$ tar xzvf /home/giga/Desktop/iWeather_0.1-ayo.tar.gz
Sensors/iWeather/xmltramp.py
Sensors/iWeather/__init__.py
Sensors/iWeather/__init__.pyc
Sensors/iWeather/xmltramp.pyc
Sensors/iWeather/um/large_icons/5.png
Sensors/iWeather/um/large_icons/35.png
Sensors/iWeather/um/large_icons/47.png
Sensors/iWeather/um/large_icons/20.png
Sensors/iWeather/um/large_icons/6.png
Sensors/iWeather/um/large_icons/31.png
Sensors/iWeather/um/large_icons/13.png
Sensors/iWeather/um/large_icons/1.png
Sensors/iWeather/um/large_icons/30.png
Sensors/iWeather/um/large_icons/38.png
Sensors/iWeather/um/large_icons/10.png
Sensors/iWeather/um/large_icons/3.png
Sensors/iWeather/um/large_icons/26.png
Sensors/iWeather/um/large_icons/12.png
Sensors/iWeather/um/large_icons/42.png
Sensors/iWeather/um/large_icons/15.png
Sensors/iWeather/um/large_icons/28.png
Sensors/iWeather/um/large_icons/29.png
Sensors/iWeather/um/large_icons/19.png
Sensors/iWeather/um/large_icons/33.png
Sensors/iWeather/um/large_icons/43.png
Sensors/iWeather/um/large_icons/32.png
Sensors/iWeather/um/large_icons/22.png
Sensors/iWeather/um/large_icons/37.png
Sensors/iWeather/um/large_icons/24.png
Sensors/iWeather/um/large_icons/14.png
Sensors/iWeather/um/large_icons/44.png
Sensors/iWeather/um/large_icons/25.png
Sensors/iWeather/um/large_icons/23.png
Sensors/iWeather/um/large_icons/16.png
Sensors/iWeather/um/large_icons/2.png
Sensors/iWeather/um/large_icons/8.png
Sensors/iWeather/um/large_icons/27.png
Sensors/iWeather/um/large_icons/36.png
Sensors/iWeather/um/large_icons/41.png
Sensors/iWeather/um/large_icons/39.png
Sensors/iWeather/um/large_icons/34.png
Sensors/iWeather/um/large_icons/7.png
Sensors/iWeather/um/large_icons/9.png
Sensors/iWeather/um/large_icons/17.png
Sensors/iWeather/um/large_icons/4.png
Sensors/iWeather/um/large_icons/18.png
Sensors/iWeather/um/large_icons/45.png
Sensors/iWeather/um/large_icons/40.png
Sensors/iWeather/um/large_icons/21.png
Sensors/iWeather/um/large_icons/11.png
Sensors/iWeather/um/small_icons/5.png
Sensors/iWeather/um/small_icons/35.png
Sensors/iWeather/um/small_icons/47.png
Sensors/iWeather/um/small_icons/20.png
Sensors/iWeather/um/small_icons/6.png
Sensors/iWeather/um/small_icons/31.png
Sensors/iWeather/um/small_icons/13.png
Sensors/iWeather/um/small_icons/1.png
Sensors/iWeather/um/small_icons/30.png
Sensors/iWeather/um/small_icons/38.png
Sensors/iWeather/um/small_icons/10.png
Sensors/iWeather/um/small_icons/3.png
Sensors/iWeather/um/small_icons/26.png
Sensors/iWeather/um/small_icons/12.png
Sensors/iWeather/um/small_icons/42.png
Sensors/iWeather/um/small_icons/15.png
Sensors/iWeather/um/small_icons/28.png
Sensors/iWeather/um/small_icons/29.png
Sensors/iWeather/um/small_icons/19.png
Sensors/iWeather/um/small_icons/33.png
Sensors/iWeather/um/small_icons/43.png
Sensors/iWeather/um/small_icons/32.png
Sensors/iWeather/um/small_icons/22.png
Sensors/iWeather/um/small_icons/37.png
Sensors/iWeather/um/small_icons/24.png
Sensors/iWeather/um/small_icons/14.png
Sensors/iWeather/um/small_icons/44.png
Sensors/iWeather/um/small_icons/25.png
Sensors/iWeather/um/small_icons/23.png
Sensors/iWeather/um/small_icons/16.png
Sensors/iWeather/um/small_icons/2.png
Sensors/iWeather/um/small_icons/8.png
Sensors/iWeather/um/small_icons/27.png
Sensors/iWeather/um/small_icons/36.png
Sensors/iWeather/um/small_icons/41.png
Sensors/iWeather/um/small_icons/39.png
Sensors/iWeather/um/small_icons/34.png
Sensors/iWeather/um/small_icons/7.png
Sensors/iWeather/um/small_icons/9.png
Sensors/iWeather/um/small_icons/17.png
Sensors/iWeather/um/small_icons/4.png
Sensors/iWeather/um/small_icons/18.png
Sensors/iWeather/um/small_icons/45.png
Sensors/iWeather/um/small_icons/40.png
Sensors/iWeather/um/small_icons/21.png
Sensors/iWeather/um/small_icons/11.png
Sensors/iWeather/weather.com/large_icons/5.png
Sensors/iWeather/weather.com/large_icons/35.png
Sensors/iWeather/weather.com/large_icons/47.png
Sensors/iWeather/weather.com/large_icons/20.png
Sensors/iWeather/weather.com/large_icons/6.png
Sensors/iWeather/weather.com/large_icons/31.png
Sensors/iWeather/weather.com/large_icons/13.png
Sensors/iWeather/weather.com/large_icons/1.png
Sensors/iWeather/weather.com/large_icons/na.png
Sensors/iWeather/weather.com/large_icons/30.png
Sensors/iWeather/weather.com/large_icons/38.png
Sensors/iWeather/weather.com/large_icons/10.png
Sensors/iWeather/weather.com/large_icons/3.png
Sensors/iWeather/weather.com/large_icons/26.png
Sensors/iWeather/weather.com/large_icons/12.png
Sensors/iWeather/weather.com/large_icons/42.png
Sensors/iWeather/weather.com/large_icons/15.png
Sensors/iWeather/weather.com/large_icons/28.png
Sensors/iWeather/weather.com/large_icons/29.png
Sensors/iWeather/weather.com/large_icons/19.png
Sensors/iWeather/weather.com/large_icons/33.png
Sensors/iWeather/weather.com/large_icons/43.png
Sensors/iWeather/weather.com/large_icons/32.png
Sensors/iWeather/weather.com/large_icons/22.png
Sensors/iWeather/weather.com/large_icons/37.png
Sensors/iWeather/weather.com/large_icons/24.png
Sensors/iWeather/weather.com/large_icons/14.png
Sensors/iWeather/weather.com/large_icons/44.png
Sensors/iWeather/weather.com/large_icons/25.png
Sensors/iWeather/weather.com/large_icons/23.png
Sensors/iWeather/weather.com/large_icons/16.png
Sensors/iWeather/weather.com/large_icons/0.png
Sensors/iWeather/weather.com/large_icons/2.png
Sensors/iWeather/weather.com/large_icons/8.png
Sensors/iWeather/weather.com/large_icons/27.png
Sensors/iWeather/weather.com/large_icons/36.png
Sensors/iWeather/weather.com/large_icons/41.png
Sensors/iWeather/weather.com/large_icons/46.png
Sensors/iWeather/weather.com/large_icons/39.png
Sensors/iWeather/weather.com/large_icons/34.png
Sensors/iWeather/weather.com/large_icons/7.png
Sensors/iWeather/weather.com/large_icons/9.png
Sensors/iWeather/weather.com/large_icons/17.png
Sensors/iWeather/weather.com/large_icons/4.png
Sensors/iWeather/weather.com/large_icons/18.png
Sensors/iWeather/weather.com/large_icons/45.png
Sensors/iWeather/weather.com/large_icons/40.png
Sensors/iWeather/weather.com/large_icons/21.png
Sensors/iWeather/weather.com/large_icons/11.png
Sensors/iWeather/weather.com/small_icons/5.png
Sensors/iWeather/weather.com/small_icons/35.png
Sensors/iWeather/weather.com/small_icons/47.png
Sensors/iWeather/weather.com/small_icons/20.png
Sensors/iWeather/weather.com/small_icons/6.png
Sensors/iWeather/weather.com/small_icons/31.png
Sensors/iWeather/weather.com/small_icons/13.png
Sensors/iWeather/weather.com/small_icons/1.png
Sensors/iWeather/weather.com/small_icons/na.png
Sensors/iWeather/weather.com/small_icons/30.png
Sensors/iWeather/weather.com/small_icons/38.png
Sensors/iWeather/weather.com/small_icons/10.png
Sensors/iWeather/weather.com/small_icons/3.png
Sensors/iWeather/weather.com/small_icons/26.png
Sensors/iWeather/weather.com/small_icons/12.png
Sensors/iWeather/weather.com/small_icons/42.png
Sensors/iWeather/weather.com/small_icons/15.png
Sensors/iWeather/weather.com/small_icons/28.png
Sensors/iWeather/weather.com/small_icons/29.png
Sensors/iWeather/weather.com/small_icons/19.png
Sensors/iWeather/weather.com/small_icons/33.png
Sensors/iWeather/weather.com/small_icons/43.png
Sensors/iWeather/weather.com/small_icons/32.png
Sensors/iWeather/weather.com/small_icons/22.png
Sensors/iWeather/weather.com/small_icons/37.png
Sensors/iWeather/weather.com/small_icons/24.png
Sensors/iWeather/weather.com/small_icons/14.png
Sensors/iWeather/weather.com/small_icons/44.png
Sensors/iWeather/weather.com/small_icons/25.png
Sensors/iWeather/weather.com/small_icons/23.png
Sensors/iWeather/weather.com/small_icons/16.png
Sensors/iWeather/weather.com/small_icons/0.png
Sensors/iWeather/weather.com/small_icons/2.png
Sensors/iWeather/weather.com/small_icons/8.png
Sensors/iWeather/weather.com/small_icons/27.png
Sensors/iWeather/weather.com/small_icons/36.png
Sensors/iWeather/weather.com/small_icons/41.png
Sensors/iWeather/weather.com/small_icons/46.png
Sensors/iWeather/weather.com/small_icons/39.png
Sensors/iWeather/weather.com/small_icons/34.png
Sensors/iWeather/weather.com/small_icons/7.png
Sensors/iWeather/weather.com/small_icons/9.png
Sensors/iWeather/weather.com/small_icons/17.png
Sensors/iWeather/weather.com/small_icons/4.png
Sensors/iWeather/weather.com/small_icons/18.png
Sensors/iWeather/weather.com/small_icons/45.png
Sensors/iWeather/weather.com/small_icons/40.png
Sensors/iWeather/weather.com/small_icons/21.png
Sensors/iWeather/weather.com/small_icons/11.png
Sensors/iWeather/weather.com/small_icons/.pics/large/5.png
Sensors/iWeather/weather.com/small_icons/.pics/large/35.png
Sensors/iWeather/weather.com/small_icons/.pics/large/47.png
Sensors/iWeather/weather.com/small_icons/.pics/large/20.png
Sensors/iWeather/weather.com/small_icons/.pics/large/6.png
Sensors/iWeather/weather.com/small_icons/.pics/large/31.png
Sensors/iWeather/weather.com/small_icons/.pics/large/13.png
Sensors/iWeather/weather.com/small_icons/.pics/large/1.png
Sensors/iWeather/weather.com/small_icons/.pics/large/na.png
Sensors/iWeather/weather.com/small_icons/.pics/large/30.png
Sensors/iWeather/weather.com/small_icons/.pics/large/38.png
Sensors/iWeather/weather.com/small_icons/.pics/large/10.png
Sensors/iWeather/weather.com/small_icons/.pics/large/3.png
Sensors/iWeather/weather.com/small_icons/.pics/large/26.png
Sensors/iWeather/weather.com/small_icons/.pics/large/12.png
Sensors/iWeather/weather.com/small_icons/.pics/large/42.png
Sensors/iWeather/weather.com/small_icons/.pics/large/15.png
Sensors/iWeather/weather.com/small_icons/.pics/large/28.png
Sensors/iWeather/weather.com/small_icons/.pics/large/29.png
Sensors/iWeather/weather.com/small_icons/.pics/large/19.png
Sensors/iWeather/weather.com/small_icons/.pics/large/33.png
Sensors/iWeather/weather.com/small_icons/.pics/large/43.png
Sensors/iWeather/weather.com/small_icons/.pics/large/32.png
Sensors/iWeather/weather.com/small_icons/.pics/large/22.png
Sensors/iWeather/weather.com/small_icons/.pics/large/37.png
Sensors/iWeather/weather.com/small_icons/.pics/large/24.png
Sensors/iWeather/weather.com/small_icons/.pics/large/14.png
Sensors/iWeather/weather.com/small_icons/.pics/large/44.png
Sensors/iWeather/weather.com/small_icons/.pics/large/25.png
Sensors/iWeather/weather.com/small_icons/.pics/large/23.png
Sensors/iWeather/weather.com/small_icons/.pics/large/16.png
Sensors/iWeather/weather.com/small_icons/.pics/large/0.png
Sensors/iWeather/weather.com/small_icons/.pics/large/2.png
Sensors/iWeather/weather.com/small_icons/.pics/large/8.png
Sensors/iWeather/weather.com/small_icons/.pics/large/27.png
Sensors/iWeather/weather.com/small_icons/.pics/large/36.png
Sensors/iWeather/weather.com/small_icons/.pics/large/41.png
Sensors/iWeather/weather.com/small_icons/.pics/large/46.png
Sensors/iWeather/weather.com/small_icons/.pics/large/39.png
Sensors/iWeather/weather.com/small_icons/.pics/large/34.png
Sensors/iWeather/weather.com/small_icons/.pics/large/7.png
Sensors/iWeather/weather.com/small_icons/.pics/large/9.png
Sensors/iWeather/weather.com/small_icons/.pics/large/17.png
Sensors/iWeather/weather.com/small_icons/.pics/large/4.png
Sensors/iWeather/weather.com/small_icons/.pics/large/18.png
Sensors/iWeather/weather.com/small_icons/.pics/large/45.png
Sensors/iWeather/weather.com/small_icons/.pics/large/40.png
Sensors/iWeather/weather.com/small_icons/.pics/large/21.png
Sensors/iWeather/weather.com/small_icons/.pics/large/11.png
Sensors/iWeather/liquid/large_icons/5.png
Sensors/iWeather/liquid/large_icons/35.png
Sensors/iWeather/liquid/large_icons/20.png
Sensors/iWeather/liquid/large_icons/6.png
Sensors/iWeather/liquid/large_icons/31.png
Sensors/iWeather/liquid/large_icons/13.png
Sensors/iWeather/liquid/large_icons/1.png
Sensors/iWeather/liquid/large_icons/30.png
Sensors/iWeather/liquid/large_icons/38.png
Sensors/iWeather/liquid/large_icons/10.png
Sensors/iWeather/liquid/large_icons/3.png
Sensors/iWeather/liquid/large_icons/26.png
Sensors/iWeather/liquid/large_icons/12.png
Sensors/iWeather/liquid/large_icons/42.png
Sensors/iWeather/liquid/large_icons/15.png
Sensors/iWeather/liquid/large_icons/28.png
Sensors/iWeather/liquid/large_icons/29.png
Sensors/iWeather/liquid/large_icons/19.png
Sensors/iWeather/liquid/large_icons/33.png
Sensors/iWeather/liquid/large_icons/43.png
Sensors/iWeather/liquid/large_icons/32.png
Sensors/iWeather/liquid/large_icons/22.png
Sensors/iWeather/liquid/large_icons/37.png
Sensors/iWeather/liquid/large_icons/24.png
Sensors/iWeather/liquid/large_icons/14.png
Sensors/iWeather/liquid/large_icons/44.png
Sensors/iWeather/liquid/large_icons/25.png
Sensors/iWeather/liquid/large_icons/23.png
Sensors/iWeather/liquid/large_icons/16.png
Sensors/iWeather/liquid/large_icons/2.png
Sensors/iWeather/liquid/large_icons/8.png
Sensors/iWeather/liquid/large_icons/27.png
Sensors/iWeather/liquid/large_icons/36.png
Sensors/iWeather/liquid/large_icons/41.png
Sensors/iWeather/liquid/large_icons/39.png
Sensors/iWeather/liquid/large_icons/34.png
Sensors/iWeather/liquid/large_icons/7.png
Sensors/iWeather/liquid/large_icons/9.png
Sensors/iWeather/liquid/large_icons/17.png
Sensors/iWeather/liquid/large_icons/4.png
Sensors/iWeather/liquid/large_icons/18.png
Sensors/iWeather/liquid/large_icons/40.png
Sensors/iWeather/liquid/large_icons/21.png
Sensors/iWeather/liquid/large_icons/11.png
Sensors/iWeather/liquid/small_icons/5.png
Sensors/iWeather/liquid/small_icons/35.png
Sensors/iWeather/liquid/small_icons/47.png
Sensors/iWeather/liquid/small_icons/20.png
Sensors/iWeather/liquid/small_icons/6.png
Sensors/iWeather/liquid/small_icons/31.png
Sensors/iWeather/liquid/small_icons/13.png
Sensors/iWeather/liquid/small_icons/1.png
Sensors/iWeather/liquid/small_icons/30.png
Sensors/iWeather/liquid/small_icons/38.png
Sensors/iWeather/liquid/small_icons/10.png
Sensors/iWeather/liquid/small_icons/3.png
Sensors/iWeather/liquid/small_icons/26.png
Sensors/iWeather/liquid/small_icons/12.png
Sensors/iWeather/liquid/small_icons/42.png
Sensors/iWeather/liquid/small_icons/15.png
Sensors/iWeather/liquid/small_icons/28.png
Sensors/iWeather/liquid/small_icons/29.png
Sensors/iWeather/liquid/small_icons/19.png
Sensors/iWeather/liquid/small_icons/33.png
Sensors/iWeather/liquid/small_icons/43.png
Sensors/iWeather/liquid/small_icons/32.png
Sensors/iWeather/liquid/small_icons/22.png
Sensors/iWeather/liquid/small_icons/37.png
Sensors/iWeather/liquid/small_icons/24.png
Sensors/iWeather/liquid/small_icons/14.png
Sensors/iWeather/liquid/small_icons/44.png
Sensors/iWeather/liquid/small_icons/25.png
Sensors/iWeather/liquid/small_icons/23.png
Sensors/iWeather/liquid/small_icons/16.png
Sensors/iWeather/liquid/small_icons/2.png
Sensors/iWeather/liquid/small_icons/8.png
Sensors/iWeather/liquid/small_icons/27.png
Sensors/iWeather/liquid/small_icons/36.png
Sensors/iWeather/liquid/small_icons/41.png
Sensors/iWeather/liquid/small_icons/46.png
Sensors/iWeather/liquid/small_icons/39.png
Sensors/iWeather/liquid/small_icons/34.png
Sensors/iWeather/liquid/small_icons/7.png
Sensors/iWeather/liquid/small_icons/9.png
Sensors/iWeather/liquid/small_icons/17.png
Sensors/iWeather/liquid/small_icons/4.png
Sensors/iWeather/liquid/small_icons/18.png
Sensors/iWeather/liquid/small_icons/45.png
Sensors/iWeather/liquid/small_icons/40.png
Sensors/iWeather/liquid/small_icons/21.png
Sensors/iWeather/liquid/small_icons/11.png
Displays/iWeather/iWeather.display
Displays/iWeather/iWeatherBig.display
Displays/iWeather/iWeather.display~
Displays/iWeather/gfx/bg-left.png
Displays/iWeather/gfx/bg-right.png
Displays/iWeather/gfx/bg-weather.png
Displays/iWeather/gfx/bg-bar.png
giga@ubuntuzilla:~$

Then it'll be in gdesklets

---

### Post by mbslrm on 2006-12-07
What would be the directory, if it is in Desktop?

Yeah, I know I'm newbie....

---

### Post by snap2phil on 2006-12-12
Hi,
can someone tell me plz where I can find the updated Yahoo Weather Sensor (by levellord)! On [www.gdesklets.org](www.gdesklets.org) I cant download it. Or can someone upload the tarball for me? 
Thx snap2phil

---

### Post by bernt on 2007-01-20
> **snap2phil said:**
> Hi,
can someone tell me plz where I can find the updated Yahoo Weather Sensor (by levellord)! On [www.gdesklets.org](www.gdesklets.org) I cant download it. Or can someone upload the tarball for me? 
Thx snap2phil


Hi!

I really like to have the update to, please.

Kind Regards
/Bernt

---

### Post by jcconnor on 2007-02-03
Great stuff - the drag and drop method worked like a champ for me!!!

---

### Post by flammenwurfer on 2007-02-06
Does anybody know where in the source or settings I can resize the desklet?  The thing is huge!  I changed the number of forecast days to 3 instead of 5, however the desklet stays the same size and the space where those other days were overlaps other stuff.

---

### Post by David_Scott_1904 on 2007-02-25
> **snap2phil said:**
> Hi,
can someone tell me plz where I can find the updated Yahoo Weather Sensor (by levellord)! On [www.gdesklets.org](www.gdesklets.org) I cant download it. Or can someone upload the tarball for me? 
Thx snap2phil

Another request for this, please. Gdesklets link now just gives a login screen in German, linking to about 4 desklets.
 
Thanks in advance

---

### Post by Tiller on 2007-02-25
WOW it worked I dragged and dropped and the gadget came up the only thing not discussed is..
I'm from Canada and it is only for the good ole U.S.A. oh well any other suggestions? Thanks:)

---

### Post by wesley_of_course on 2007-04-06
Wesley here ; 

               A little late but ,,,,,,,  [http://www.gdesklets.de/](http://www.gdesklets.de/)


     Have fun !

---

### Post by 13217495 on 2007-04-22
Yahoo's website has changed the page layout so I rewrote the regular expressions if you want some of the weather desklets to work replace the code with the below in the __init__.py file in the /usr/share/gdesklets/Sensor/weather directory


RE_TEMPERATURE = re.compile("<h3>(?P<temp>\d+)&deg;</h3>")
RE_TEMPERATURE_HI = re.compile("")
RE_TEMPERATURE_LO = re.compile("")
RE_TEMPERATURE_FEEL = re.compile("<dt>Feels Like:</dt>\n<dd>(?P<temp_feel>\d+)&deg;</dd>")
RE_PRESSURE = re.compile("<dt>Barometer:</dt>\n<dd>\n(?P<pressure>[\d\.]+) \w+ \nand (?P<pressure_change>.+)\n")
RE_DEWPOINT = re.compile("<dt>Dewpoint:</dt>\n<dd>(?P<dewpoint>\d+)&deg;</dd>")
RE_WIND = re.compile("<dt>Wind:</dt>\n<dd>(?P<wind>[\w\s]+)</dd>")
RE_HUMIDITY = re.compile("<dt>Humidity:</dt>\n<dd>(?P<humidity>\d+)\%")
RE_SUNRISE = re.compile("<dt>Sunrise:</dt>\n<dd>(?P<sunrise>.+)</dd>")
RE_SUNSET = re.compile("<dt>Sunset:</dt>\n<dd>\n(?P<sunset>.+)</dd>")
RE_VISIBILITY = re.compile("<dt>Visibility:</dt>\n<dd>\n(?P<visibility>\S+)")
RE_SKY = re.compile("</em>\n<h3>(?P<sky>[^\<]+)</h3>")
RE_ICON = re.compile("http://us.i1.yimg.com/us.yimg.com/i/us/nws/weather/gr/(?P<icon>\d+)\D.png")
RE_MATCHES = re.compile("Weather location matches:\</font\>\</td\>\n\s*\</tr\>\</table\>\n\s*\<font face=\"arial\" size=-1\>\n\s*\<ul\>\n\s*\<li\>\n\s*\<a href=\"(?P<matchurl>[^\"]+)\"\>")

---

### Post by Nevis on 2007-06-01
Excellent! Works perfectly. For newbies (such as myself) remember to indent properly or Python won't be happy! ;-)

---

