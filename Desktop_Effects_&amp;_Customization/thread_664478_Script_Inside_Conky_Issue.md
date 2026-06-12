---
title: "Script Inside Conky Issue"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by lvleph on 2008-01-11
I wrote my own weather script for conky. Everything displayed perfectly, but I decided to clean the code up and use functions. When I run the script from terminal it works perfectly, no errors. When I run the script inside conky I get no output. So I decided to see what was going on, and redirected the output ```
conky &> conky.log
``` This is when I noticed something quite weird. Conky is telling me there is an error with my script. ```
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
/home/erich/scripts/weather.sh: 5: Syntax error: "(" unexpected
``` This doesn't make any sense to me, because it works fine in terminal. Additionally, if I run a script inside conky, that calls the weather script, every thing works. Can someone tell me what is going on? Oh, and if I get rid of the () in the function definition, I then get an error relating to the {}.
**weather.sh**
[php]# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

#!/bin/bash

function cond_symb () { #get condition symbol and print it
	#cnd=$(cat "$file" | grep -A10 "class=\"titles\"" | head -n"$1" | tail -n1)
	#translate condition to symbol in weather font
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
}

function temp () { #get high and low temp and print it
	#get high temp
	hilo=$(cat "$file" | grep -A6 "class=\"temps\"" | head -n"$1" | tail -n1)
	tmp1=$(echo "$hilo" | cut -b19-22 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	#get low temp
	tmp2=$(echo "$hilo" | cut -b46-49 | awk '{ sub(/&/,"\n"); print}' | awk '{ sub(" ",""); print}' | head -n1)
	echo -e "$tmp1\0302\0260/$tmp2\0302\0260" #print the high and low temp
}

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
			5p displays 5th day's conditions
			c displays current temp in chosen system
			1 displays today's high/low temp in chosen system
			2 displays tomorrow's high/low temp in chosen system
			3 displays 3rd day's high/low temp in chosen system
			4 displays 4th day's high/low temp in chosen system
			5 displays 5th day's high/low temp in chosen system"
		;;
esac[/php]

**weather portion of .conkyrc**
```
${voffset -3}$alignc 3 DAY FORECAST
${voffset -7}$hr $color${endif}
${voffset -5}${font weather:size=50}${alignc}${execi 3600 ~/scripts/weather.sh USVA0652 f 1p}${execi 3600 ~/scripts/weather.sh USVA0652 f 2p}${execi 3600 ~/scripts/weather.sh USVA0652 f 3p}${font}$color
${alignc}${offset -20}${execi 3600 ~/scripts/weather.sh USVA0652 f 1}${offset 20}${execi 3600 ~/scripts/weather.sh USVA0652 f 2}${offset 20}${execi 3600 ~/scripts/weather.sh USVA0652 f 3}

```

---

