---
title: "copy paste tooltip"
date: 2022-08-10
forum: Desktop Environments
---

### Post by Claus7 on 2022-08-10
Hello,

I was wondering if there is any possibility that the tooltip shown when hovering the mouse on an item, could be copied somehow, so as to be pasted elsewhere.

For example under Places of flashback there are Recent Documents. There, if you hover on any of them, you will see a popup that shows the path of this certain item. I would like to be able to copy that path. Alternatively would be a nice idea if by right clicking it could open directly the location that file is located, yet just copying the path of the item would suffice.

I suppose that is not feasible, yet any ideas are more than welcome.

Regards!

---

### Post by TheFu on 2022-08-11
I don't know of any way. It is frustrating.

In theory, there is a localization file for the program which contains all the UI strings displayed.  Sometimes those files remain separate and sometimes they are compiled into the binary.

From a terminal, you could try using the 'strings' command with a 'grep' to look for unique parts of the tip, and hopefully, the entire line will be shown in the results.

For example, there's a menu item in Firefox with "History".
```
$ strings /usr/lib/firefox/*/* |egrep History
```
That finds a few results which can be used to look into more detail.  Because firefox uses javascript, many of the results are related to history functions.  The lesson here is to choose a unique string that only exists in a tooltip.  Here's a tooltip search:
```
$ strings /usr/lib/firefox/*/* |egrep "Reload Current Page" 
```
That didn't find anything.  See how stuff can be hidden/compressed but many applications won't do that.

---

### Post by Claus7 on 2022-08-11
Hello,

I tried with some files using the applications-overview-tooltip@RaphaelRochet extension for gnome shell, just in case. I couldn't find anything as well.
The easy part is that in every recent file under flashback, the word "Open" is in every tooltip. What is not obvious is where these tooltips are stored so as to get retrieved. Thank you for your direction.

edit: I tried to "capture" all open windows of the screen using the 
```
sleep 5 && wmctrl -l
```
command to no avail. The tooltip and the Applications, Places are part of the Top Expanded Edge Panel and makes no difference if invoked or not.

edit2: I tried also the command:
```
sleep 5 && import -window "$(wmctrl -l | grep -i Expanded)" ~/Desktop/result.jpg
```
it shows when Places is selected, yet it does not show anything under Places.

Regards!

---

### Post by Claus7 on 2022-08-15
Hello,

I created the following script in order to open a location of a recently opened file, bypassing the tooltip recording:
```
#with this script we want to open the directories of the most recently opened files

#add the command launcher to panel in order to open a terminal, while script is executed:
#gnome-terminal -- bash -c "~/Documents/how_to_s/open_path.sh && exit; exec bash"

#change to home directory
cd ~
#use the file where the information of the recent documents is stored to isolate path
awk '/home/{s=x}{s=s$0"\n"}/added/{print $2}' ~/.local/share/recently-used.xbel > test1.txt
#get rid of some redundant information
awk '{gsub("href=\"file:///", "");print}' test1.txt > test2.txt
#keep the path without filename
awk -F/ '{NF=NF-1;$NF=$NF"/"}1' OFS=/ test2.txt > test3a.txt
#keep filename from path
awk -F/ 'gsub("\"", ""){print $NF}' OFS=/ test2.txt > test3b.txt
#merge path and filename in one file with space inbetween
paste test3a.txt test3b.txt > test3.txt
#isolate last 10 directories with increment number in front
awk -v n=10 '{line[NR]=$0} END {for (i=NR-(n-1); i<=NR; i++) print i+n-NR, line[i]}' test3.txt > test4.txt
#get rid of home/username from path because nautilus has this by default
awk '{gsub("home/<username>/","");print}' test4.txt > test5.txt
#display paths opening new terminal
cat test5.txt
#choose path by entering line number (starts from 0, if while read above is used)
read -p 'Enter the folder number :'  ln
#display number
echo $ln
#open folder
nautilus $(awk -v ln="$ln" 'FNR==ln {print $2}' test5.txt)
#remove previously created files
rm test1.txt test2.txt test3a.txt test3b.txt test3.txt test4.txt test5.txt
```

Just change username, with your own in order to work.

Regards!

---

