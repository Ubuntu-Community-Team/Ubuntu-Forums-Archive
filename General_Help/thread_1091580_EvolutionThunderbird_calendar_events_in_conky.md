---
title: "Evolution/Thunderbird calendar events in conky"
date: 2009-03-09
forum: General Help
---

### Post by 987poiuytrewq on 2009-03-09
There are plugins for conky that let you display the events in your google calendar. But why use google calendar if you're already using the calendar on your desktop. With a little help from a program called calcurse, a CLI for ical calendars, it is possible to display your local calendar using conky on your desktop. This script shows your Evolution calendar in conky. Just insert

```
${execi 1 ~/path/to/script}
```

in conky to display it, where 1 is the update interval in seconds. At the moment, I don't know how to do any formatted text in conky using the output of this script, so any help would be welcomed. The following script shows the next 3 days only, as per the screenshot

```
#! /bin/bash
rm ~/.calcurse/apts
calcurse -i ~/.evolution/calendar/local/system/calendar.ics | sed 's/.*//'
today=$(date +%D | sed 's/\//\\\//g')
tomorrow=$(date -d tomorrow +%D| sed 's/\//\\\//g')
twodays=$(date -d "2 days" +%D| sed 's/\//\\\//g')
twodaysname=`date -d "2 days" +%A`
echo
echo
calcurse -r 3 | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}' | sed -e 's/'$today':/--Today------------/' -e 's/'$tomorrow':/\n--Tomorrow------/' -e 's/'$twodays':/\n--'$twodaysname'---/'
```

Obviously if you want to use thunderbird or any other ical file, just change the path to that file.

NB: you will need to download and compile the newest version of calcurse from [http://culot.org/calcurse/download.html](http://culot.org/calcurse/download.html)
and you will need libncurses5-dev and libncursesw-dev from the repos.

Enjoy!

---

### Post by hawkbane47 on 2009-03-27
i followed the instructions, and but i haven't been able to get this script to work. calcurse is installed (version 2.5) but it still does not display the events, and I have

${execi 100 ~/Desktop/1.sh}
and the path in the script is to my calendar....

---

### Post by clementeb on 2009-04-24
Hi, I tried the script as well but it seems it doesn't do anything. 
By the way, is there a way to add tasks as well? Or is there a similar script tthat works with sunbird or thunderbird?
Cheers

---

### Post by 987poiuytrewq on 2009-04-28
Hi my laptop is broken and I'm waiting until after my exams before I get a new one so I'll repost then, when I can play around with the script a bit. I also managed to get formatting to work eg days in a different color/bold etc.

But in the meantime, you could do some debugging. Firstly, are you sure you made the script executable? If you did, could you close down all instances of conky by opening up a terminal and entering 
```
killall conky
```
then enter
```
rm ~/.calcurse/apts
```
to clear the copy of your calendar that calcurse uses. Then run
```
calcurse -i ~/.evolution/calendar/local/system/calendar.ics
```
(replacing the directory with your own ical file) this should import the ical file. If you open up calcurse by typing
```
calcurse
```
you should be able to see whether the file imported correctly and if so there is not a problem with calcurse but with the script. If the data was imported, try exiting calcurse and typing
```
calcurse -r 5
```
in a terminal and you should get the next five days worth of appointments (if any). If you get some output, there is definitely a problem with the script, and I'll have a look at it when I get a new laptop.

@clementeb the tasks should be imported if they are in the same ical file, and you can display them by putting the following at the end of the script:
```
calcurse -t
``` or ```
calcurse -t 1
``` will print tasks of priority 1 (highest) will be printed.

---

### Post by clementeb on 2009-04-29
Thank you very much for your kind reply. It is all very clear now. Anyhow I am having troubles with ics files and calcurse, which does not accept complicated ics files. An example of my ics both on evolution and alone is: 
[QUOTE]BEGIN:VCALENDAR
CALSCALE:GREGORIAN
PRODID:-//Ximian//NONSGML Evolution Calendar//EN
VERSION:2.0
BEGIN:VEVENT
UID:XXXXXXXX
DTSTART;VALUE=DATE:20090702
DTEND;VALUE=DATE:20090702
SUMMARY:XXXXXX
X-LIC-ERROR;X-LIC-ERRORTYPE=VALUE-PARSE-ERROR:No value for DESCRIPTION 
 property. Removing entire property:
CATEGORIES:Default
DTSTAMP:20090424T183034Z
CREATED:20090424T183034
LAST-MODIFIED:20090424T183034
END:VEVENT

etc

while if I check a calcurse ics file (export function) I only see the date (dd/mm/yyyy) and the summary What should I do? 
Cheers  

P.s. I have put XXXX instead of personal information

---

### Post by clementeb on 2009-04-30
Hello,

Thank you again for your help and for  the script.
I have found out why I could not import the calendar: the default version of calcurse in ubuntu is 2.1 not 2.5
I managed to update and try the debugging.
In the terminal I do get all the proper information (the events for the next 5 days), but nothing on concky, so there must be some problem with the script.
I am looking forward to see the new version:)
All the best,

