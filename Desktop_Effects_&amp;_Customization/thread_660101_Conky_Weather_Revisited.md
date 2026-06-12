---
title: "Conky Weather Revisited"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by lvleph on 2008-01-06
[COLOR="Red"][B]CAUTION

This bash script is no longer being updated, see my new thread: [Conky Weather Revisited V2](http://ubuntuforums.org/showthread.php?p=4130735#post4130735)[/B][/COLOR]


Well, I didn't really like the other conky weather scripts that were out there. They just didn't do what I wanted, so I made my own. I hope everyone likes it. 

**Step 1:** This conky setup uses a weather font, which I have attached.
To install the fonts follow the directions below.

1. Make the following directory as root:
```
# sudo mkdir /usr/share/fonts/truetype/myfonts
```
2. Copy the font(s) into the newly created directory:
```
# sudo cp [fonts] /usr/share/fonts/truetype/myfonts
```
3. Run the following to setup your fonts cache:
```
# fc-cache -f -v
```

**Step 2:** Save the following script in a file named **weather.sh** and place it in **~/scripts** folder. If you don't want the script to create the file /tmp/weather.html set update=0.
```
# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

#the following commented out code is not implemented correctly yet
#function cond_symb () { #get condition symbol and print it
	#cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
	#translate condition to symbol in weather font
#	if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
#		echo 'c'
#	elif echo "$cnd" | grep -E -i -q 'fair|sun|clear'; then
#		echo 'A'
#	elif echo "$cnd" | grep -E -i -q 'cloud'; then
#		echo 'e'
#	elif echo "$cnd" | grep -E -i -q 'storm|thunder|t\-'; then
#		echo 'i'
#	elif echo "$cnd" | grep -E -i -q 'snow'; then
#		echo 'k'
#	elif echo "$cnd" | grep -E -i -q 'rain'; then
#		echo 'h'
#	elif echo "$cnd" | grep -E -i -q 'shower'; then
#		echo 'g'
#	fi
#}

#function temp () { #get high and low temp and print it
	#get high temp
#	hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1)
#	tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	#get low temp
#	tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
#	echo -e "$tmp1\0302\0260/$tmp2\0302\0260" #print the high and low temp
#}

code=$1 #zipcode or weather.com city code
system=$2 #f for imperial c for metric
file=/tmp/weather.html #temp file holding weather
update=3600 #time in seconds to update file if set to 0 don't use file

if echo "$3" | grep -E -i -q 'c'; then
	update=0
fi

if [ $update -eq 0 ]; then
	age=1
else 
	#check to see if file exists
	if [ ! -e $file ]; then
		touch "/tmp/weather.html"
		age=3601
	else
		age=$(($(date +%s) - $(stat -c '%Y' "$file"))) #age of file in seconds
	fi
fi

if [ $age -gt  $update ]; then #check for age of file and if option was c
	#Check to see if server is available
	if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]; then
		echo "Service not available"
		exit
	fi
	
	if [ $update -eq 0 ]; then
		#get weather directly from site
		file=$(wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html)
	else
		#get new weather file
		wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html &> "$file"
	fi
fi

case "$3" in
	cp) #give me the symbol for the current condition
		cnd=$(cat "$file" | grep -A1 "Current conditions as of" | tail -n1)
		#cond_symb #get condition symbol and print it
		if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
			echo 'c'
		elif echo "$cnd" | grep -E -i -q 'fair|sun|clear'; then
			echo 'A'
		elif echo "$cnd" | grep -E -i -q 'cloud'; then
			echo 'e'
		elif echo "$cnd" | grep -E -i -q 'storm|thunder|t\-'; then
			echo 'i'
		elif echo "$cnd" | grep -E -i -q 'snow'; then
			echo 'k'
		elif echo "$cnd" | grep -E -i -q 'rain'; then
			echo 'h'
		elif echo "$cnd" | grep -E -i -q 'shower'; then
			echo 'g'
		fi
		;;
	c) #give me current temp
		tmp=$(cat "$file" | grep -A1 "\"forecast\-temperature\"" | tail -n1 | cut -b5-8 | awk 'sub(/&d/,"")')
		echo "$tmp\0302\0260"
		;;
	[1-5]p) #give me the symbol for the conditions
		#get conditions
		day=$(echo "$3" | awk 'sub(/p/,"")') #get day
		head=$((2*$day+1)) #translate day into number of lines
		cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$head" | tail -n1)
		#cond_symb #get condition symbol and print it
		if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
			echo 'c'
		elif echo "$cnd" | grep -E -i -q 'fair|sun|clear'; then
			echo 'A'
		elif echo "$cnd" | grep -E -i -q 'cloud'; then
			echo 'e'
		elif echo "$cnd" | grep -E -i -q 'storm|thunder|t\-'; then
			echo 'i'
		elif echo "$cnd" | grep -E -i -q 'snow'; then
			echo 'k'
		elif echo "$cnd" | grep -E -i -q 'rain'; then
			echo 'h'
		elif echo "$cnd" | grep -E -i -q 'shower'; then
			echo 'g'
		fi
		;;	
	[1-5]) #give me today's weather
		#get high and low
		head=$(($3+1)) #translate day into number of lines
		#temp $head #get high and low temp and print it
		hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$head" | tail -n1)
		tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
		#get low temp
		tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
		echo "$tmp1\0302\0260/$tmp2\0302\0260" #print the high and low temp
		;;
	*) #didn't use correct option 
		echo "Usage error weather.sh <citycode> <system> <option>
	weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 5th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac
```

The usage of the **weather.sh** script above is as follows (also see: Step 4)
```
weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 5th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system
```

**Step 3:** Make **weather.sh** executable.
```

sudo chmod a+x ~/scripts/weather.sh

```


To prevent the use of a weather file set update to 0. You can also adjust how often the file is updated through the same variable.

**Step 4:** Add this code to your **conky** file, changing "**USVA0652**" for your city code or ZIP code if you live in the USA, Replace "f" with "c" if you want metric degrees. Most likely the formatting won't line up perfectly for you at first, because of fonts and window sizing, so play with it a bit.
```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 5}

```

**NOTE:** This script is very dependent on the html tagging used by weather.com, so when they change that tagging this script won't work any more. However, I plan on staying on top of things like that. Just post here if you have any issues.

**EDIT:Updated 11 January 08**: Conky could not run script properly so code has been reorganized to allow conky to run the script
**EDIT:Updated 10 January 08**: Fixed /tmp/weather.html does not exist error. Also, added the ability to not use a file. Set update to 0 to use that feature.
**EDIT:Updated 10 January 08**: Optimized condition code because cloudy and clouds could be replaced with cloud. Sunny and sun could be replaced with just sun. 
**EDIT:Updated 10 January 08**: Added ability to obtain current conditions
**EDIT:Updated 10 January 08**: I noticed that sometimes there are AM Clouds PM Sun. Neither Sun nor Clouds were listed, so I have added those. Also, I have the script download to a file instead of it being read directly to a variable. Also, it now uses the same file for an hour and after an hour it downloads the file again. Except when current temp is asked for in which case it will download every time you call it.
**EDIT:Updated 09 January 08**: Degree symbol should be fixed and work for anyone using utf-8. 
**EDIT:Updated 09 January 08**: Fixed the clear issue. Sorry thought I already implemented that fix.
**EDIT:Updated 08 January 08**: Fixed another issue where high and low are both three characters and corrected a problem with single digits.
**EDIT:Updated 08 January 08**: Optimized code for readability and less wget calls.
**EDIT:Updated 08 January 08**: Added clear to the conditions.
**EDIT:Updated 07 January 08**: Fixed 3 character issue.
**EDIT:Updated 07 January 08**: Fixed issues with reading weather.com formatting and added a 5th day to the forecast. Also, changed the option parameters

---

### Post by lvleph on 2008-01-06
I fixed some bugs with the code. Please point out any additional bugs.

---

### Post by lvleph on 2008-01-07
Definitely still had some bugs in my code. Specifically dealing with formatting issues.  I have taken a completely different strategy.

I know of two cases in which it still has issues. The two cases are when the temperature is negative or over 100. I am still working on this issue and I hope to have that solved very shortly. Anyone with any ideas?

I also added the ability to have a 5 day forecast. The inability to use 5 day was because of formatting issues and that is why I left it out. However, I solved that with the new strategy. I also changed the option commands.

EDIT: Single Negative digits work. Once there are more than 2 digits is when there is a problem.

---

### Post by lvleph on 2008-01-07
I have fixed the issue with 3 character temperatures and for those living in the bitter cold I have addressed the 4 character problem.

---

### Post by valucha on 2008-01-07
[COLOR="DarkOrchid"]Hi... there is a problem with this line
> 		elif echo "$cnd" | grep -E -i -q 'fair|sunny'; then in many cases yahoo.com use "clear" in stead of "fair" or "sunny" because it's on night and it's not sunny ;)... so you only have to add |clear and problem solved :).

