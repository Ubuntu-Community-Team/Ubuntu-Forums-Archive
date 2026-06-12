---
title: "Unity + Conky?"
date: 2011-05-08
forum: Desktop Environments
---

### Post by grayfox444 on 2011-05-08
I've tried searching but haven't found if conky is working with unity.
So, my question is firstly, is it?
And, secondly, can someone walk me through the installation? I tried to follow guides on Ubuntu 10.04 but it crashed my OS.
Thanks.

---

### Post by Frogs Hair on 2011-05-08
Yes , the conky-all package is running in unity as I type , but have not tried any configuration scripts yet . I'm sill in the hunt for a good tutorial .

---

### Post by grayfox444 on 2011-05-08
Yeah I definitely need some step-by-step easy-to-follow guide, last time i wrecked my OS.

---

### Post by Frogs Hair on 2011-05-08
I found a method to run a .conkyrc I found @ gnome look but when I try to run it I get an error . The script seems to be looking for library I don't have. This the error if anyone can help . 

Conky: invalid configuration file '/home/david/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

---

### Post by Frogs Hair on 2011-05-08
I have my Conky running ! The instructions I used stated that a folder be made in hidden folders for the .conkyrc and this was the problem. I simply had to copy and paste the newly named .conkyrc into the home directory with no folder. I chose this theme because I'm running unity.
[http://gnome-look.org/content/show.php/Horizontal+conky?content=140243](http://gnome-look.org/content/show.php/Horizontal+conky?content=140243)

---

### Post by Frogs Hair on 2011-05-08
This is the method I used for a Conky theme.

```
sudo apt-get install conky-all 

```
Copy and paste text from the theme download page to Gedit , save as .conkyrc and save to home . Open terminal , type conky and select enter.

---

### Post by grayfox444 on 2011-05-08
excellent, thank you

---

### Post by grayfox444 on 2011-05-08
i'm not savvy enough to recode this, is there an easy way to add the weather, perhaps headlines from news sites? things like that?

---

### Post by grayfox444 on 2011-05-08
if i click anywhere on the desktop whilst conky is running it vanishes, do you experience this as well?

---

### Post by Frogs Hair on 2011-05-08
Here are some themes I found after I installed and they should install the same way. I will see what I can find on the disappearing issue. I read something earlier about it.
[http://www.webupd8.org/2010/11/3-beautiful-conky-configurations.html](http://www.webupd8.org/2010/11/3-beautiful-conky-configurations.html)

---

### Post by ManualSparrow on 2011-05-08
It works in Xubuntu 11.04, and so should work with the main release as well. 
You need three things to get conky to run properly:
a) A conky install
b) A config file (or more than one)
c) An autostart program