Clemente

---

### Post by clementeb on 2009-05-18
Hello,

after reinstalling the OS the script started working!!!
There is still a problem anyhow: there are 2 or 3 blank lines before the first calendar entry.
I have also added the tasks line to the script, but no tasks appear.
Hope the problem can be solved. 
All the best,

Clemente

---

### Post by 987poiuytrewq on 2009-05-28
Right, here is the new script, you need to use 
```
${exec**p**i 1 ~/path/to/script}
```
in conky this time, so it can parse the formatting properly

Firstly, if you're using Jaunty, calcurse 2.5 is in the repos, so no need to compile from source just
```
sudo apt-get install calcurse
```

For tasks, they appear to be stored in a seperate ical file, at least for evolution, so you need to find that .ics file and add the path to the script. The script at the moment is set up for evolution, and automatically displays tasks as well. Look at the very top for formatting settings, and at the very bottom to control the output to conky. Also, I added a horizontal line between days, but just remove ${hr} from line 51 if you don't want it. 

Finally, I added some extra processing since I ahve timezones in evolution that seem to mess up calsurse. If this doesn't work for you, try commenting out line 24 and uncommenting line 25.

```
#! /bin/bash

#settings
icalpath=~/.evolution/calendar/local/system/calendar.ics
taskpath=~/.evolution/tasks/local/system/tasks.ics
days=5
#leave blank to display all tasks
priority=

#formatting: leave blank to use default formatting
#otherwise fill in in standard conky formatting  in single quotes
# eg 'sans:size=8:style=bold' or a color in hex eg 'FFFFFF'
dayfont=
daycolor=
timefont=
timecolor=

#DON'T EDIT THIS IF YOU DON'T UNDERSTAND IT============================    |
#to change the order/style of output to conky, go to the end of the file  \|/
#                                                                          &#780; 

rm -f ~/.calcurse/apts

#need to do this to remove timezone information. try commenting out the line below if it messes things up and uncommenting the one below that i.e. the one that starts cp -f ...
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
#cp -f $icalpath ~/.calcurse/imported.ics

#import modified ics
calcurse -i ~/.calcurse/imported.ics > /dev/null

#find dates and day names in range
for i in `seq $days`
do
	day[$i]=$(date -d "$i days" +%D | sed 's/\//\\\//g')
	dayname[$i]=$(date -d "$i days" +%A)
done

#name Today and Tomorrow appropriately
dayname[1]="Today"
dayname[2]="Tomorrow"

#get list of appointments and remove extra info
apptlist=$(calcurse -r $days | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}')

#format the appointment times
apptlist=$(echo "$apptlist" | sed -e 's/[0-9][0-9]:[0-9][0-9]/${font'" ${timefont}"'}${color'" ${timecolor}"'}&\${font}\${color}/g')

#loop over days, replacing them with their correct names and formatting
for i in `seq $days`
do
	apptlist=$(echo "$apptlist" | sed -e 's/'${day[$i]}':/${font'" ${dayfont}"'}${color'" ${daycolor}"'}'${dayname[$i]}'${hr}${font}${color}/')
done



#okay, now lets do the tasks
rm -f ~/.calcurse/todo
#import the tasks ics
calcurse -i $taskpath > /dev/null

#get tasks from calcurse and strip off priority number eg 9. 
tasklist=$(calcurse -t $priority | sed -n '2,$ p' |sed 's/[0-9]\. //g')

#PRINT THIS TO CONKY==================================================
#=====================================================================
#add conky commands preceded by echo and enclosed in single quote

echo "$apptlist"
echo To do'${hr}'
echo "$tasklist"


```