Sorry about my English, I'm from Argentina... bye
[/COLOR]

---

### Post by Bruce M. on 2008-01-07
> **valucha said:**
> [COLOR="DarkOrchid"]Hi... there is a problem with this line
 in many cases yahoo.com use "clear" in stead of "fair" or "sunny" because it's on night and it's not sunny ;)... so you only have to add |clear and problem solved :).

Sorry about my English, I'm from Argentina... bye
[/COLOR]

Hola DarkOrchid

Your English is fine.
By add do you mean like this:

```

 elif echo "$cnd" | grep -E -i -q 'fair|sunny|clear'; then

```

I have to try this.

Bruce

---

### Post by lvleph on 2008-01-08
I actually didn't even write that portion of the code, so I didn't even think of that. Thank you very much. I am going to look over the weather font and see if there is something better for clear rather than a sun. 

I added clear to the conditions. My next goal is to clean up the code a bit. I have never written a bash script, so it is a little messy.

EDIT: There is a moon (9), but I am not sure if it is any better than just using the sun.

---

### Post by lvleph on 2008-01-08
I am not at home right now, so I cannot test this, but here is my new optimized version of Conky Weather. Tell me if you get any errors running it from terminal. It is definitely alpha, since it has never even been tested yet.
 
code deleted because it didn't work.

---

### Post by Goofy666 on 2008-01-08
I'll give it a try asap. With the first version, I also encountered a lot of formatting problems, couldn't figure them out after trying several (combinations of) commands. It's nice to hear that it isn't an exception. Thanks for putting the time and effort in it!

---

### Post by lvleph on 2008-01-08
> **Goofy666 said:**
> I'll give it a try asap. With the first version, I also encountered a lot of formatting problems, couldn't figure them out after trying several (combinations of) commands. It's nice to hear that it isn't an exception. Thanks for putting the time and effort in it!

Yeah, I was trying to read things directly from the web output instead of the html code. Once I started using the html code instead it became much easier. Not sure why I didn't do that in the first place. I guess because the original weather that I based mine off didn't use the html.

I am unsure if the function calls have to come first or not. so if you get some errors with the function call try moving them to the beginning of the code. It is certainly prettier and shorter now. Hopefully, it just works.

---

### Post by lvleph on 2008-01-08
I had a few issues with the newest conky script, but they are fixed now. However, my ° does not display correctly any more. Any one know how to fix this issue. I think it may have stemed from writing my code in windows. However, I copied the ° from linux and it still is not working.

```
# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

function cond_symb(){
	cnd=$(echo echo "$weather" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
			#translate condition to symbol in weather font
			if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
				echo 'c'
			elif echo "$cnd" | grep -E -i -q 'fair|sunny|clear'; then
				echo 'A'
			elif echo "$cnd" | grep -E -i -q 'cloudy'; then
				echo 'e'
			elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
				echo 'i'
			elif echo "$cnd" | grep -E -i -q 'snow'; then
				echo 'k'
			elif echo "$cnd" | grep -E -i -q 'rain'; then
				echo 'h'
			elif echo "$cnd" | grep -E -i -q 'shower'; then
				echo 'g'
			fi
}

function temp(){
	#get high temp
	tmp1=$(echo "$weather" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1 | cut -b19-22 | awk 'sub(/&d/,"")')
	#get low temp
	tmp2=$(echo "$weather" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1 | cut -b46-49 | awk 'sub(/&d/,"")')
	echo "$tmp1°/$tmp2°" #print the high and low
}

code=$1 #zipcode or weather.com city code
system=$2 #f for imperial c for metric

#Check to see if server is available
if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]; then
	echo "Service not available"
	exit
fi

#get the weather forecast
weather=$(wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html)

case "$3" in
	c) #give me current temp
		tmp=$(echo "$weather" | grep -A1 "\"forecast\-temperature\"" | tail -n1 | cut -b5-8 | awk 'sub(/&d/,"")')
		echo "$tmp°"
		;;
	[1-5]p) #give me the symbol for the conditions
		day=$(echo "$3" | awk 'sub(/p/,"")') #get day
		head=$[2*$day+1] #translate day into number of lines
		cond_symb $head #get condition symbol and print it
		;;
	[1-5]) #give me the high and low temps 
		head=$[$3+1] #translate day into number of lines
		temp $head #get high and low temps and print them
		;;
	*) #didn't use correct option 
		echo "Usage error weather.sh <citycode> <system> <option>
	weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			c displays current temp in chosen system
			1p displays today's conditions in the chosen system
			2p displays tomorrow's conditions in chosen system
			3p displays 3rd day's conditions in chosen system
			4p displays 4th day's conditions in chosen system
			5p displays 4th day's conditions in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac
```

---

### Post by lvleph on 2008-01-08
Okay, the degree issue has been fixed and so I have update the origingal code.

---

