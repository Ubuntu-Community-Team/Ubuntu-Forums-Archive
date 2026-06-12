---
title: "Conky question...HELP!!"
date: 2009-02-19
forum: Desktop Environments
---

### Post by atanase on 2009-02-19
Hi all,

I am new to this forum and even newer on the UNIX platform please don't rush me around as I get lost very quick. :)

I have Ubuntu Ultimate(OMG - ROCKS!!) and installed Conky which is also great. I decided to delete the folder in systemfile/usr/share/conky 1.6.1 as root(I know, STUPID) not only that, I did e Empty trash from bin. 

That was the intro, the problem now: I uninstalled Conky with Synaptics(Complete removal) and reinstalled it again but still can't see any folder in home or anywhere else. I tried install it in different ways Terminal/Synaptics but still can't see any traces of the program in my usr/share, nothing. It installs ok, but no Conky anywhere to see, not even as a hidden file. Considering reinstalling Ubuntu..but still hoping that you guys can help me.


The reason of deleting the Conky file from /usr/share was that I installed some Rhythm music player add that chgnaged the name of the folder ..... and I had a panic fit. SORRY..pls help!


Many thanks!!

In fact after I install it again I can't find any traces of Conky at all..wtf?

---

### Post by glotz on 2009-02-19
Open up Synaptic and find the conky package. Right click it > properties > installed files.

---

### Post by krazyd on 2009-02-19
you can also see this using```
apt-file list conky
```you may need to ```
apt-get install apt-file
```first

---

### Post by atanase on 2009-02-20
Many thanks, done now!

:)

---

### Post by atanase on 2009-02-20
Thank you for your fast replyes once again. I have another qustion regarding Conky, it's tthe Weather script, I can't get to show the temperatures. All I get it's a "C" space and then "/".

.conkyrc configuration: 