---

### Post by clementeb on 2009-05-29
Great!!!!!
It looks so cool!
Anyhow I still have one little problem that has to do with the formatting of the days of the week. I get the code lines related to font and color ie I see the following:
${font}${color}Today${hr}${font}${color}
instead of just Today
similarly  To do comes out as
To do${hr}

Could it be because in my conky the default settings for the fonts are related to xft and colors are given in name not code?
These are my default settings
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=6
xftalpha 0.8
text_buffer_size 5000

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

own_window yes
own_window_transparent yes
#own_window_type override
own_window_type desktop
#own_window_type normal #use this if you want a nice shadow to appear around conky

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 350 0
#maximum_width 240

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color green
#default_shade_color black
#default_outline_color green
own_window_colour green


Sorry for all the trouble, but it is really a great script that I believe should become one of the standard features of conky!!!!

---

### Post by 987poiuytrewq on 2009-05-29
Are you sure you're calling ```
exec**p**i
``` from conky, not ```
execi
``` AND you restarted conky? Otherwise, it should be fine. Do you get the same for the times of appointment times i.e. do you see
```
${font}${color}10:00${font}${color}
```

I'm using xft fonts and you should be able to specify colors by either name or code, so that shouldn't be a problem. The only thing that's different is your translucent fonts, but I don't see why that should make any difference.

---

### Post by clementeb on 2009-05-30
You were right, it was the missing p that created the problem. Now everything works very well and it is really pleasant to see. 
There is just one little thing that I cannot understand. Instead of today, I get the date (bold) followed by a column  (:) and then  on the following line the event (bold).
All the other things are fine (day, not date, followed by a dividing line, then on the following line the events and so on, at the end To do followed by a dividing line)
What could it be?

---

### Post by 987poiuytrewq on 2009-06-01
I don't know why that should happen really. Could you run the script in a terminal and paste here what the output is. E.g type 
```
/path/to/script
```
so I can see what it returns?

---

### Post by clementeb on 2009-06-02
I get the date in number and on the following line the events, but then I also get ${font }${color }Today${hr}${font}${color} and tomorrows events ?! The same happens on conky (of course without font problems thanks to the excpi)
How odd

---

### Post by 987poiuytrewq on 2009-06-05
I'm sorry, I can't understand unless you paste the output of the script here so I can see exactly what it displays and preferably post a screenshot of conky as well

---

### Post by clementeb on 2009-06-05
Hello,

thank you again for your patience in trying to solve the problem.
If I run the script on the terminal I get:

06/05/09:
Today is the fifth of June
${font }${color }Today${hr}${font}${color}
Today is the sixth of June
${font }${color }Tomorrow${hr}${font}${color}
Today is the seventh of June
${font }${color }Monday${hr}${font}${color}
Today is the eighth of June
To do${hr}
get some help

Instead of Today I have the date, instead of Tomorrow I have Today, then I get the proper weekday name.
In conky I get the same as you can see from the picture:
[[IMG]http://img36.imageshack.us/img36/5474/concon.th.jpg[/IMG]]("http://img36.imageshack.us/my.php?image=concon.jpg")
[http://img36.imageshack.us/i/concon.jpg/](http://img36.imageshack.us/i/concon.jpg/)

In conky regarding the calendar I have only:
${font Arial Black:size=6}${execpi 1 ~/bin/calendar.sh}

I hope the problem can be solved.
All the best

---

### Post by 987poiuytrewq on 2009-06-08
Hi, thanks for posting a screenshot, that makes things much clearer. I know what the problem is, basically I have an array that starts from 1 instead of 0, so it misses out today and goes straight on to tomorrow, so all the day names are shifted by a day into the future. I just moved the start back to zero days away, which should correspond to today. If that makes any sense at all!

Anyway, just use this new script, and it should fix the formatting to be all the same. The script picks up your default formatting in conky unless you specify otherwise, so it will ignore any formatting line you put in front of it. Change the font bit before TEXT in your .conkyrc to
```
font Arial Black:size=6
```
to set your default font, and then the script should use that.

New script:
```
#! /bin/bash