### Post by lvleph on 2008-01-08
This is sort of funny. For some reason conky will not run my script. I can run it from a terminal and it works just fine, but nothing is displayed in conky. Here is my conkyrc
```
# UBUNTU-CONKY.
#

# Update interval in seconds
update_interval 1.0
total_run_times=0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 250

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Candera:size=7
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color0 97b9f4
color1 orange
color2 red
color3 green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right


# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignc}${offset -20}${color0}${font Arial:bold:size=12}${time %H:%M:%S}$font
${alignc}${time %A}, ${time %d %B %G}$color
${color1}$hr
${voffset -3}$alignc GMAIL
${voffset -9}$hr $color
${voffset -5}${color}You have ${color3}${texeci 100 python ~/scripts/gmail.py} ${color}new email(s).
${if_empty ${execi 100 python ~/scripts/gmail_subj.py}}${color1}$hr
${voffset -3}$alignc 3 DAY FORECAST
${voffset -9}$hr $color
${else}${execi 100 python ~/scripts/gmail_subj.py}
${color1}$hr
${voffset -3}$alignc 3 DAY FORECAST
${voffset -9}$hr $color${endif}
${voffset -10}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${font}$color
${alignc}${offset -10}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}
${color1}$hr
${voffset -3}$alignc SYSTEM
${voffset -9}$hr $color
${exec cat /etc/issue.net}
$sysname Kernel $kernel ($machine)
Uptime: $uptime
Battery status: $acpiacadapter, $battery 
${color1}$hr
${voffset -3}$alignc PROCESSES
${voffset -9}$hr $color
${alignc}Processes: $processes  Running: $running_processes
${color1}NAME${alignr}PID      CPU%     MEM%$color
${top name 1}${alignr}${offset -40}${top pid 1}${offset 15}${top cpu 1}${offset 15}${top mem 1}
${top name 2}${alignr}${offset -40}${top pid 2}${offset 15}${top cpu 2}${offset 15}${top mem 2}
${top name 3}${alignr}${offset -40}${top pid 3}${offset 15}${top cpu 3}${offset 15}${top mem 3}
${color1}$hr
${voffset -3}$alignc CPU/MEM
${voffset -9}$hr $color
${voffset -5}${cpugraph 50,250 000000 ff0000}
${voffset -55}${execi 1000 head /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | cut -b 0-20,31-48}
Clock: ${freq}MHz${alignr}Usage: ${cpu}%        Temp: ${acpitemp}C
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
${color1}$hr
${voffset -3}$alignc FILE SYSTEM
${voffset -9}$hr $color
Root:  ${fs_free}/${fs_size /} ${fs_bar 6 /}
Home:  ${fs_free /home}/${fs_size /home} ${fs_bar 6 /home}
${if_mounted /media/samba/}Samba:  ${fs_free /media/samba}/${fs_size /media/samba} ${fs_bar 6 /media/samba}
${color1}$hr 
${else}${color1}$hr $endif
${voffset -3}$alignc NETWORK
${voffset -9}$hr $color
${if_empty ${exec python ~/scripts/wifiUp.py}}${voffset -5}${downspeedgraph eth0 55,124 000000 ff0000} ${upspeedgraph eth0 55,124 000000 00ff00}$color
${voffset -60}${alignc}WIRED
Local IP: ${addr eth0} $alignr Public IP: ${execi 18000 ~/scripts/myip.sh}
Down: ${downspeed eth0} kb/s $alignr Up: ${upspeed eth0} kb/s
Total: ${totaldown eth0} $alignr Total: ${totalup eth0}
${else}${voffset -5}${downspeedgraph wlan0 64,124 000000 ff0000} ${upspeedgraph wlan0 64,124 000000 00ff00}$color
${voffset -69}${alignc}ESSID:"${wireless_essid wlan0}"
Local IP: ${addr wlan0} $alignr Public IP: ${execi 1800 ~/scripts/myip.sh}
Signal: ${execi 1800 ~/scripts/wifiQ.sh}% $alignr Bit Rate: ${execi 18000 ~/scripts/wifiBR.sh} Mb/s
Down: ${downspeed wlan0} kb/s $alignr Up: ${upspeed wlan0} kb/s
Total: ${totaldown wlan0} $alignr Total: ${totalup wlan0}$endif
```

and here is my long list for ~/scripts
```

-rwxr-xr-x 1 erich erich  551 2007-12-02 12:44 conditions.sh
-rw-r--r-- 1 erich erich  16K 2008-01-01 15:38 gmail.html
-rwxr-xr-x 1 erich erich  469 2008-01-05 09:30 gmail.py
-rw-r--r-- 1 erich erich 1.9K 2008-01-04 16:16 gmail_subj2.py
-rwxr-xr-x 1 erich erich 1.9K 2008-01-06 12:34 gmail_subj.py
-rwxr-xr-x 1 erich erich  111 2008-01-04 16:54 myip.sh
-rwxr-xr-x 1 erich erich 2.8K 2008-01-08 17:18 weather.sh
-rwxr-xr-x 1 erich erich   62 2008-01-01 17:05 wifiBR.sh
-rwxr-xr-x 1 erich erich   51 2008-01-01 17:09 wifiQ.sh
-rwxr-xr-x 1 erich erich  126 2008-01-02 17:34 wifiUp.py
```

---

### Post by lvleph on 2008-01-08
I have been testing some more and I discovered a problem with high and low if they are both negative or three characters. Also, had an issue with single digit temps. I believe it is fixed.

Note: It is difficult testing all of these combos, mostly because of the way I am testing. I am testing by getting info directly from weather.com and so I have to figure out what places might have certain conditions. I suppose I could use a file instead.

EDIT And I am still having conky issues.

---

### Post by Goofy666 on 2008-01-09
> **lvleph said:**
> I suppose I could use a file instead.

You mean like a local temporary file?

Btw, the ° that won't show, is it something like  'Â' (a capital A with a ^ on top of it)? This is what was displayed when I included the script in Conky (the first version), although the ° still stood behind that weird 'a'.

---

### Post by lvleph on 2008-01-09
No it was a question mark. I think the issue with this is wholly to do with locale settings in Ubuntu. I am trying to figure out how to encode ascii code into a bash script and this should solve that problem.

Everything displays fine for me when running from the script, but now I get nothing in conky. Is anyone else having this issue?

EDIT: I believe \167 in place of ° should do the trick.