${voffset -15}${font ConkyWeather:size=36}c ${font Zero Threes:size=15}${voffset -5}${execi 3600 conkyForecast --location=UKXX0309 --datatype=LT} / ${execi 3600 conkyForecast --location=UKXX0309 --datatype=HT

.conkyForecast.config configuration:

[http://xoap.weather.com/weather/local/30339?cc=*&dayf=5&link=xoap&prod=xoap&par=](http://xoap.weather.com/weather/local/30339?cc=*&dayf=5&link=xoap&prod=xoap&par=)***[COLOR="Red"]these are hidden from public view[/COLOR]***&key=***[COLOR="Red"]these are hidden from public view[/COLOR]***

What am I doing wrong? I know I'm missing something... See image attached.

Cheers..

---

### Post by glotz on 2009-02-20
So what does the conkyForecast script do? Do you get any output if you run it from terminal? Does it have the executable permission set?

---

### Post by atanase on 2009-02-20
Well glotz, this is what I am missing I think, but still can't figure out how to set it up. I got as far as you can see nothing else. Don't know what else to add to the script. I looked online but can't get my head around it. I suppose I'm the slowest learner in the world...some ppl call is stupid. :D

Cheers mate!

Add: 

I followed this tutorial [http://maketecheasier.com/how-to-create-a-minimal-and-beautiful-desktop-with-conky/2008/10/30](http://maketecheasier.com/how-to-create-a-minimal-and-beautiful-desktop-with-conky/2008/10/30)  , but I'm missing something.

---

### Post by glotz on 2009-02-20
Oh, looks like it's some custom rig from this guy's ppa. Did you install it?

And if you look at **his** screenshot, there's a strange letter Â there too! :)

If you can't figure out this tutorial, there's like 1000000 other weather tutorials for conky around, some of them could be better. Don't worry the stupid part, it's your computer and your leisure time! Have fun!

---

### Post by atanase on 2009-02-21
Many thanks "glotz" I thought I did install the ppa but I haven't, in terminal I had to press return twice :D. 
 However I did get rid of the "A" thing and the only problem left is the degree symbol, shows a upside down "!". 

Screenshot attached as well.



Here is my Template:

```
${voffset 5}${goto 10}${font ConkyWeather:style=Bold:size=40}[--datatype=WF]${font}
${voffset 5}${goto 20}[--datatype=HT --hideunits --centeredwidth=3]/[--datatype=LT --hideunits --centeredwidth=3]
${voffset 10}${goto 10}${font ConkyWindNESW:size=40}[--datatype=BS]${font}
${voffset 5}${goto 10}[--datatype=WS --imperial] - [--datatype=WD]
${voffset -145}${goto 100}${color1}${font Bitstream Vera Sans Mono:style=Bold:size=14}[--datatype=CT]${font}
${voffset 10}${goto 100}${color3}Station: ${color1}[--datatype=OB]
${goto 100}${color3}Rain: ${color1}[--datatype=PC]
${goto 100}${color3}UV: ${color1}[--datatype=UI] - [--datatype=UT]
${goto 100}${color3}Humidity: ${color1}[--datatype=HM]
${goto 100}${color3}Dew Point: ${color1}[--datatype=DP]
${goto 100}${color3}Sunrise/Set: ${color1}[--datatype=SR] / [--datatype=SS]
${goto 100}${color3}Bar: ${color1}[--datatype=BR] - [--datatype=BD]
${goto 100}${color3}Moon: ${color1}[--datatype=MP]
${voffset 25}${goto 25}[--datatype=DW --startday=1 --shortweekday]${goto 100}[--datatype=DW --startday=2 --shortweekday]${goto 175}[--datatype=DW --startday=3 --shortweekday]${goto 250}[--datatype=DW --startday=4 --shortweekday]
${voffset 10}${goto 10}${font ConkyWeather:size=32}[--datatype=WF --startday=1 --endday=4 --spaces=3]${font}
${voffset 15}${goto 15}[--datatype=HT --startday=1 --hideunits --centeredwidth=3]/[--datatype=LT --startday=1 --hideunits --centeredwidth=3]${goto 90}[--datatype=HT --startday=2 --hideunits --centeredwidth=3]/[--datatype=LT --startday=2 --hideunits --centeredwidth=3]${goto 170}[--datatype=HT --startday=3 --hideunits --centeredwidth=3]/[--datatype=LT --startday=3 --hideunits --centeredwidth=3]${goto 245}[--datatype=HT --startday=4 --hideunits --centeredwidth=3]/[--datatype=LT --startday=4 --hideunits --centeredwidth=3]
${color3}${font Bitstream Vera Sans Mono:size=7}${alignr 20}Last Update: [--datatype=LU]${font}
```



I just noticed, I have 2 Templates. One in folder "example" the other in "test". I'm posting both:


```
CURRENT CONDITIONS:
[--datatype=DW]: [--datatype=HT] / [--datatype=LT] [--datatype=CC] (unlocalized text: [--datatype=CT])
Wind: [--datatype=WD] ([--datatype=WA]) at [--datatype=WS] Humidity: [--datatype=HM] Precipatation: [--datatype=PC] Visibility: [--datatype=VI] Sun: Rise/Set: [--datatype=SR] / [--datatype=SS]
Moon: [--datatype=MP] Bar: [--datatype=BR] ([--datatype=BD]) UV: [--datatype=UI] ([--datatype=UT]) Dew point: [--datatype=DP] [--datatype=LU]
IMPERIAL:
[--datatype=DW --imperial]: [--datatype=HT --imperial] / [--datatype=LT --imperial] [--datatype=CC --imperial] (unlocalized text: [--datatype=CT --imperial])
Wind: [--datatype=WD --imperial] ([--datatype=WA --imperial]) at [--datatype=WS --imperial] Humidity: [--datatype=HM --imperial] Precipatation: [--datatype=PC --imperial] Visibility: [--datatype=VI --imperial] Sun: Rise/Set: [--datatype=SR --imperial] / [--datatype=SS --imperial]
Moon: [--datatype=MP --imperial] Bar: [--datatype=BR --imperial] ([--datatype=BD --imperial]) UV: [--datatype=UI --imperial] ([--datatype=UT --imperial]) Dew point: [--datatype=DP --imperial] [--datatype=LU --imperial]
HIDEUNITS:
[--datatype=DW --hideunits]: [--datatype=HT --hideunits] / [--datatype=LT --hideunits] [--datatype=CC --hideunits] (unlocalized text: [--datatype=CT --hideunits])
Wind: [--datatype=WD --hideunits] ([--datatype=WA --hideunits]) at [--datatype=WS --hideunits] Humidity: [--datatype=HM --hideunits] Precipatation: [--datatype=PC --hideunits] Visibility: [--datatype=VI --hideunits] Sun: Rise/Set: [--datatype=SR --hideunits] / [--datatype=SS --hideunits]
Moon: [--datatype=MP --hideunits] Bar: [--datatype=BR --hideunits] ([--datatype=BD --hideunits]) UV: [--datatype=UI --hideunits] ([--datatype=UT --hideunits]) Dew point: [--datatype=DP --hideunits] [--datatype=LU --hideunits]
FORECAST 0:
[--datatype=DW --startday=0]: [--datatype=HT --startday=0] / [--datatype=LT --startday=0] [--datatype=CC --startday=0] (unlocalized text: [--datatype=CT --startday=0])
Wind: [--datatype=WD --startday=0] ([--datatype=WA --startday=0]) at [--datatype=WS --startday=0] Humidity: [--datatype=HM --startday=0] Precipatation: [--datatype=PC --startday=0] Visibility: [--datatype=VI --startday=0] Sun: Rise/Set: [--datatype=SR --startday=0] / [--datatype=SS --startday=0]
Moon: [--datatype=MP --startday=0] Bar: [--datatype=BR --startday=0] ([--datatype=BD --startday=0]) UV: [--datatype=UI --startday=0] ([--datatype=UT --startday=0]) Dew point: [--datatype=DP --startday=0] [--datatype=LU --startday=0]
FORECAST 1:
[--datatype=DW --startday=1]: [--datatype=HT --startday=1] / [--datatype=LT --startday=1] [--datatype=CC --startday=1] (unlocalized text: [--datatype=CT --startday=1])
Wind: [--datatype=WD --startday=1] ([--datatype=WA --startday=1]) at [--datatype=WS --startday=1] Humidity: [--datatype=HM --startday=1] Precipatation: [--datatype=PC --startday=1] Visibility: [--datatype=VI --startday=1] Sun: Rise/Set: [--datatype=SR --startday=1] / [--datatype=SS --startday=1]
Moon: [--datatype=MP --startday=1] Bar: [--datatype=BR --startday=1] ([--datatype=BD --startday=1]) UV: [--datatype=UI --startday=1] ([--datatype=UT --startday=1]) Dew point: [--datatype=DP --startday=1] [--datatype=LU --startday=1]
FORECAST 4:
[--datatype=DW --startday=4]: [--datatype=HT --startday=4] / [--datatype=LT --startday=4] [--datatype=CC --startday=4] (unlocalized text: [--datatype=CT --startday=4])
Wind: [--datatype=WD --startday=4] ([--datatype=WA --startday=4]) at [--datatype=WS --startday=4] Humidity: [--datatype=HM --startday=4] Precipatation: [--datatype=PC --startday=4] Visibility: [--datatype=VI --startday=4] Sun: Rise/Set: [--datatype=SR --startday=4] / [--datatype=SS --startday=4]
Moon: [--datatype=MP --startday=4] Bar: [--datatype=BR --startday=4] ([--datatype=BD --startday=4]) UV: [--datatype=UI --startday=4] ([--datatype=UT --startday=4]) Dew point: [--datatype=DP --startday=4] [--datatype=LU --startday=4]
MINUTESHIDE LAST FETCH:
default: [--datatype=LF --minuteshide=-1]
0: [--datatype=LF --minuteshide=0]
5: [--datatype=LF --minuteshide=5]
SPACING:
default: [--datatype=DW --startday=0 --endday=4]
[--datatype=CT --startday=0 --endday=4]
spaces = 3: [--datatype=DW --startday=0 --endday=4 --spaces=3]
[--datatype=CT --startday=0 --endday=4 --spaces=3]
```



Thank you all!

---

### Post by atanase on 2009-02-23
OK, the weather thing all sorted, thank God! It was the font I was using not showing the degree symbol, or showing as a eclamation upside down symbol.

Next issue is trying to get me CPU and HDD temp added to my conky, so if anybody offering to send me a tutorial pls do. 

Cheers!!

---

### Post by glotz on 2009-02-23
Perhaps just check out [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

It's pretty straight forward.

---