#settings
icalpath=~/.evolution/calendar/local/system/calendar.ics
taskpath=~/.evolution/tasks/local/system/tasks.ics
days=5
#leave blank to display all tasks
priority=

#formatting: leave blank to use default formatting
#otherwise fill in in standard conky formatting  in single quotes
# eg 'sans:size=8:style=bold' or a color in hex eg 'FFFFFF'
dayfont='sans:size=7'
daycolor='B2C8E6'
timefont='sans:size=8:style=bold'
timecolor='FFFFFF'

#DON'T EDIT THIS IF YOU DON'T UNDERSTAND IT============================    |
#to change the order/style of output to conky, go to the end of the file  \|/
#                                                                          &#780; 

rm -f ~/.calcurse/apts
#need to do this to remove timezone information
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
#import modified ics
calcurse -i ~/.calcurse/imported.ics > /dev/null

#find dates and day names in range
for i in `seq $days`
do
	j=$(echo $i'-1' | bc)
	day[$i]=$(date -d "$j days" +%D | sed 's/\//\\\//g')
	dayname[$i]=$(date -d "$j days" +%A)
done

#name Today and Tomorrow appropriately
dayname[1]="Today"
dayname[2]="Tomorrow"

#get list of appointments and remove extra info
apptlist=$(calcurse -r $days | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}')

#format the appointment times
apptlist=$(echo "$apptlist" | sed -e 's/[0-9][0-9]:[0-9][0-9]/${font'" ${timefont}"'}${color'" ${timecolor}"'}&\${font}\${color}/g')

#loop over days, replacing them with their correct names and formatting
for i in `seq $days`
do
	apptlist=$(echo "$apptlist" | sed -e 's/'${day[$i]}':/${font'" ${dayfont}"'}${color'" ${daycolor}"'}'${dayname[$i]}' ${voffset -2}${hr}${voffset +2}${font}${color}/')
done



#okay, now lets do the tasks
rm -f ~/.calcurse/todo
#import the tasks ics
calcurse -i $taskpath > /dev/null

#get tasks from calcurse and strip off priority number eg 9. 
tasklist=$(calcurse -t $priority | sed -n '2,$ p' |sed 's/[0-9]\. //g')

#PRINT THIS TO CONKY==================================================
#=====================================================================
#add conky commands here if you wish, enclosed in single quotes

echo "$apptlist"