I got the info from [here](http://www.pantz.org/software/shell/enhancingshellprompt.html). It has color escapes too, but I am pretty sure that is overridden by conky.

---

### Post by Bruce M. on 2008-01-09
> **lvleph said:**
> No it was a question mark. I think the issue with this is wholly to do with locale settings in Ubuntu. I am trying to figure out how to encode ascii code into a bash script and this should solve that problem.

Everything displays fine for me when running from the script, but now I get nothing in conky. Is anyone else having this issue?

EDIT: I believe \167 in place of ° should do the trick.

I got the info from [here](http://www.pantz.org/software/shell/enhancingshellprompt.html). It has color escapes too, but I am pretty sure that is overridden by conky.

 I have a Spanish keyboard and ° is just a [shift] + [the key to the left of the #1 key] and it shows up in conky just fine.

---

### Post by lvleph on 2008-01-09
> **Bruce M. said:**
> I have a Spanish keyboard and ° is just a [shift] + [the key to the left of the #1 key] and it shows up in conky just fine.

Well, for those that are having the issue, I do believe it is with your locale settings. However, adding \167 only results in 167 being printed.

---

### Post by Bruce M. on 2008-01-09
> **lvleph said:**
> Well, for those that are having the issue, I do believe it is with your locale settings. However, adding \167 only results in 167 being printed.

Sorry I didn't mean to sound like a "smart alec".
I've been watching this thread and your work with interest. I would love to see you get it working. I admit, it's because I'd like to try it.  :)

I can't help you because I don't know how to program.

But try this coding:  °

Found it in the Character Map app (see attached)

Bruce

EDIT: Obviously the coding worked as the line shows the ° symbol instead of the coding.
Remove the _ from this and try it:  _&_#_1_7_6_;_

---

### Post by lvleph on 2008-01-09
Does the program not work for you? No one has informed me that it doesn't work. I can't address any issues until I am told what the issues are. As of right now all I know about is the °, and I am going to try your solution here in a moment and report back.

If you are having an issue you can look at the code directly and change the part where you see
```
echo "$tmp1°/$tmp2°"
```
This is line 31. Just type in the symbol you described earlier in place of the messed up one. I also didn't think you were being a "smart alec". I am glad I am getting some feed back.

EDIT: the & # 176 doesn't work. I remember trying it earlier. That is the html encoding. There is a different one for bash.

---

### Post by lvleph on 2008-01-09
Okay, I had to use the following to get the degree symbol. This may not work with all fonts, but it should work with most.

```
echo -e "$tmp1\0302\0260/$tmp2\0302\0260"
```

---

### Post by lvleph on 2008-01-09
I have been looking into my conky problems. It definitely seems to be an issue with my script. Has anyone else experienced this issue with the new version?

---

### Post by lvleph on 2008-01-09
This is the dumbest thing I have ever seen.The way I got the script to display was by writing another script. Here it is.

```
#!/bin/bash

~/scripts/weather.sh $1 $2 $3
```

And then I named it weather2.sh. 
Made it executable 
```
chmod a+x ~/scripts/weather2.sh
```
Changed my .conkyrc to call that instead of weather.sh. How stupid. I am going to try and figure this out still.

---

### Post by tad1073 on 2008-01-10
How do I make the weather.sh file or all the .sh files I have in home/thomas/.scripts for that matter.

---

### Post by lvleph on 2008-01-10
I just use gedit.

```
gedit ~/scripts/weather.sh
```
That will create the file. Now just paste the code into it, and then save, exit and type ```
chmod a+x ~/scripts/weather.sh
```
To make it executable.

---

### Post by lvleph on 2008-01-10
I noticed that sometimes there are AM Clouds PM Sun. Neither Sun nor Clouds were listed, so I have added those. Also, I have the script download to a file instead of it being read directly to a variable. Also, it now uses the same file for an hour and after an hour it downloads the file again. Except when current tempis asked for in which case it will download every time you call it.

---

### Post by lvleph on 2008-01-10
I have added the ability to get your current conditions.

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> Does the program not work for you? No one has informed me that it doesn't work. I can't address any issues until I am told what the issues are. As of right now all I know about is the °, and I am going to try your solution here in a moment and report back.

I don't know if it works on my machine yet.  Haven't tried it due to being busy with other things up until now.  Today I'm going to play with it.  :)

> **lvleph said:**
> If you are having an issue you can look at the code directly and change the part where you see
```
echo "$tmp1°/$tmp2°"
```
This is line 31. Just type in the symbol you described earlier in place of the messed up one. I also didn't think you were being a "smart alec". I am glad I am getting some feed back.

It is my lack of programming expertize that sometimes doesn't come across right at times. But I still endeavour to help where I can.

> **lvleph said:**
> EDIT: the & # 176 doesn't work. I remember trying it earlier. That is the html encoding. There is a different one for bash.

Never thought of that due to my previous statement.
Anyway I'm off to try it now.

Bruce

---

### Post by Bruce M. on 2008-01-10
```

bruloo@The-Team:~$ fc-cache -f -v 
/usr/share/fonts: caching, 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, 0 fonts, 24 dirs
/usr/share/fonts/truetype/arphic: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/baekmuk: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/latex-xft-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, 60 fonts, 0 dirs
/usr/share/fonts/truetype/myfonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, 27 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-devanagari-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gentium: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gujarati-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: caching, 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-mgopen: caching, 16 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: caching, 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, 35 fonts, 0 dirs
/usr/share/X11/fonts: caching, 0 fonts, 6 dirs
/usr/share/X11/fonts/100dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/75dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/Type1: caching, 8 fonts, 0 dirs
/usr/share/X11/fonts/encodings: caching, 0 fonts, 1 dirs
/usr/share/X11/fonts/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/misc: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/util: caching, 0 fonts, 0 dirs
/usr/local/share/fonts: caching, 0 fonts, 0 dirs
/home/bruloo/.fonts: skipping, no such directory
/var/lib/defoma/fontconfig.d: caching, 0 fonts, 28 dirs
/var/lib/defoma/fontconfig.d/A: caching, 14 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: caching, 11 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/C: caching, 12 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: caching, 24 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/E: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/F: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/G: caching, 16 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/I: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/K: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/L: caching, 10 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/M: caching, 19 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/N: caching, 25 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/O: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/P: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/R: caching, 3 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/S: caching, 7 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/T: caching, 30 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/V: caching, 5 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/W: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/c: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/j: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/w: caching, 1 fonts, 0 dirs
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/bruloo/.fontconfig: cleaning cache directory
fc-cache: succeeded
bruloo@The-Team:~$ 

```

OK, did that but have a question on these lines:

```

/home/bruloo/.fonts: skipping, no such directory
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/bruloo/.fontconfig: cleaning cache directory
fc-cache: succeeded

```

 1. skipped - Do I need it?
 2. not cleaning unwritable cache directory - Don't understand?
 3. cleaning cache directory - What does this mean?

Bruce

---

### Post by Goofy666 on 2008-01-10
> **lvleph said:**
> This is the dumbest thing I have ever seen.The way I got the script to display was by writing another script. Here it is.

```
#!/bin/bash

~/scripts/weather.sh $1 $2 $3
```

And then I named it weather2.sh. Changed my .conkyrc to call that instead of weather.sh. How stupid. I am going to try and figure this out still.

Ouch... Such solutions, when found, always make me kind of disappointed. I'm glad you figured that out! Come to think about it... I also use such kind of scripts to invoke the gmail.py plugin, since I modified it to take arguments so I can use the same script for different accounts. Just because I thought it would be easier. Maybe it is safer to use such extra script whenever you need to pass arguments to a program/script, when including it in Conky.

> **Bruce M. said:**
>  1. skipped - Do I need it?
 2. not cleaning unwritable cache directory - Don't understand?
 3. cleaning cache directory - What does this mean?

1. Not really, unless you hold a fonts directory in your home. But that doesn't necessarily has to be like that.
2 & 3. A cache directory is a directory where (temporary) files get stored, when they need to be executed, or used by a script or... In this situation, nor 2 or 3 are a problem (2 says that some cache directory cannot be cleaned, because e.g. you don't have access to it, 3 means that a cache directory to which you do have access was cleaned).

---

### Post by Bruce M. on 2008-01-10
```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 5}

```

 1. I take it the "USVA0652" is what I would change to "ARBA0009" for Buenos Aires, and
 2. the 60000 is updating just over every 16 hours?

Bruce

---

### Post by lvleph on 2008-01-10
> **Bruce M. said:**
> ```

bruloo@The-Team:~$ fc-cache -f -v 
/usr/share/fonts: caching, 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, 0 fonts, 24 dirs
/usr/share/fonts/truetype/arphic: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/baekmuk: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/latex-xft-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, 60 fonts, 0 dirs
/usr/share/fonts/truetype/myfonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, 27 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-devanagari-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gentium: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gujarati-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: caching, 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-mgopen: caching, 16 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: caching, 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, 35 fonts, 0 dirs
/usr/share/X11/fonts: caching, 0 fonts, 6 dirs
/usr/share/X11/fonts/100dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/75dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/Type1: caching, 8 fonts, 0 dirs
/usr/share/X11/fonts/encodings: caching, 0 fonts, 1 dirs
/usr/share/X11/fonts/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/misc: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/util: caching, 0 fonts, 0 dirs
/usr/local/share/fonts: caching, 0 fonts, 0 dirs
/home/bruloo/.fonts: skipping, no such directory
/var/lib/defoma/fontconfig.d: caching, 0 fonts, 28 dirs
/var/lib/defoma/fontconfig.d/A: caching, 14 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: caching, 11 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/C: caching, 12 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: caching, 24 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/E: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/F: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/G: caching, 16 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/I: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/K: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/L: caching, 10 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/M: caching, 19 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/N: caching, 25 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/O: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/P: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/R: caching, 3 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/S: caching, 7 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/T: caching, 30 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/V: caching, 5 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/W: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/c: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/j: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/w: caching, 1 fonts, 0 dirs
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/bruloo/.fontconfig: cleaning cache directory
fc-cache: succeeded
bruloo@The-Team:~$ 

```

OK, did that but have a question on these lines:

```

/home/bruloo/.fonts: skipping, no such directory
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/bruloo/.fontconfig: cleaning cache directory
fc-cache: succeeded

```

 1. skipped - Do I need it?
 2. not cleaning unwritable cache directory - Don't understand?
 3. cleaning cache directory - What does this mean?

Bruce
Proceed and see what happens. If it doesn't display correctly it obviously didn't work. You will have to post a question about installing fonts on the boards, because I don't know what the issue is.

---

### Post by Bruce M. on 2008-01-10
> **Goofy666 said:**
> 1. Not really, unless you hold a fonts directory in your home. But that doesn't necessarily has to be like that.
2 & 3. A cache directory is a directory where (temporary) files get stored, when they need to be executed, or used by a script or... In this situation, nor 2 or 3 are a problem (2 says that some cache directory cannot be cleaned, because e.g. you don't have access to it, 3 means that a cache directory to which you do have access was cleaned).

Thanks Goofy666, so all is well, so far.  :)

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> Proceed and see what happens. If it doesn't display correctly it obviously didn't work. You will have to post a question about installing fonts on the boards, because I don't know what the issue is.

```
/usr/share/fonts/truetype/myfonts: caching, 1 fonts, 0 dirs
```

The fonts in question worked though   :)

---

### Post by lvleph on 2008-01-10
> **Bruce M. said:**
> ```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 5}

```

 1. I take it the "USVA0652" is what I would change to "ARBA0009" for Buenos Aires, and
 2. the 60000 is updating just over every 16 hours?

Bruce

Yeah change "USVA0652" to "ARBA0009. Truthfully I don't know how long 60000 is.

I remember reading that 100 was one second, but I am not sure if that is true. I should look that up.

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> Yeah change "USVA0652" to "ARBA0009. Truthfully I don't know how long 60000 is.

I remember reading that 100 was one second, but I am not sure if that is true. I should look that up.

Ok for BsAs but from what I read 1 is 1 second, in which case 60000 is 16 hours 40 minutes.

However: I have been known to be wrong before.  ;)

---

### Post by lvleph on 2008-01-10
My gmail.py is set to 100 and seems to load every second.

EDIT: I have read some more and I believe you are correct.

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> My gmail.py is set to 100 and seems to load every second.

EDIT: I have read some more and I believe you are correct.

You lost me!
100 would be: 1 min 40 seconds.
If you meant to say; "seems to load every minute" that would be correct.  ;)

Personally I'd set it to 5 (300) or 10 (600) minutes.  But then I have a "slow" machine.

EDIT: stilll working on this end.

---

### Post by Bruce M. on 2008-01-10
Getting this error:

```
Conky: /home/bruloo/.conkyscripts/ivlephweather: 22: no such configuration: 'qalignment'

```

Bruce

---

### Post by lvleph on 2008-01-10
Post your .conkyrc. I don't think it has anything to do with the weather script.

Oh by the way, in lvleph it is an l not an i. lvl is 1337 for M. lvleph is short for Mephistopheles.

---

### Post by Goofy666 on 2008-01-10
Can the script work well without placing the output in a local file? Once I was working on another script, for system temps, but I did not try to use such a method because it would generate a continuous disk load. In this case it is a bit more practical, but more when you update every hour or so, instead of every minute or less. But unless you really want your disk to go idle after a while, this shouldn't be a real issue.

On the other hand... Every time you execute a script the disk gets accessed as well, I think, but that's merely a read-action. It probably isn't worth the effort. Excuse me for the brainstorming in this topic :).

/edit: Nice to know about the name, It didn't occured to me that the first part is in 1337 :).

---

### Post by lvleph on 2008-01-10
I only have it check the file once an hour. That is built into the script. The only time it would read more often is when you are checking current conditions. The way I wrote the script there is no reason to have it update more than once an hour unless you are getting current conditions.

I will write an option not to use the file. You could go through the script and change it so that it doesn't, but you would have to change some conditional statements. Give me about an hour and I will have it working.

---

### Post by Goofy666 on 2008-01-10
If you feel it doesn't need such kind of option, please don't put your time and effort in it! I was wondering about it merely because I couldn't get a script to act that way myself recently.

Btw;

```
4p displays 4th day's conditions
5p displays 4th day's conditions
```

It is by far no critical bug, but hey :).