a) For the install, just do ```
sudo apt-get install conky
```b) Normally, conky looks for a file in your home directory called .conkyrc - so for a basic, one-window conky, you can just create that file in the GUI by right-clicking in the home folder and creating a blank file, then renaming it. Or, type ```
gedit ~/.conkyrc
``` to create and open the file for editing (replace gedit with your default text editor, ie kate for KDE or mousepad for XFCE). You will want to fill that file with stuff something like ```
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type below
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer none

# Use Xft?
use_xft yes
xftfont Ubuntu:size=10
xftalpha 0.1
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
 minimum_size 200 1
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no 
draw_borders no
uppercase no
stippled_borders 0
border_width 0
default_color white
own_window_colour black
alignment bottom_right
gap_x 0
gap_y 0
default_bar_size 40 6

TEXT
${if_up wlan0}${color}${font PizzaDude Bullets:size=16}N${font}   ${wireless_essid wlan0} ${wireless_link_qual_perc wlan0}%${endif}
${color}${font PizzaDude Bullets:size=16}v${font}   Up:                ${upspeed eth0} | ${upspeed wlan0}
${font PizzaDude Bullets:size=16}r${font}   Down:          ${downspeed eth0} | ${downspeed wlan0}
${font PizzaDude Bullets:size=16}M${font}   Upload:       ${totalup eth0} | ${totalup wlan0}
${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0} | ${totaldown wlan0}
${font StyleBats:size=16}p${font}    Uptime: ${voffset 2} ${uptime_short}
${font StyleBats:size=18}8${font}    Battery: ${voffset 2} ${battery_percent}% ${battery_bar}
${font StyleBats:size=18}J${font}    CPU:    ${cpu cpu0}% ${cpubar cpu0}  ${cpu cpu1}% ${cpubar cpu1}
                        ${cpu cpu2}% ${cpubar cpu2}  ${cpu cpu3}% ${cpubar cpu3}
${font StyleBats:size=18}b${font}   Temp: ${voffset 2}CPU ${acpitemp}
${font PizzaDude Bullets:size=16}J${font}   RAM: ${voffset 2}   ${mem} / ${memmax}  ${memperc}%
```Of course, you will need all those fonts mentioned, and you will have to delete some of the CPU-related lines if you have only two processors, for example (otherwise it won't work). The fonts are [here]("http://dl.getdropbox.com/u/83257/conkyfonts.zip"), and I got them from[ this tutorial]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/") which I recommend reading even though it says pretty much the same thing.

c) Autostart by going into your system preferences and finding "Startup Applications" and adding the command "conky" to the list. Or, make a file called "conky_start" and make it executable by right-clicking it and changing the permissions, then add that file to the startup applications list instead. It should contain something like ```
#!/bin/bash
sleep 10
conky -c ~/.conky/.conkyrc_clock &
conky -c ~/.conky/.conkyrc_system &
conky -c ~/.conky/.conkyrc_text &
conky -c ~/.conky/.conkyrc_mail
```(Just correct the paths to fit wherever you are keeping your config files - as you can see I have 4 in a folder called .conky in the home directory (that's what ~/ is).

---

### Post by Frogs Hair on 2011-05-08
I resolved the disappearance issue.
1. Home Folder > Ctrl + H
2. Open .conkrc in the text editor 
3. scroll to this line :# Create own window instead of using desktop (required in nautilus)

4.change the directly under to read```
own_window_type_override yes
``` 
5.save and close the editor.

The whole section should look like this.```
# Create own window instead of using desktop (required in nautilus)
own_window_type_override yes
own_window_type desktop
own_window_transparent yes
#own_window_hints yes

```

Use Alt + F2 to run conky.

---

### Post by grayfox444 on 2011-05-08
I have everything working except the weather on this script. I can't figure it out because it seems the yahoo weather site has changed so the script doesn't match it properly.
Directions:
Now you need to know the location id for your location for weather info. Head to [http://weather.yahoo.com](http://weather.yahoo.com). Enter city or zip code for your location and click go. Copy the location ID from the adress bar. For examples the location id for Geneva, Switzerland is SZXX0013, for Kathmandu, Nepal is NPXX0003
Open pogodynka.sh file look for this line kod=USID0025. Replace USID0025 with the location ID you got from step 10 above

Code:
```
w3m -dump http://weather.yahoo.com/forecast/"$kod".html
```
I tried inserting the entire http link and removing the variable, but that doesn't seem to work either.
It seems like the weather.com forecast links are a different format now.
Any ideas?

---

### Post by grayfox444 on 2011-05-08
[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)
this is the guide i'm using. it seems everyone is having this weather issue because yahoo has changed their site. anything we can do?

i actually found the code i needed in the page source on yahoo, but it still isn't running.

when i run conky in terminal i get this error:
scripts/pogodynka.sh: 50: w3m: not found

that w3m is the line i pasted above, which is line 50 

here is the entire code if need be.

```
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Pogodynka 0.2.2.1													#
#															#
# azhag (azhag@bsd.miki.eu.org)												#
#															# 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i	#
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message.					#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Wymagane aplikacje:													#
# w3m - tekstowa przegl±darka www											#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															# 
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod".							#
#															#
# Aby ustaliæ kod swojego miasta wejd¿ na stronê http://weather.yahoo.com/ i wyszukaj tam swoje miasto. Kodem jest 	#
# koñcówka linka z pogod± naszego miasta.										#	
#															#
# Przyk³adowe kody:													#
# Warszawa - PLXX0028													#
# Kraków - PLXX0012													#
# Gdañsk - PLXX0005													#
# Szczecin - PLXX0025													#
#															#
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji		#
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych.			#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/scripts

# Kod miasta
kod=USDC0001

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
	#echo "Serwis niedostêpny"
  #else
	# pobieranie informacji
 	w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

	# ustalenie warto¶ci zmiennych
	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $1}'`
	tempo=`head -n6 $plik | tail -n1`
	cisn=`head -n8 $plik | tail -n1`
	wiatr=`head -n16 $plik | tail -n1`
	wilg=`head -n10 $plik | tail -n1`
	wsch=`head -n18 $plik | tail -n1`
	zach=`head -n20 $plik | tail -n1`
	if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
	  then
		stanpl=$stan
	  else
		stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
	fi
	
	# formatowanie informacji wyj¶ciowej
	# dostêpne zmienne:
	# $stan		opis stanu po angielsku
	# $stanpl	opis stanu po polsku
	# $temp		temperatura powietrza
	# $tempo	temperatura odczuwalna
	# $cisn		ci¶nienie atmosferyczne
	# $wiatr	kierunek, si³a wiatru
	# $wilg		wilgotno¶æ powietrza
	# $wsch		godzina wschodu s³oñca
	# $zach		godzina zachodu s³oñca
	
	#echo $stan
	#echo $stanpl
	echo $temp F  /  $tempo F
	#echo Cisnienie $cisn hPa
	#echo $wiatr
	#echo Wilgotno¶æ: $wilg
	#echo Wschód S³oñca: $wsch
	#echo Zachód S³oñca: $zach
	#echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# &#352;nieg
# Snow / Wind
# &#352;nieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# &#352;nieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# &#352;nieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# &#352;nieg z deszczem/Wiatr
# Rain / Snow / Wind
# &#352;nieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
# 
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
# 
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
# 
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
# 
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
# 
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d

```

---

### Post by ManualSparrow on 2011-05-09
You can use the NOAA site instead. I just looked into this myself, as I Gmail_parser stopped working after the upgrade (something to do with Python3, possibly) and I wanted something useful in the bottom left corner.

Do the last option of [these three options]("http://ubuntuforums.org/showthread.php?t=1156383") to use the NOAA xml feed for your area. Note what the URL looks like - it is an xml file (bunch of text and syntax in brackets) and ends in =dwhl. It won't work if you plug in the wrong URL. 

I personally thought this forecast was too detailed, so I just display the text for the next few days like this: ```
${execi 600 sh ~/Scripts/conky_forecast_nws/NWSforecast.sh}
${execi 600  sed -n '1p' ~/Scripts/conky_forecast_nws/t}
${execi 600  sed -n '2p' ~/Scripts/conky_forecast_nws/d | fold -w50}

${execi 600  sed -n '2p' ~/Scripts/conky_forecast_nws/t}
${execi 600  sed -n '4p' ~/Scripts/conky_forecast_nws/d}

${execi 600  sed -n '3p' ~/Scripts/conky_forecast_nws/t}
${execi 600  sed -n '6p' ~/Scripts/conky_forecast_nws/d}

${execi 600  sed -n '4p' ~/Scripts/conky_forecast_nws/t}
${execi 600  sed -n '8p' ~/Scripts/conky_forecast_nws/d}

${execi 600  sed -n '5p' ~/Scripts/conky_forecast_nws/t}
${execi 600  sed -n '10p' ~/Scripts/conky_forecast_nws/d}
```
Note that I'm keeping the files in a folder called Scripts (capital S) in my home folder, inside the conky_forecast_nws subfolder.

Good luck!

(I attached the file I downloaded from the other thread, just in case it goes away for some reason. Basically just make a folder called Scripts and extract the conky_forecast_nws folder to it, and you should be able to use my code above in your conky).

EDIT AGAIN:

[COLOR="Red"]Note that in the tutorial I posted, your folder (where the old weather script was) was called 'scripts,' but in mine it is called 'Scripts.' This is important. For any of these scripts you will need to double-check the paths.[/COLOR]

Also, nice job on fixing the window hints. You can also do the same thing by selecting your conky window in the advanced options of your window manager, such as compiz.

It is a good idea to run conky in a terminal rather than Alt+F2'ing it when you are debugging/configing, because you will be able to see the errors if there are any.

Also, attached a screenshot for a little guidance/suggestion. 

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) contains all of the variables you might want to add to your conky - for example I use ```
${head ~/Scripts/DesktopToDoList 20}
``` to spit out the to do list in the top left.

---

### Post by grayfox444 on 2011-05-15
thanks, i appreciate the reply.
it's giving me a URL error but it looks like everything is fine. so i'm not sure what the issue is. even if i use the original text in the file it says something like
wget missing URL

---

### Post by grayfox444 on 2011-05-15
i found this error in the terminal.
sed: can't read /home/name/Scripts/conky_forecast_nws/t: No such file or directory

---

### Post by ManualSparrow on 2011-05-15
You will have to extract that tar.gz in the Scripts folder, and make sure your weather script is executable. If you autostarted and got the URL error, it was probably because your internet connection wasn't established before you loaded conky. Try ```
killall conky
``` then go to your autostart file and execute it manually (just run it) and see if it works then.

---

### Post by grayfox444 on 2011-05-21
> **ManualSparrow said:**
> You will have to extract that tar.gz in the Scripts folder, and make sure your weather script is executable. If you autostarted and got the URL error, it was probably because your internet connection wasn't established before you loaded conky. Try ```
killall conky
``` then go to your autostart file and execute it manually (just run it) and see if it works then.

Where is this autostart file?

 Sorry I'm just getting to this now, I haven't been home.

---

### Post by grayfox444 on 2011-05-21
But I'm sure my internet connection was working properly at the time.

---

### Post by Schappenberg on 2011-11-23
> **Frogs Hair said:**
> I resolved the disappearance issue.
1. Home Folder > Ctrl + H
2. Open .conkrc in the text editor 
3. scroll to this line :# Create own window instead of using desktop (required in nautilus)

4.change the directly under to read```
own_window_type_override yes
```5.save and close the editor.

The whole section should look like this.```
# Create own window instead of using desktop (required in nautilus)
own_window_type_override yes
own_window_type desktop
own_window_transparent yes
#own_window_hints yes

```Use Alt + F2 to run conky.Hi Frogs Hair,
Thanks for your instructions, but when setup conky like recommended, there is an other problem:
all files and folders on the desktop are invisible, but when i move the mouse over the desktop the icons under the mouse pointer appear for a second and then disappear again.
Do you have any solution for that?
Thanks
Schappenberg

---

### Post by stinkeye on 2011-11-24
> 
[B]own_window_type_override yes
own_window_type desktop[/B]
own_window_transparent yes
#own_window_hints yes

Delete the line
```
own_window_type_override yes
```

and change the line ***own_window_type desktop *** to
```
own_window_type override
```


When using **own_window_type override** windows are not under the control of the window manager. Hints are ignored.Windows are below and sticky. 

When using **own_window_type normal** windows are under the control of the window manager and you must include another setting in the config for hints 
eg
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

**own_window_type desktop** causes problems when using nautilus to draw the desktop.(ie icons on the desktop)

---

### Post by werewolves on 2012-05-01
> **grayfox444 said:**
> if i click anywhere on the desktop whilst conky is running it vanishes, do you experience this as well?

I am having the same problem on 12.04/Unity, except that conky just winks out for a second, then comes back.  None of the suggestions in this thread have helped, any other suggestions?

---

### Post by dhunt84971 on 2012-10-10
Having the same problem.  Bump.

---

### Post by oldos2er on 2012-10-10
Hi dhunt84971, please start a new thread for your problem.

---