```

---

### Post by shadesofevil on 2009-06-14
from what I gather, your scripts imports the ical file everytime it's run to mirror changes to the ical file in calcurse's database. 

The problem I'm having is that whenever I import, it creates new entries for already existing events. Is anybody else having the same problem?

---

### Post by shadesofevil on 2009-06-14
Never mind: I didn't see the "rm ~/.calcurses/apts" part before.

---

### Post by 987poiuytrewq on 2009-06-15
Yeah, it deletes and re-imports every time it refreshes. I agree it's not the most efficient way to update a calendar, but the parsing of the ical file seems to be very fast, and I couldn't think of a better way to do it :p.

---

### Post by clementeb on 2009-06-19
Sorry for this very late reply, but my system crashed and I didn't have time to fix the entire thing.
The code now works perfectly!!!
Thank you very much for everything.
All the best

---

### Post by exutable on 2009-09-28
So how do we get this to work with thunderbird, considering that the default paths are all to evolution.  It seems thunderbird stores it's calendar in a different format than evolution

---

### Post by 987poiuytrewq on 2009-10-03
Hi, yeah, thunderbird/lightning/sunbird now uses a sdb file instead of an ics file. However, if you download the extension "Automatic Export" [http://www.sunbird-kalender.de/extension/autoexport/en/download.html](http://www.sunbird-kalender.de/extension/autoexport/en/download.html) then it will export to a file called Home.ics every time you exit thunderbird. Then set the path to wherever you saved this file and everything should come together nicely.

---

### Post by clementeb on 2009-10-05
Hi,

it's me again.
I have just reinstalled the entire system (I am now using calcurse 2.7 on ubuntu 9.04 based os) thinking everything would be fine, but I don't get the appointments anymore. Rather I get all the variables as you wrote them on the script.
Here is a picture of what I see
[[IMG]http://img210.imageshack.us/img210/3861/screenshotcx.th.png[/IMG]](http://img210.imageshack.us/i/screenshotcx.png/)
[http://yfrog.com/5uscreenshotcxp](http://yfrog.com/5uscreenshotcxp)
What could it be?
Cheers

---

### Post by 987poiuytrewq on 2009-10-08
> [QUOTE]Rather I get all the variables as you wrote them on the script.[/QUOTE]
That's not in fact true at all. If you run ```
calcurse -h
``` in a terminal you'll see that this is calcurse encountering an error and printing out its help to assist you, which then gets piped into conky which is why it is there. In short, its failing to read your ics file correctly. I'm not sure why but go through the debugging steps I outlined a few posts back and see if that comes up with anything.

---

### Post by clementeb on 2009-10-14
Hi, it's again me.
I tried debugging, but when I do calcurse -r 5, I get:

Usage: calcurse [-h|-v] [-N] [-an] [-t[num]] [-i<file>] [-x[format]]
                [-d <date>|<num>] [-s[date]] [-r[range]]
                [-c<file> | -D<dir>] [-S<regex>] [--status]
Try 'calcurse -h' for more information.

The funny thing is that if I run calcurse from the terminal I get all the events in the calendar.
Another funny thing happening is that calcurse is often locked, so even if  Ikill the program  the calcurse.pid remains, so I have to delete the file.
I am not sure why.
Cheers

---

### Post by rocketpants on 2009-12-11
> **clementeb said:**
> Hi,

it's me again.
I have just reinstalled the entire system (I am now using calcurse 2.7 on ubuntu 9.04 based os) thinking everything would be fine, but I don't get the appointments anymore. Rather I get all the variables as you wrote them on the script.

What could it be?
Cheers

The problem is that calcurse v2.7 seems to have changed the way it parses it's input parameters. Instead of "calcurse -r n", it now expects "calcurse -rn" (no space between "r" and "n").

Remove the space between "-r" and "$days" on line 41 of the script, and you'll be back up and running again.

---

### Post by 987poiuytrewq on 2009-12-18
That's spot on rocketpants, I just stumbled across this. I don't really use this script much anymore, although I will continue to maintain it. You need to also remove the space between -t and $priority. Give this a whirl, and see what happens:
```
#! /bin/bash

#settings
icalpath=~/.evolution/calendar/local/system/calendar.ics
taskpath=~/.evolution/tasks/local/system/tasks.ics
days=5
#leave blank to display all tasks
priority=

#formatting: leave blank to use default formatting
#otherwise fill in in standard conky formatting  in single quotes
# eg 'sans:size=8:style=bold' or a color in hex eg 'FFFFFF'
dayfont='sans:size=7'
daycolor='B2C8E6'
timefont='sans:size=8:style=bold'
timecolor='FFFFFF'

#DON'T EDIT THIS IF YOU DON'T UNDERSTAND IT============================    |
#to change the order/style of output to conky, go to the end of the file  \|/
#                                                                          &#780; 

rm -f ~/.calcurse/apts
#need to do this to remove timezone information
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
#import modified ics
calcurse -i ~/.calcurse/imported.ics > /dev/null

#find dates and day names in range
for i in `seq $days`
do
	j=$(echo $i'-1' | bc)
	day[$i]=$(date -d "$j days" +%D | sed 's/\//\\\//g')
	dayname[$i]=$(date -d "$j days" +%A)
done

#name Today and Tomorrow appropriately
dayname[1]="Today"
dayname[2]="Tomorrow"

#get list of appointments and remove extra info
apptlist=$(calcurse -r$days | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}')

#format the appointment times
apptlist=$(echo "$apptlist" | sed -e 's/[0-9][0-9]:[0-9][0-9]/${font'" ${timefont}"'}${color'" ${timecolor}"'}&\${font}\${color}/g')

#loop over days, replacing them with their correct names and formatting
for i in `seq $days`
do
	apptlist=$(echo "$apptlist" | sed -e 's/'${day[$i]}':/${font'" ${dayfont}"'}${color'" ${daycolor}"'}'${dayname[$i]}' ${voffset -2}${hr}${voffset +2}${font}${color}/')
done



#okay, now lets do the tasks
rm -f ~/.calcurse/todo
#import the tasks ics
calcurse -i $taskpath > /dev/null

#get tasks from calcurse and strip off priority number eg 9. 
tasklist=$(calcurse -t$priority | sed -n '2,$ p' |sed 's/[0-9]\. //g')