I gave the new version a try, but I got a flood of errors saying that /tmp/weather.tmp could not be found. After creating that myself, it only displayed some other conky errors... I'll have to get rid of those before I can get your script going :(.

---

### Post by Bruce M. on 2008-01-10
Being a non-techie, non-programing person I'm getting confused and having problems here. Let me see if I have this correct:

 **Step 1:** This conky setup uses a weather font, which I have attached.
To install the fonts follow the directions below.

 1. Make the following directory as root:
```
# sudo mkdir /usr/share/fonts/truetype/myfonts
```
 2. Copy the font(s) into the newly created directory:
```
# sudo cp [fonts] /usr/share/fonts/truetype/myfonts
```
 3. Run the following to setup your fonts cache:
```
# fc-cache -f -v
```

 **Step 2:** Save the following script in a file named **weather.sh** and place it in **~/scripts** folder.
```

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

function cond_symb(){ #get condition symbol and print it
	#cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
	#translate condition to symbol in weather font
	if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
		echo 'c'
	elif echo "$cnd" | grep -E -i -q 'fair|sunny|clear|sun'; then
		echo 'A'
	elif echo "$cnd" | grep -E -i -q 'cloudy|clouds'; then
		echo 'e'
	elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
		echo 'i'
	elif echo "$cnd" | grep -E -i -q 'snow'; then
		echo 'k'
	elif echo "$cnd" | grep -E -i -q 'rain'; then
		echo 'h'
	elif echo "$cnd" | grep -E -i -q 'shower'; then
		echo 'g'
	fi
}

function temp(){ #get high and low temp and print it
	#get high temp
	hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1)
	tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	#get low temp
	tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	echo -e "$tmp1°/$tmp2°" #print the high and low temp
}

code=$1 #zipcode or weather.com city code
system=$2 #f for imperial c for metric
file=/tmp/weather.tmp #temp file holding weather

age=$(($(date +%s) - $(stat -c '%Y' "$file"))) #age of file in seconds

if [ "$age" -gt 3600 ] || echo "$3" | grep -E -i -q 'c'; then #check for age of file and if option was c
	#Check to see if server is available
	if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]; then
		echo "Service not available"
		exit
	fi

	#get new weather file
	wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html &> "$file"
fi

case "$3" in
	cp) #give me the symbol for the current condition
		cnd=$(cat "$file" | grep -A1 "Current conditions as of" | tail -n1)
		cond_symb #get condition symbol and print it
		;;
	c) #give me current temp
		tmp=$(cat "$file" | grep -A1 "\"forecast\-temperature\"" | tail -n1 | cut -b5-8 | awk 'sub(/&d/,"")')
		echo -e "$tmp\0302\0260"
		;;
	[1-5]p) #give me the symbol for the conditions
		#get conditions
		day=$(echo "$3" | awk 'sub(/p/,"")') #get day
		head=$[2*$day+1] #translate day into number of lines
		cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$head" | tail -n1)
		cond_symb #get condition symbol and print it
		;;	
	[1-5]) #give me today's weather
		#get high and low
		head=$[$3+1] #translate day into number of lines
		temp $head #get high and low temp and print it
		;;
	*) #didn't use correct option 
		echo "Usage error weather.sh <citycode> <system> <option>
	weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 4th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac

```

