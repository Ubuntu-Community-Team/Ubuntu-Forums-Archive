---
title: "How to mark in conky in calender current day+centered?"
date: 2010-02-09
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-09
Hi,
i just want to have simple calender in my conky. I found here how to add it, but want to know is it possible to have marked current day and have calendar centered?
At the end there is line that marks current day but i can not get it centered.

[http://solutionsandtips.blogspot.com/2009/03/how-to-add-calendar-in-conky-linux.html](http://solutionsandtips.blogspot.com/2009/03/how-to-add-calendar-in-conky-linux.html)

Thanks

So, the line for calendar is
> ${font DejaVu Sans Mono :size=8}${exec cal -m | cut -c23-44 --complement}
The line for calendar with the current day marked is:
$> {execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color #b7d1ea}'"$DJS"'${color}'" "/} 

But if i try to add center the second line i get the calendar messed up.

---

### Post by vickoxy on 2010-02-10
So this is my conky:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes


# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 186 0
maximum_width 220 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
use_xft yes
xftfont Sans:size=8
xftalpha 0.8

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3



# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
${font Sans:size=26}${alignc}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```

and this is also on simple line, but can not adjust it:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'}
```

---

### Post by mobilediesel on 2010-02-10
> **vickoxy said:**
> So this is my conky:

and this is also on simple line, but can not adjust it:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'}
```

add [COLOR="Blue"]|sed 's/^/${alignc}/'[/COLOR] to the end like this:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'[COLOR="Blue"]|sed 's /^/${alignc}/'[/COLOR]}
```

---

### Post by Bruce M. on 2010-02-10
Hi vickoxy

Rather than look at yours, because I'm sure if you use an ${alignc} on it only the top half gets centred, here is one that does what you want and more:

```
${font DejaVu Sans Mono:bold:size=9}${execpi 3600 $HOME/Conky/scripts/conkycal.sh -l es|sed 's/^/\${goto 105}/'}${font}
```

[LIST=1]
[*]today is a different colour
[*] it is available in various languages.
[*] you can cetnre it with a ${goto} or ${alignc} I use a goto it os much more accurate.
[*] this calendar "always" displays 31 days: Feb ends at 28, the first three days of March are there in a different colour.  GREAT for spacing.
[/LIST]

I left the font call there as a MONO font is important for this calendar to be displayed correctly (any mono font)

Two things to look at in that line:

**[COLOR="Teal"]Language:[/COLOR]**
> conkycal.sh **[COLOR="Teal"]-l es[/COLOR]**|sed 's/^/\**[COLOR="DarkRed"]${goto 105}[/COLOR]**/'}
and the **[COLOR="DarkRed"]"spacing"[/COLOR]** you asked about.

**conkycal.sh** <<-- make this one executable.
```
#!/bin/bash
cd $(dirname $0)
# horizontal and vertical calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names
DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su")
while getopts ":vl:" opts; do
case "$opts" in
l) lang=$OPTARG;;
v) orientation="$opts";;
esac
done
if [ -f lang ]; then
    . lang
fi
COLOROLD="445566" #MidSlateGrey
COLORTODAY="FF8C00" #Darkorange
COLORREST="445566" #MidSlateGrey
COLORNEXT="778899" #LightSlateGrey
COLORSATURDAY="FFFF00"
COLORSUNDAY="FF8C00"
COLOR=("" "" "" "" "" "\${color $COLORSATURDAY}" "\${color $COLORSUNDAY}")
COLOREND=("" "" "" "" "" "" "\${color}")

TODAY=$(date +%-d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[$TODAY-1] days" +%u)

# horizontal function
h () {
# Build $TOPLINE
k=$FIRSTDAY
for j in {1..31}; do
  x=$[j+LASTDAY/j]
  case $j in
  	${j/#$x})	TOPLINE="$TOPLINE ${COLOR[$[k-1]]}${DOW[$[k-1]]}${COLOREND[$[k-1]]}";;
  	$[LASTDAY+1])	TOPLINE="$TOPLINE \${color $COLORNEXT}${DOW[$[k-1]]}";;
  	*)		TOPLINE="$TOPLINE ${DOW[$[k-1]]}";;
  esac
  k=$[${k/#7/0}+1]
done

BOTTOM="\${color $COLOROLD}$(seq -w -s ' ' $LASTDAY|sed "0,/[0-3]*$TODAY \?/s//\${color $COLORTODAY}&\${color $COLORREST}/") \${color $COLORNEXT}$(seq -w -s ' ' 0$[31-$LASTDAY])"

echo "${TOPLINE/# /}"
echo "$BOTTOM\${color}"
}

#vertical function
v () {
for i in $(seq 1 $[TODAY-1]); do
    TODAYC[$i]="\${color $COLOROLD}"
done
TODAYC[$TODAY]="\${color $COLORTODAY}"
for i in $(seq $[TODAY+1] $LASTDAY); do
    TODAYC[$i]="\${color $COLORREST}"
done

k=$FIRSTDAY
for j in $(seq $LASTDAY); do
  	echo  "${COLOR[$[k-1]]}${DOW[$[k-1]]} ${TODAYC[$j]}$(printf "%02d" $j)\${color}"
  k=$[${k/#7/0}+1]
done
}

# call function based on "$orientation"
${orientation:-h}
```

and in the same directory as that script the language file called: **lang**
```
case ${lang:-$LANG} in
	af* )  DOW=("Ma" "Di" "Wo" "Do" "Vr" "Sa" "So");;			# Afrikaans (Afrikaans)
	be* )  DOW=("&#1055;&#1072;" "&#1040;&#1118;" "&#1057;&#1077;" "&#1063;&#1072;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1053;&#1103;");;			# Belarusian (&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;)
	bs* )  DOW=("Po" "Ut" "Sr" "&#268;e" "Pe" "Su" "Ne");;			# Bosnian (Bosanac)
	bg* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1077;" "&#1057;&#1098;" "&#1053;&#1077;");;			# Bulgarian (&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;)
	zh* )  DOW=("&#21608;&#19968;" "&#21608;&#20108;" "&#21608;&#19977;" "&#21608;&#22235;" "&#21608;&#20116;" "&#21608;&#20845;" "&#21608;&#22825;");;		# Chinese (&#20013;&#25991;)
	hr* )  DOW=("Po" "Ut" "Ut" "Sr" "&#268;e" "Su" "Ne");;			# Croatian (Hrvatska)
	cs* )  DOW=("Po" "Út" "St" "&#268;t" "Pá" "So" "Ne");;			# Czech (&#268;eština)
	da* )  DOW=("Ma" "Ti" "On" "To" "Fr" "Lø" "Sø");;			# Danish (Dánština)
	nl* )  DOW=("Ma" "Di" "Wo" "Do" "Vr" "Za" "Zo");;			# Dutch (Nederlandse)
	de* )  DOW=("Mo" "Di" "Mi" "Do" "Fr" "Sa" "So");;			# German (Deutche)
	el* )  DOW=("&#916;&#949;" "&#932;&#961;" "&#932;&#949;" "&#928;&#941;" "&#928;&#945;" "&#931;&#940;" "&#922;&#965;");;			# Greek (&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;)
	et* )  DOW=("Es" "Te" "Ko" "Ne" "Re" "La" "Pü");;			# Estonian (Eesti)
	tl* )  DOW=("Lu" "Ma" "Mi" "Hu" "Bi" "Sa" "Li");;			# Filipino (Filipino)
	fi* )  DOW=("Ma" "Ti" "Ke" "To" "Pe" "La" "Su");;			# Finnish (Suomen)
	fr* )  DOW=("Lu" "Ma" "Me" "Je" "Ve" "Sa" "Di");;			# French (Français)
	gl* )  DOW=("Lu" "Ma" "Mé" "Xo" "Ve" "Sá" "Do");;			# Galician (Galego)
	hi* )  DOW=("&#2360;&#2379;&#2350;" "&#2350;&#2306;&#2327;&#2354;" "&#2348;&#2369;&#2343;" "&#2327;&#2369;&#2352;&#2369;" "&#2358;&#2369;&#2325;&#2381;&#2352;" "&#2358;&#2344;&#2367;" "&#2360;&#2370;&#2352;&#2381;&#2351;")	;;			# Hindi (&#2361;&#2367;&#2344;&#2381;&#2342;&#2368;)
	hu* )  DOW=("Hé" "Ke" "Se" "Cü" "Pé" "So" "Va");;			# Hungarian (Magyar)
	is* )  DOW=("Má" "Þr" "Mi" "Fi" "Fö" "La" "Su");;			# Icelandic (Íslenska)
	id* )  DOW=("Se" "Se" "Ra" "Ka" "Ju" "Sa" "Mi");;			# Indonesian (Indonesia)
	it* )  DOW=("Lu" "Ma" "Me" "Gi" "Ve" "Sa" "Do");;			# Italian (Italiano)
	ja* )  DOW=("&#26376;&#26332;" "&#28779;&#26332;" "&#27700;&#26332;" "&#26408;&#26332;" "&#37329;&#26332;" "&#22303;&#26332;" "&#26085;&#26332;");;		# Japanese (&#26085;&#26412;&#35486;) x
	ko* )  DOW=("&#50900;&#50836;" "&#54868;&#50836;" "&#49688;&#50836;" "&#47785;&#50836;" "&#44552;&#50836;" "&#53664;&#50836;" "&#51068;&#50836;");;		# Korean (&#54620;&#44397;&#50612;) x
	lv* )  DOW=("Pr" "Ot" "Tr" "Ce" "Pe" "Se" "Sv");;			# Latvian (Latviešu)
	lt* )  DOW=("pi" "an" "tr" "ke" "pe" "še" "se");;			# Lithuanian (Lietuviškai)
	mk* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1077;" "&#1057;&#1072;" "&#1053;&#1077;");;			# Macedonian (&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;)
	ml* )  DOW=("Is" "Se" "Ra" "Ra" "Ju" "Sa" "Mi");;			# Malayam (Bahasa Melayu)
	nb* )  DOW=("ma" "ti" "on" "to" "fr" "lø" "sø");;			# Norwegian (Norsk)
	pl* )  DOW=("Po" "Wt" "&#346;r" "Cz" "Pt" "So" "Nd");;			# Polish (Polska)
	pt* )  DOW=("Sq" "Te" "Qa" "Qi" "Se" "Sá" "Do");;			# Portuguese (Português)
	ro* )  DOW=("Lu" "Ma" "Mi" "Jo" "Vi" "Sa" "Du");;			# Romanian (Român)
	ru* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1042;&#1086;");;			# Russian (&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;)
	sr* )  DOW=("Po" "Ut" "Sr" "&#268;e" "Pe" "Su" "Ne");;			# Serbian (&#1057;&#1088;&#1087;&#1089;&#1082;&#1080;)
	sk* )  DOW=("Po" "Ut" "St" "Št" "Pi" "So" "Ne");;			# Slovak (Sloven&#269;ina)
	sl* )  DOW=("Po" "To" "Sr" "&#268;e" "Pe" "So" "Ne");;			# Slovenian (Slovenski)
	es* )  DOW=("Lu" "Ma" "Mi" "Ju" "Vi" "Sá" "Do");;			# Spanish (Español)
	sv* )  DOW=("Må" "Ti" "On" "To" "Fr" "Lö" "Sö");;			# Swedish (Svenska)
	tr* )  DOW=("Pa" "Sa" "Ça" "Pe" "Cu" "Cu" "Pa");;			# Turkish (Türkçe)
	uk* )  DOW=("&#1055;&#1086;" "&#1042;&#1110;" "&#1057;&#1077;" "&#1063;&#1077;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1053;&#1077;");;			# Ukrainian (&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;)
        * ) DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su") ;;
esac
```

Hope that helps.
Bruce

---

### Post by Bruce M. on 2010-02-10
> **mobilediesel said:**
> add [COLOR="Blue"]|sed 's/^/${center}/'[/COLOR] to the end like this:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'[COLOR="Blue"]|sed 's /^/${center}/'[/COLOR]}
```

HEY there buddy, you beat me to the punch, but missed one part of his two part quest.

He wanted the day marked differently AND centred.  No problem though, I did give him "# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al." so you're still in the game.

CHIMO!
Bruce

---

### Post by vickoxy on 2010-02-10
> **mobilediesel said:**
> add [COLOR="Blue"]|sed 's/^/${alignc}/'[/COLOR] to the end like this:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'[COLOR="Blue"]|sed 's /^/${alignc}/'[/COLOR]}
```

Unfortunately, this code gives me nothing-as something is missing.. i prefer such a simple solution...

---

### Post by vickoxy on 2010-02-10
> **Bruce M. said:**
> HEY there buddy, you beat me to the punch, but missed one part of his two part quest.

He wanted the day marked differently AND centred.  No problem though, I did give him "# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al." so you're still in the game.

CHIMO!
Bruce

No- i meant only that calender is centered in conky column-not the day-i just wan simple calender, only wit current day marked.

I made conkycal.sh script in my /home/ directory, made it executable. I made also one lang file in /home/-but got only few letters:

this is the line:
```
${font DejaVu Sans Mono:bold:size=9}${execpi 3600 $HOME/conkycal.sh -l es|sed 's/^/\${goto 105}/'}${font}
```

---

### Post by mobilediesel on 2010-02-10
> **Bruce M. said:**
> HEY there buddy, you beat me to the punch, but missed one part of his two part quest.

He wanted the day marked differently AND centred.  No problem though, I did give him "# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al." so you're still in the game.

CHIMO!
Bruce

This can also work:
```
#!/bin/bash
############################################################
# This work is licensed under the Creative Commons         #
# Attribution-Share Alike 3.0 Unported License.            #
# To view a copy of this license, visit                    #
# http://creativecommons.org/licenses/by-sa/3.0/           #
# or send a letter to Creative Commons, 171 Second Street, #
# Suite 300, San Francisco, California, 94105, USA.        #
############################################################

date=$(date '+%F')
DAY=${date:8:2}
# m="-m" # uncomment this line for starting the week on Monday instead of Sunday.
cal=$(cal $m)
prev=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color blue} $next"
else next="\${color blue}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
current=$(echo "${cal:42}"|sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' )
current=$(echo "$current"|sed -e /" ${DAY/#0/} "/s/" ${DAY/#0/} "/" "'${color white}'"${DAY/#0/}"'${color}'" "/ -e 's/^ //' -e 's/ *$//')
echo -e "\${color}${cal:0:21}${cal:21:21}\${color blue}$prev\${color}$current$next"
```
so you get the last days of last month and the first days of next month:
```
   February 2010    
Su Mo Tu We Th Fr Sa
[COLOR="Blue"]31[/COLOR]  1  2  3  4  5  6
 7  8  9 [COLOR="grey"]10[/COLOR] 11 12 13
14 15 16 17 18 19 20
21 22 23 24 25 26 27
28  [COLOR="Blue"]1  2  3  4  5  6[/COLOR]
```
The current day color is white but I made it grey in the code output above since the background is white.

If you want even MORE complicated, I can post the one where the holidays and birthdays are highlighted! :D

---

### Post by mobilediesel on 2010-02-10
> **vickoxy said:**
> Unfortunately, this code gives me nothing-as something is missing.. i prefer such a simple solution...

There was an extra space near the end, my fault!

Try this one:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
```

---

### Post by vickoxy on 2010-02-10
> **mobilediesel said:**
> There was an extra space near the end, my fault!

Try this one:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
```

Thanks-that almost did it-but the calender is centered and little bit messed up-is it possible to add right alingment and then to add some offset to make it nice looking?

---

### Post by vickoxy on 2010-02-10
Found solution-Bruce said to use Mono:popcorn:
Thanks mobilediesel for code :popcorn:- i just added offset instead of alignment:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${offset 35}/'} 
```

So, the output is just fine for me.

---

### Post by vickoxy on 2010-02-10
Ha-at 00:00 conky is dead-obviously, the line with calender does something to conky to crash down-i deleted the line
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${offset 35}/'}
```
and everything is normal again.
If i bring it back, conky crashes.

?!?:-k:-k:-k

---

### Post by mobilediesel on 2010-02-10
> **vickoxy said:**
> Ha-at 00:00 conky is dead-obviously, the line with calender does something to conky to crash down-i deleted the line
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${offset 35}/'}
```
and everything is normal again.
If i bring it back, conky crashes.

?!?:-k:-k:-k

If you're more interested in keeping fairly simple, try this:
```
${execpi 300 cal |sed -e "s/\<$(date +%-d)\>/\${color e84448}&\${color}/" -e 's/^/${offset 35}/'}
```

obviously don't forget the mono-spaced font before the code. :D

---

### Post by vickoxy on 2010-02-10
> **mobilediesel said:**
> If you're more interested in keeping fairly simple, try this:
```
${execpi 300 cal |sed -e "s/\<$(date +%-d)\>/\${color e84448}&\${color}/" -e 's/^/${offset 35}/'}
```

obviously don't forget the mono-spaced font before the code. :D

Unfortunately-these yours codes are killing my conky-if i add those lines, it can not start any more.

Compare to these one:
```
${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color #b7d1ea}'"$DJS"'${color}'" "/}
``` 

This is showing everything ok, but i can not achieve offset, and there is no month and year displayed as it is by your lines...

---

### Post by vickoxy on 2010-02-10
I found these simple line: ```
${execpi 60 DJS=`date +%_d`; cal | sed s/"$DJS"'\b'/'${color orange}'"$DJS"'$color'/}
```
it works, but i do not know how to put it in the center/offset?

---

### Post by vickoxy on 2010-02-10
Mobilediesel, this is your line whitout offset-it is working, but i do not know how to achieve that centering:
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^//'}
```

---

### Post by vickoxy on 2010-02-10
ok-i think i did it with this line:

```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
```

Thanks :popcorn:

---

### Post by mobilediesel on 2010-02-10
> **vickoxy said:**
> ok-i think i did it with this line:

```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
```

Thanks :popcorn:

Hopefully that works without killing conky again. I've found that sometimes just changing the conkyrc file can crash conky. It seems to be random though.

---