#PRINT THIS TO CONKY==================================================
#=====================================================================
#add conky commands here if you wish, enclosed in single quotes

echo "$apptlist"
```

---

### Post by joep-vd on 2010-01-31
Hey! I am having problems to get conky to display my sunbird events and tasks. I have no experience with making scripts, so there is a lot to check. 

I have worked with the recommendations mentioned in this thread. I made an executable file named conf with the following contents: 

```

#! /bin/bash

#settings
icalpath=~/.mozilla/sunbird/export/Home.ics
taskpath=~/.mozilla/sunbird/export/Home.ics
days=5
#leave blank to display all tasks
priority=

#formatting: leave blank to use default formatting
#otherwise fill in in standard conky formatting  in single quotes
# eg 'sans:size=8:style=bold' or a color in hex eg 'FFFFFF'
dayfont='sans:size=7'
daycolor='B2C8E6'
timefont='sans:size=8:style=bold'
timecolor='FFFFFF'

#DON'T EDIT THIS IF YOU DON'T UNDERSTAND IT============================    |
#to change the order/style of output to conky, go to the end of the file  \|/
#                                                                          &#780; 

rm -f ~/.calcurse/apts
#need to do this to remove timezone information
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
#import modified ics
calcurse -i ~/.calcurse/imported.ics > /dev/null

#find dates and day names in range
for i in `seq $days`
do
	j=$(echo $i'-1' | bc)
	day[$i]=$(date -d "$j days" +%D | sed 's/\//\\\//g')
	dayname[$i]=$(date -d "$j days" +%A)
done

#name Today and Tomorrow appropriately
dayname[1]="Today"
dayname[2]="Tomorrow"

#get list of appointments and remove extra info
apptlist=$(calcurse -r$days | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}')

#format the appointment times
apptlist=$(echo "$apptlist" | sed -e 's/[0-9][0-9]:[0-9][0-9]/${font'" ${timefont}"'}${color'" ${timecolor}"'}&\${font}\${color}/g')

#loop over days, replacing them with their correct names and formatting
for i in `seq $days`
do
	apptlist=$(echo "$apptlist" | sed -e 's/'${day[$i]}':/${font'" ${dayfont}"'}${color'" ${daycolor}"'}'${dayname[$i]}' ${voffset -2}${hr}${voffset +2}${font}${color}/')
done



#okay, now lets do the tasks
rm -f ~/.calcurse/todo
#import the tasks ics
calcurse -i $taskpath > /dev/null

#get tasks from calcurse and strip off priority number eg 9. 
tasklist=$(calcurse -t$priority | sed -n '2,$ p' |sed 's/[0-9]\. //g')

#PRINT THIS TO CONKY==================================================
#=====================================================================
#add conky commands here if you wish, enclosed in single quotes

echo "$apptlist"

```

...and the following line in conky: 

```

${execpi -1 ~/.calcurse/conf}

```

any help would be appreciated. Thanks!

---

### Post by snoxu on 2010-02-25
I also can't get this display my Sunbird calendar

Here are the errors when I run the script in the terminal:
```
./calscript: line 24: /home/hugo/.calcurse/imported.ics: No such file or directory
FATAL ERROR: could not create /home/hugo/.calcurse/apts: No such file or directory
./calscript: line 31: bc: command not found
./calscript: line 31: bc: command not found
./calscript: line 31: bc: command not found
./calscript: line 31: bc: command not found
./calscript: line 31: bc: command not found
FATAL ERROR: could not create /home/hugo/.calcurse/apts: No such file or directory

```

---

### Post by akernan on 2011-07-24
Is this thread still active?

---

### Post by arclance on 2012-01-13
I found that the location were the calender and tasks file is stored by evolution had changed in Ubuntu 11.04.
The calendar file is found at
```
~/.local/share/evolution/calendar/system/calendar.ics
```and the tasks file is found at
```
~/.local/share/evolution/tasks/system/tasks.ics
```The script mostly works if you make those changes like this.
```

#! /bin/bash

#settings
icalpath=~/.local/share/evolution/calendar/system/calendar.ics
taskpath=~/.local/share/evolution/tasks/system/tasks.ics
days=5
#leave blank to display all tasks
priority=