The usage of the **weather.sh** script above is as follows (also see: Step 5)
```

weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 4th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system

```

 **Step 4:** Make **weather.sh** executable.
```

sudo chmod a+x ~/scripts/weather.sh

```

 **Step 5:** Add this code to your **conky** file, changing "**USVA0652**" for your city code or ZIP code if in the USA, and "f" to "c" if you want celcus degrees.
```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 5}

```

I guess that's it, is this the proper procedure?
Bruce

---

### Post by lvleph on 2008-01-10
> **Goofy666 said:**
> If you feel it doesn't need such kind of option, please don't put your time and effort in it! I was wondering about it merely because I couldn't get a script to act that way myself recently.

Btw;

```
4p displays 4th day's conditions
5p displays 4th day's conditions
```

It is by far no critical bug, but hey :).

I gave the new version a try, but I got a flood of errors saying that /tmp/weather.tmp could not be found. After creating that myself, it only displayed some other conky errors... I'll have to get rid of those before I can get your script going :(.

Okay, I have made it so that you can pick using a file or not. I also fixed the creation of the file and changed the file name to weather.html.

---

### Post by lvleph on 2008-01-10
> **Bruce M. said:**
> Being a non-techie, non-programing person I'm getting confused and having problems here. Let me see if I have this correct:

 **Step 1:** This conky setup uses a weather font, which I have attached.
To install the fonts follow the directions below.

 1. Make the following directory as root:
```
# sudo mkdir /usr/share/fonts/truetype/myfonts
```
 2. Copy the font(s) into the newly created directory:
```
# sudo cp [fonts] /usr/share/fonts/truetype/myfonts
```
 3. Run the following to setup your fonts cache:
```
# fc-cache -f -v
```

 **Step 2:** Save the following script in a file named **weather.sh** and place it in **~/scripts** folder.
```

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

function cond_symb(){ #get condition symbol and print it
	#cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
	#translate condition to symbol in weather font
	if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
		echo 'c'
	elif echo "$cnd" | grep -E -i -q 'fair|sunny|clear|sun'; then
		echo 'A'
	elif echo "$cnd" | grep -E -i -q 'cloudy|clouds'; then
		echo 'e'
	elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
		echo 'i'
	elif echo "$cnd" | grep -E -i -q 'snow'; then
		echo 'k'
	elif echo "$cnd" | grep -E -i -q 'rain'; then
		echo 'h'
	elif echo "$cnd" | grep -E -i -q 'shower'; then
		echo 'g'
	fi
}

function temp(){ #get high and low temp and print it
	#get high temp
	hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1)
	tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	#get low temp
	tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	echo -e "$tmp1°/$tmp2°" #print the high and low temp
}

code=$1 #zipcode or weather.com city code
system=$2 #f for imperial c for metric
file=/tmp/weather.tmp #temp file holding weather

age=$(($(date +%s) - $(stat -c '%Y' "$file"))) #age of file in seconds

if [ "$age" -gt 3600 ] || echo "$3" | grep -E -i -q 'c'; then #check for age of file and if option was c
	#Check to see if server is available
	if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]; then
		echo "Service not available"
		exit
	fi

	#get new weather file
	wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html &> "$file"
fi

case "$3" in
	cp) #give me the symbol for the current condition
		cnd=$(cat "$file" | grep -A1 "Current conditions as of" | tail -n1)
		cond_symb #get condition symbol and print it
		;;
	c) #give me current temp
		tmp=$(cat "$file" | grep -A1 "\"forecast\-temperature\"" | tail -n1 | cut -b5-8 | awk 'sub(/&d/,"")')
		echo -e "$tmp\0302\0260"
		;;
	[1-5]p) #give me the symbol for the conditions
		#get conditions
		day=$(echo "$3" | awk 'sub(/p/,"")') #get day
		head=$[2*$day+1] #translate day into number of lines
		cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$head" | tail -n1)
		cond_symb #get condition symbol and print it
		;;	
	[1-5]) #give me today's weather
		#get high and low
		head=$[$3+1] #translate day into number of lines
		temp $head #get high and low temp and print it
		;;
	*) #didn't use correct option 
		echo "Usage error weather.sh <citycode> <system> <option>
	weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 4th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac

```

The usage of the **weather.sh** script above is as follows (also see: Step 5)
```

weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 4th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system

```

 **Step 4:** Make **weather.sh** executable.
```

sudo chmod a+x ~/scripts/weather.sh

```

 **Step 5:** Add this code to your **conky** file, changing "**USVA0652**" for your city code or ZIP code if in the USA, and "f" to "c" if you want celcus degrees.
```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather.sh USVA0652 f 5}

```

I guess that's it, is this the proper procedure?
Bruce

Yes and I will update my how to.

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> Post your .conkyrc. I don't think it has anything to do with the weather script.

my conky for your weather script:
```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont Candara:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT
$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr
${voffset -5}${font weather:size=50}${alignc}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 1p}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 2p}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 3p}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 4p}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 5p}${font}
${alignc}${offset -15}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 1}${offset 10}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 2}${offset 10}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 3}${offset 10}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 4}${offset 10}${execi 60 ~/Documents/weather/iviephweather.sh ARDF0127 c 5}

```
I can't get it past displaying:
```

----------------------------
5 DAY FORECAST
----------------------------

```

```

sh: /home/bruloo/Documents/weather/iviephweather.sh: not found
sh: /home/bruloo/Documents/weather/iviephweather.sh: not found
sh: /home/bruloo/Documents/weather/iviephweather.sh: not found

```


> **lvleph said:**
> Oh by the way, in lvleph it is an l not an i. lvl is 1337 for M. lvleph is short for Mephistopheles.

so it's not ivieph then, but lvl.  Whatever the rest of that means I haven't a clue. :confused:
Will change it when I get it working.

---

### Post by lvleph on 2008-01-10
Are you sure that is where you place the weather script? I would check to make sure the file is actually there. If it is there ???See below for a possible solution.

EDIT: Where did you get that output?

---

### Post by lvleph on 2008-01-10
For anyone that has run the script through terminal and gets the proper output, but doesn't get anything through conky, follow [this post](http://ubuntuforums.org/showpost.php?p=4106393&postcount=23)

---

### Post by Bruce M. on 2008-01-10
> **lvleph said:**
> Are you sure that is where you place the weather script? I would check to make sure the file is actually there. If it is there ???See below for a possible solution.

EDIT: Where did you get that output?

**First:** Sorry about ducking out so fast, I had a personal problem that need attention immediately.

That output was in Terminal.
I had placed the weather script with my other weather scripts.

I changed my original "script" location to match your suggestion of **~/scripts**

file:///home/bruloo/scripts/weather.xslt
file:///home/bruloo/scripts/weather.sh
file:///home/bruloo/scripts/lvlephweather.sh

To start conky I have:
```
/home/bruloo/.startconky
```
Which is:
```

#!/bin/bash
sleep 30 &&
conky -c ~/.conkyscripts/conkymain;
sleep 1 &&
conky -c ~/.conkyscripts/conkyweather;
sleep 1 &&
conky -c ~/.conkyscripts/lvlephweather;

```

After putting my original *weather.xslt* and *weather.sh* in **~/scripts** and making the nessary changes I started my conkys with:
```
./.startconky
```

This is my **lvlephweather** conky file:
```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont Candara:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT
$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr
${voffset -5}${font weather:size=50}${alignc}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 1p}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 2p}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 3p}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 4p}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 5p}${font}
${alignc}${offset -15}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 1}${offset 10}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 2}${offset 10}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 3}${offset 10}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 4}${offset 10}${execi 60 ~/scripts/lvlephweather.sh ARDF0127 c 5}

```

and my **lvlephweather.sh** (which is executable: see attached)
```

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

function cond_symb(){ #get condition symbol and print it
	#cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
	#translate condition to symbol in weather font
	if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
		echo 'c'
	elif echo "$cnd" | grep -E -i -q 'fair|sunny|clear|sun'; then
		echo 'A'
	elif echo "$cnd" | grep -E -i -q 'cloudy|clouds'; then
		echo 'e'
	elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
		echo 'i'
	elif echo "$cnd" | grep -E -i -q 'snow'; then
		echo 'k'
	elif echo "$cnd" | grep -E -i -q 'rain'; then
		echo 'h'
	elif echo "$cnd" | grep -E -i -q 'shower'; then
		echo 'g'
	fi
}
First:
function temp(){ #get high and low temp and print it
	#get high temp
	hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1)
	tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	#get low temp
	tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	echo -e "$tmp1°/$tmp2°" #print the high and low temp
}

code=$1 #zipcode or weather.com city code
system=$2 #f for imperial c for metric
file=/tmp/weather.tmp #temp file holding weather

age=$(($(date +%s) - $(stat -c '%Y' "$file"))) #age of file in seconds

if [ "$age" -gt 3600 ] || echo "$3" | grep -E -i -q 'c'; then #check for age of file and if option was c
	#Check to see if server is available
	if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]; then
		echo "Service not available"First:
		exit
	fi

	#get new weather file
	wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html &> "$file"
fi

case "$3" in
	cp) #give me the symbol for the current condition
		cnd=$(cat "$file" | grep -A1 "Current conditions as of" | tail -n1)
		cond_symb #get condition symbol and print it
		;;
	c) #give me current temp
		tmp=$(cat "$file" | grep -A1 "\"forecast\-temperature\"" | tail -n1 | cut -b5-8 | awk 'sub(/&d/,"")')
		echo -e "$tmp\0302\0260"
		;;
	[1-5]p) #give me the symbol for the conditions
		#get conditions
		day=$(echo "$3" | awk 'sub(/p/,"")') #get day
		head=$[2*$day+1] #translate day into number of lines
		cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$head" | tail -n1)
		cond_symb #get condition symbol and print it
		;;	
	[1-5]) #give me today's weather
		#get high and low
		head=$[$3+1] #translate day into number of lines
		temp $head #get high and low temp and print it
		;;
	*) #didn't use correct option 
		echo "Usage error weather.sh <citycode> <system> <option>
	weather.sh <citycode> <system> <option>
		<citycode> - This can be either your zipcode or weather.com city code
		<system> - c for metric or f for imperial
		<option> - Only one option can be entered at a time
			cp displays current conditions
			1p displays today's conditions
			2p displays tomorrow's conditions
			3p displays 3rd day's conditions
			4p displays 4th day's conditions
			5p displays 4th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac

```

My *conkymain* and *conkyweather*  run fine, however *lvlephweather* is now having a different problem.

In Treminal:
```

bruloo@The-Team:~$ ./.startconky
Conky: forked to background, pid is 18190

Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2800005)
Conky: drawing to double buffer
Conky: forked to background, pid is 18202

Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2a00002)
Conky: drawing to double buffer
Conky: forked to background, pid is 18215
bruloo@The-Team:~$ 
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2e00002)
Conky: drawing to double buffer
bruloo@The-Team:~$ 

```

Below is a screenshot:
Bruce

[[IMG]http://img210.imageshack.us/img210/9338/3conkysiw7.th.png[/IMG]](http://img210.imageshack.us/my.php?image=3conkysiw7.png)

---

### Post by lvleph on 2008-01-10
looks like you didn't
```
chmod a+x ~/scripts/lvlephwether.sh
```
Try using sudo.
```
sudo chmod a+x ~/scripts/lvlephwether.sh
```

---

### Post by Bruce M. on 2008-01-11
> **lvleph said:**
> looks like you didn't
```
chmod a+x ~/scripts/lvlephwether.sh
```
Try using sudo.
```
sudo chmod a+x ~/scripts/lvlephwether.sh
```

I'm sure I did.  Anyway did it again and have different error:

```

bruloo@The-Team:~$ killall conky
bruloo@The-Team:~$ ./.startconky
Conky: forked to background, pid is 15053

Conky: desktop window (1000035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (1c00005)
Conky: drawing to double buffer
Conky: forked to background, pid is 15066

Conky: desktop window (1000035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2800002)
Conky: drawing to double buffer
Conky: forked to background, pid is 15077
bruloo@The-Team:~$ 
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
/home/bruloo/scripts/lvlephweather.sh: 5: Syntax error: "(" unexpected
Conky: desktop window (1000035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2a00002)
Conky: drawing to double buffer

```

---

### Post by lvleph on 2008-01-11
That is the exact same error I am having. I have a workaround for it. You will have to create a second script. I named mine weather2.sh. In that script place 

```
#!/bin/bash
~/scripts/weather.sh $1 $2 $3
```
Then in conky you replace the call for weather.sh with weather2.sh, and it will work. In your specific case you have your script named lvlephweather.sh, so replace weather.sh with lvlephweather.sh. I will post new code in an hour or so that will solve this problem. So you could just wait for that.

---

### Post by lvleph on 2008-01-11
For some reason conky doesn't allow bash functions, and so I reorganized the script to not use the bash functions. I am going to have to look into why conky executes bash scripts differently than on the terminal.

Anyway, the current script should work just fine. There may be little bugs in it, but I promise it will actually display in conky.

---

### Post by Goofy666 on 2008-01-12
> **lvleph said:**
> Okay, I have made it so that you can pick using a file or not. I also fixed the creation of the file and changed the file name to weather.html.

Thanks :). I'll try it asap.

> **lvleph said:**
> For anyone that has run the script through terminal and gets the proper output, but doesn't get anything through conky, follow [this post](http://ubuntuforums.org/showpost.php?p=4106393&postcount=23)

Maybe you should put that in your first post as well.

> **Bruce M. said:**
> ```

bruloo@The-Team:~$ ./.startconky
Conky: forked to background, pid is 18190

Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2800005)
Conky: drawing to double buffer
Conky: forked to background, pid is 18202

Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2a00002)
Conky: drawing to double buffer
Conky: forked to background, pid is 18215
bruloo@The-Team:~$ 
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
sh: /home/bruloo/scripts/lvlephweather.sh: Permission denied
Conky: desktop window (e00035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2e00002)
Conky: drawing to double buffer
bruloo@The-Team:~$ 

```]