#formatting: leave blank to use default formatting
#otherwise fill in in standard conky formatting  in single quotes
# eg 'sans:size=8:style=bold' or a color in hex eg 'FFFFFF'
dayfont=''
daycolor='CC9900'
timefont=''
timecolor='EE7600'

#DON'T EDIT THIS IF YOU DON'T UNDERSTAND IT============================    |
#to change the order/style of output to conky, go to the end of the file  \|/
#                                                                          &#780; 

rm -f ~/.calcurse/apts
#need to do this to remove timezone information
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
#import modified ics
calcurse -i ~/.calcurse/imported.ics > /dev/null

#find dates and day names in range
for i in `seq $days`
do
    j=$(echo $i'-1' | bc)
    day[$i]=$(date -d "$j days" +%D | sed 's/\//\\\//g')
    dayname[$i]=$(date -d "$j days" +%A)
done

#name Today and Tomorrow appropriately
dayname[1]="Today"
dayname[2]="Tomorrow"

#get list of appointments and remove extra info
apptlist=$(calcurse -r$days | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}')

#format the appointment times
apptlist=$(echo "$apptlist" | sed -e 's/[0-9][0-9]:[0-9][0-9]/${font'" ${timefont}"'}${color'" ${timecolor}"'}&\${font}\${color}/g')

#loop over days, replacing them with their correct names and formatting
for i in `seq $days`
do
    apptlist=$(echo "$apptlist" | sed -e 's/'${day[$i]}':/${font'" ${dayfont}"'}${color'" ${daycolor}"'}'${dayname[$i]}' ${voffset -2}${hr}${voffset +2}${font}${color}/')
done



#okay, now lets do the tasks
rm -f ~/.calcurse/todo
#import the tasks ics
calcurse -i $taskpath > /dev/null

#get tasks from calcurse and strip off priority number eg 9. 
tasklist=$(calcurse -t$priority | sed -n '2,$ p' |sed 's/[0-9]\. //g')

#PRINT THIS TO CONKY==================================================
#=====================================================================
#add conky commands here if you wish, enclosed in single quotes

echo "$apptlist"

```This line
```
sed -e '/^ / !{h};/^ / {H;x;s/;.*:\r\n /:/g}' -e '/:\r$/ d' < $icalpath > ~/.calcurse/imported.ics
```can duplicate some lines in the calendar.ics file in addition to its intended function.
I don't know if this will cause any problems because it only mangled some of my appointments from ~3 years ago.

The script also no longer gets the date or day-names just returning a ":" separating the events by the day they occur on because these values are blank (should be date:day-name).

Each days events are displayed correctly however.

I don't know enough about bash or regular expressions to fix the script myself.

I rewrote the calendar part in python based on what I learned about calcurse from this script.
I am still working on some things I added to it right now.
If there is interest in it I can clean up what I wrote and start a new thread for it.

---

### Post by DarkWerra on 2012-04-03
Sorry for my bad English. What needs to be changed in the script, so the events will be displayed in a row? My knowledge are not so good. Thank you.

---

### Post by ZlyChleba on 2012-05-09
@arclance

I also found this issue of no day names. It would be great if you could figure this out. :)

---

### Post by arclance on 2012-05-09
> **ZlyChleba said:**
> @arclance

I also found this issue of no day names. It would be great if you could figure this out. :)
I got it mostly working a while ago.  [You can find the scripts here.]("http://crunchbanglinux.org/forums/post/217257/#p217257")
I ended up completely rewriting the script in Python to get it to work the way I wanted.
It does not work correctly with recurring appointments yet.
That is more complicated and I have not had time to work on it yet.
[IMG]http://www.deviantart.com/download/1226005047828424/conky_icalendar_display_scripts_by_arclance-d4z8xtu.png[/IMG]

---

### Post by arclance on 2012-05-11
[I released a new version of my script here.]("http://crunchbanglinux.org/forums/topic/19512/display-icalendar-file-events-in-conky-v251/")
It now supports DAILY, WEEKLY, and YEARLY recurring appointment types.
Recurring appointments were not possible to handle with calcurse so I switched to using the [icalendar python module]("https://github.com/collective/icalendar") instead.
[IMG]http://www.deviantart.com/download/1226005047828424/conky_icalendar_display_scripts_by_arclance-d4z8xtu.png[/IMG]

---