Can you post the output you get when you run the following command?

```
$ ls -la /home/bruloo/scripts/
```

/edit: Nevermind this last question, I didn't notice lvleph's answers on the next page...

---

### Post by Bruce M. on 2008-01-12
> **lvleph said:**
> That is the exact same error I am having. I have a workaround for it. You will have to create a second script. I named mine weather2.sh. In that script place 

```
#!/bin/bash
~/scripts/weather.sh $1 $2 $3
```
Then in conky you replace the call for weather.sh with weather2.sh, and it will work. In your specific case you have your script named lvlephweather.sh, so replace weather.sh with lvlephweather.sh. I will post new code in an hour or so that will solve this problem. So you could just wait for that.

You'll have to add *something like this* on the first page of the thread, so people don't have to read multiple pages to get to it.:

**Step 5:** Now create a second weather script, **weather2.sh**. In that script place 
```

#!/bin/bash
~/scripts/weather.sh $1 $2 $3

```
**Step 6:** Make the script executable
```

sudo chmod a+x ~/scripts/weather2.sh

```

If you needed: *Step 5 & 6* follow with *Step 7*

**Step 7:** Replace the weather portion of your conky file with the following code:

```

${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${voffset -5}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather2.sh USVA0652 f 1p}${execi 60000 ~/scripts/weather2.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather2.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather2.sh USVA0652 f 4p}${execi 60000 ~/scripts/weather2.sh USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 60000 ~/scripts/weather2.sh USVA0652 f 1}${offset 10}${execi 60000 ~/scripts/weather2.sh USVA0652 f 2}${offset 10}${execi 60000 ~/scripts/weather2.sh USVA0652 f 3}${offset 10}${execi 60000 ~/scripts/weather2.sh USVA0652 f 4}${offset 10}${execi 60000 ~/scripts/weather2.sh USVA0652 f 5}

```

I'm going to apply the changes.  Will post results in a few minutes.
Bruce

**Added Info:**
 1. Posted screen shot
 2. In the new script you posted I forgot to change the code to °.
 3. Be right back.

---

### Post by Bruce M. on 2008-01-12
[CENTER]
[SIZE="6"]**HUSTON, WE HAVE LIFTOFF!**[/SIZE]

As evident in the screenshot - ***_"It Works!"_***

[[IMG]http://img221.imageshack.us/img221/6549/screen13jan08wf4.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screen13jan08wf4.png)

[/CENTER]

Curious how "tomorrows" forecasts don't match in the "**5 Day Forecast**" and the lower **Weather** (on the right).

Bruce

---

### Post by Bruce M. on 2008-01-12
[CENTER]
Made one more change, and it looks GREAT! Just have to work on the colours now. ;)

**lvleph: Thank you for all your hard work!**

[[IMG]http://img221.imageshack.us/img221/6549/screen13jan08wf4.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screen13jan08wf4.png)

[/CENTER]
Bruce

---

### Post by lvleph on 2008-01-12
Maybe there is AM Sun PM Showers. You could always check.
[http://weather.yahoo.com/forecast/ARDF0127_c.html](http://weather.yahoo.com/forecast/ARDF0127_c.html)
Looks like it worked perfectly.

Also, I have completely rewritten this script. Conky was buggy running bash, so I rewrote the script in Perl. However, now it doesn't have the ability to use no file. To run this in conky you replace the "~/scripts/weather.sh" with "perl ~/scripts/weather.pl". 
```
${execi 3600 perl ~/scripts/weahter.pl USVA0652 f 1p}
```

Everything else is the same. I have not decided if I should just link to that new version that I will be maintaining, or if I should just replace the one here. The current version on here is really buggy and kept breaking on me. Let me know what you guys think I should do.

[php]#!/usr/bin/perl

use Switch;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp }le holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

if(-e $file){ #does the file exist?
	$date=`date -u +%s`; #get current date in seconds
	$created=`stat -c %Y $file`; #get creation date of file in seconds
	$age=$date - $created; #determine age of file
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file");

$count=0; #set count so we can match proper day

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1°\n"; exit;}
			}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0;
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				cond_symb ($cnd); #translate conditions to symbol
				exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high°/$low°\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.sh <citycode> <system> <option>
weather.sh <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\t1p displays today's conditions
\t\t2p displays tomorrow's conditions
\t\t3p displays 3rd day's conditions
\t\t4p displays 4th day's conditions
\t\t5p displays 5th day's conditions
\t\tc displays current temp in chosen system
\t\t1 displays today's high/low temp in chosen system
\t\t2 displays tomorrow's high/low temp in chosen system
\t\t3 displays 3rd day's high/low temp in chosen system
\t\t4 displays 4th day's high/low temp in chosen system
\t\t5 displays 5th day's high/low temp in chosen system\n"
	}
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_\n";
}

close FILE;[/php]

---

### Post by lvleph on 2008-01-12
> **Bruce M. said:**
> [CENTER]
Made one more change, and it looks GREAT! Just have to work on the colours now. ;)

**lvleph: Thank you for all your hard work!**

[[IMG]http://img297.imageshack.us/img297/2519/screenshotxg9.th.png[/IMG]](http://img297.imageshack.us/my.php?image=screenshotxg9.png)
[/CENTER]
Bruce

I am going to need to see how you got the calendar working correctly. Mine won't line up. I think I read something about the font. I have been thinking about writing a script that so that you can highlight the current date.

---

### Post by Bruce M. on 2008-01-12
> **lvleph said:**
> I am going to need to see how you got the calendar working correctly. Mine won't line up. I think I read something about the font. I have been thinking about writing a script that so that you can highlight the current date.

Use a MONO font. Here's what I use:

```

${font DejaVu Sans Mono :size=8}${execi 60 cal -3 | cut -c23-64} $font

```

---

### Post by lvleph on 2008-01-12
Okay thanks, I will try that. But you didn't answer my other question. Should I let this thread die and start another for the new version, or should I keep it alive and just update? The current bash script keeps breaking. I am actually surprised yours is working, but maybe you don't have the latest version. i of course lost the last one.

---

### Post by Bruce M. on 2008-01-12
> **lvleph said:**
> Okay thanks, I will try that. But you didn't answer my other question. Should I let this thread die and start another for the new version, or should I keep it alive and just update? The current bash script keeps breaking. I am actually surprised yours is working, but maybe you don't have the latest version. i of course lost the last one.

You are using: [http://weather.yahoo.com/](http://weather.yahoo.com/)

The other script uses: [http://xoap.weather.com/](http://xoap.weather.com/)

If you are **NOT** going to keep this bash script updated.  Make a note in your initial post here ... similar to this:

[CENTER][SIZE="6"]CAUTION[/SIZE][/CENTER]

**This bash script is no longer being updated, see my new thread: Conky Weather Revisited 2 - Perl**

Now before you actually make that change and hit the [Submit Reply] button, create **Conky Weather Revisited 2 - Perl**. Then link to it in the message you will leave here.  :)

And start Fresh.
Trust me, I'll be there :)
Bruce

---

### Post by lvleph on 2008-01-13
New perl version can be found [here](http://ubuntuforums.org/showthread.php?p=4130735#post4130735).

This version will not longer be maintained.

---

