---
title: "Upper taskbar applet icons change order randomly (GNOME)"
date: 2008-06-25
forum: Desktop Environments
---

### Post by drewster1829 on 2008-06-25
This was also a problem I had in 7.04 and 7.10, but hasn't really happened in 8.04 until a week ago or so.  Every time I reboot, two (or more) of the taskbar icons in the upper right corner (the weather applet, volume control, networking status, date and time, and shutdown button) seem to randomly switch the order they are in.  Why is this?  Some of them I can't even move (Pidgin puts an icon up there, and I can't move it, or the network status icon) even after I turn "lock to panel" off (they were on on all of the applets which had it as an option, but didn't prevent them from randomly switching order).

Like I said, this hasn't happened for a month or two, but now it's doing it on every reboot.  Any ideas?:confused:

---

### Post by mcduck on 2008-06-26
They are not individual icons, but instead icons that running programs show inside the Notification Area-applet. Because of this you can't move them around individually (you can only move the Notifiation Area itself). The icons will appear in the order the programs load.

(The notification Area is pretty much the equivalent of the systray in Windows, although Gnome Human Interface guidelines say that only actual notifications should use it instead of just about any random program like in Windows.)

---

### Post by drjonze on 2008-06-26
> **mcduck said:**
> They are not individual icons, but instead icons that running programs show inside the Notification Area-applet. Because of this you can't move them around individually (you can only move the Notifiation Area itself). The icons will appear in the order the programs load.

(The notification Area is pretty much the equivalent of the systray in Windows, although Gnome Human Interface guidelines say that only actual notifications should use it instead of just about any random program like in Windows.)

I have the same issue, and its not the icons in the notification area. Its my System Monitor, Power, Volume control, User Switcher, Weather etc. These do not display in the notification area, they are launchers for other applications. 

It just started happening to me. I reset them back in the order I liked a few times but it now seems to have stopped.

---

### Post by drewster1829 on 2008-06-26
> **drjonze said:**
> I have the same issue, and its not the icons in the notification area. Its my System Monitor, Power, Volume control, User Switcher, Weather etc. These do not display in the notification area, they are launchers for other applications. 

It just started happening to me. I reset them back in the order I liked a few times but it now seems to have stopped.

Yeah, they randomly move around for a few reboots, then eventually quit.  It seems quite random.  Thanks for clearing that up!  It's not *in* the notification area, it's the icons for the applets themselves (in the taskbar, including the notification area).

---

### Post by alexbishops on 2009-02-19
I have the same sort of problem. Whenever I change the resolution of my screen the icons move around. I'm using an asus eee PC with an external monitor. The icons need to remember where they are for each resolution setting.

---

### Post by mcduck on 2009-02-19
You could try first moving everything into correct places when using the highest resolution you are going to use, and then locking the panel configuration with gconf-editor.

To lock panel settings, press Alt-F2 and run "gconf--editor", then use that to browse to panel/global and enable "locked_down"-key.

(I can't guarantee that this helps, Gnome's panels seem to have a bit of problems with changing resolutions, but it's definitely worth a try)

---

### Post by MeanEYE on 2009-07-29
Hello fellow ubuntu users :)...

I had similar issue :) so I decided to help out a bit...

I've create a small python script which will allow you to save and restore applet positions. You can also save the positions, manually edit configuration file and then restore as needed. 

In my experience, once I edited positions manually problem with randomly arranging applets is significantly reduced if not solved. Please note that I have aligned applets all to the right of the panel. I think problem with with random positions was in fact that not all applets were aligned equally... 

```
/apps/panel/applets/applet_4=100/1/0 					# top_panel_screen0:bonobo-applet (OAFIID:GNOME_KeyboardApplet)
/apps/panel/objects/object_2=90/1/0 					# top_panel_screen0:separator ()
/apps/panel/applets/applet_2=80/1/0 					# top_panel_screen0:bonobo-applet (OAFIID:GNOME_CPUFreqApplet)
/apps/panel/applets/applet_1=70/1/0 					# top_panel_screen0:bonobo-applet (OAFIID:GNOME_CPUFreqApplet)
/apps/panel/objects/object_0=60/1/0 					# top_panel_screen0:separator ()
/apps/panel/applets/applet_0=50/1/0 					# top_panel_screen0:bonobo-applet (OAFIID:GNOME_MultiLoadApplet)
/apps/panel/applets/notification_area_screen0=40/1/0 	# top_panel_screen0:bonobo-applet (OAFIID:GNOME_NotificationAreaApplet)
/apps/panel/objects/object_1=30/1/0 					# top_panel_screen0:separator ()
/apps/panel/applets/mixer_screen0=20/1/0 				# top_panel_screen0:bonobo-applet (OAFIID:GNOME_MixerApplet)
/apps/panel/applets/clock_screen0=10/1/0 				# top_panel_screen0:bonobo-applet (OAFIID:GNOME_ClockApplet)
/apps/panel/applets/window_list_screen0=23/0/1 			# bottom_panel_screen0:bonobo-applet (OAFIID:GNOME_WindowListApplet)
/apps/panel/applets/workspace_switcher_screen0=10/1/1 	# bottom_panel_screen0:bonobo-applet (OAFIID:GNOME_WorkspaceSwitcherApplet)

```

This is how my config looks. The format is following:
```
path=xpos/right_align/locked
```

I would advise you not to edit paths nor to use my config since every system is different. Program also saves additional info so you can easily configure by hand. Well I hope you find this little script useful as I do... Cheers!

Oh, it can be downloaded [here]("http://rcf-group.com/index.php?section=downloads&action=view&id=22") :)

---

### Post by whiteside on 2010-02-03
this bash script will save your gnome panel icons positions if you don't have python (spits them out to standard out).

```

#!/bin/bash

#get list of icon object folders
objectsList=`ls -d ~/.gconf/apps/panel/objects/*/ | sed s/.*objects\\\/// | sed s/\\\///`

#get objects, like object_16
numObjects=0
for object in $objectsList;
do
	let numObjects=$numObjects+1;
done;

#get object names, like object_16
i=0
for object in $objectsList;
do
	objectNameList[$i]=$object
	#echo $object;
	let i=$i+1;
done;

#get stringvalues from icon object folders, like pidgin-1.desktop
i=0
for object in $objectsList;
do
	stringvalueList[$i]=`cat ~/.gconf/apps/panel/objects/$object/\%gconf.xml | grep --after-context 1 launcher_location | grep stringvalue | sed s/\<stringvalue\>// | sed s/\<\\\/stringvalue\>//`
	#echo ${stringvalueList[$i]};
	let i=$i+1;
done;

#get icon positions in pixels
i=0
for object in $objectsList;
do
	positionList[$i]=`cat ~/.gconf/apps/panel/objects/$object/\%gconf.xml | grep position | sed s/.*value=\"// | sed s/\"\\\/\>//`
	#echo ${positionList[$i]};
	let i=$i+1;
done;

#get icon launcher names launcherName names, like Pidgin Internet Messenger
i=0
for object in $objectsList;
do
	myTmp=`echo ${stringvalueList[$i]} | sed s/^\ //`
	myFirstChar=`echo $myTmp | cut -c 1`

	if [ -z $myFirstChar ]; then
		launcherNameList[$i]="NO-LAUNCHER-FILE";
	else
		if [ $myFirstChar = "/" ]; then
			myPath=$myTmp;
		else
			myPath="$HOME/.gnome2/panel2.d/default/launchers/"$myTmp;
		fi

		launcherNameList[$i]=`cat $myPath | grep Name= | sed s/Name=//`;
	fi

	#echo ${launcherNameList[$i]};
	let i=$i+1;
done;

#cat array
i=0
for object in $objectsList;
do
	echo ${objectNameList[$i]}, ${stringvalueList[$i]}, ${launcherNameList[$i]}, ${positionList[$i]}
	let i=$i+1;
done;


```

i'm too lazy to figure out how to restore the positions from the saved file though.

---

### Post by whiteside on 2010-02-03
if you want to write a script to restore them back, here's the explanation of my approach...

idea
-----------------------------
1. manually move panel icons to desired positions
2. log out
3. log in
4. run save-positions script to save icon positions to a txt file
5. icons move after resolutions changes
6. run restore-positions script using txt file of positions as input

task 1 - save-positions script
-----------------------------
1. get list, objList, of objects in /home/white/.gconf/apps/panel/objects by name e.g. object_16, object_5
2. go into each %gconf.xml file in /home/white/.gconf/apps/panel/objects/object_XX/
3. grab each <stringvalue> and position, as in pidgin-1.desktop from,
<gconf>
	<entry name="position" mtime="1265156014" schema="/schemas/apps/panel/objects/position" type="int" value="721"/>
	<entry name="launcher_location" mtime="1255549391" schema="/schemas/apps/panel/objects/launcher_location" type="string">
		<stringvalue>pidgin-1.desktop</stringvalue>
	</entry>
</gconf>
4. match each stringvalue to an entry in objList
5. open each file, stringvalueFile, of name stringvalue in goto /home/white/.gnome2/panel2.d/default/launchers/
6. grab all names, Name, from stringvalueFile, e.g. "Pidgin Internet Messenger" in "Name=Pidgin Internet Messenger"
7. save array objList in a myPositions.txt file, saving fields object_XX, stringvalue, position, Name
	e.g.
		object_16, pidgin-1.desktop, 721, Pidgin Internet Messenger
		object_14, eclipse-1.desktop, 280, Eclipse
		object_7, home-1.desktop, 500, Home folder


task 2 - restore-positions script SHORT WAY
-----------------------------
1. read myPositions.txt
2. for each row do the following
3. change position's value in /home/white/.gconf/apps/panel/objects/object_XX/ to position in myPositions.txt, in
<gconf>
	<entry name="position" mtime="1265156014" schema="/schemas/apps/panel/objects/position" type="int" value="721"/>
</gconf>


task 2 - restore-positions script BETTER WAY
-----------------------------
1. read myPositions.txt
2. for each row do the following
3. search for Name in Name field of all files in /home/white/.gnome2/panel2.d/default/launchers/
4. grab filename
5. search for filename in /home/white/.gconf/apps/panel/objects/object_*/%gconf.xml
6. change position's value in /home/white/.gconf/apps/panel/objects/object_XX/%gconf.xml to position in myPositions.txt, in
<gconf>
	<entry name="position" mtime="1265156014" schema="/schemas/apps/panel/objects/position" type="int" value="721"/>
</gconf>


note: if you change the Name of an icon, you'll have to rerun the save script

---

### Post by AlexanderDGreat on 2010-02-07
I hate to kill the party, but seriously for icons, I need to go through all these? Is there an easier way? I'm lost.

---

### Post by a_rojilla on 2010-02-19
Hi all,

Still no solution for this? I'm having the same problem with Karmic (9.10): icons randomly reordered whenever I change resolution. I've found like a dozen of threads about this BUG but the only solution seems to be one of those scripts that some of you propose here, what I really find... cumbersome? I appreciate the help, though.

Well, any new idea will be welcome.

Regards.

---

### Post by amillionsheep on 2010-02-22
I'm using UNR 9.10 with netbook-launcher disabled and am having this same issue. Every time I login my panel applets are in a different order than I put them in.

SOLUTION: Whoever is in charge of developing the Gnome Panel, DO YOUR JOB. Why would we want our applets in a different position each login? *sigh*

---

### Post by SuperElectric on 2010-04-05
Seems that the GNOME developers are working on the problem:

[https://bugs.launchpad.net/gnome-panel/+bug/44082](https://bugs.launchpad.net/gnome-panel/+bug/44082)

---

### Post by SuperElectric on 2010-04-05
Ooops; they've been "working on it" for four years now :/

[https://bugzilla.gnome.org/show_bug.cgi?id=341441](https://bugzilla.gnome.org/show_bug.cgi?id=341441)

---

### Post by sickiwicki on 2010-04-06
Hi all,

I'm a big fan of non-expanded panels so each time I installed Ubuntu for my home PCs I set the panel not to expand. As a result after next boot I got mixed applet positions. Then I moved the applets to the order I want, left each applet position unlocked. Since then they've stayed put. Now I've done this for 9.04, 9.10 and 10.04.

---

### Post by Karim_ on 2010-04-26
I feel much better that I'm not the only one with this problem. Hah ha. It's not a big problem just a few icons rearranged.

---

### Post by jonny163 on 2010-04-27
I found that if you unlock them and move them to where you want and then relock them, they will stay put :D

---

### Post by diogodpc on 2010-06-20
To me, the best solution is the one in the bug description:

[FONT="Courier New"]Temporary solution:
Backup the state of your panel:
gconftool-2 --dump /apps/panel > panel_backup.xml

and then restore it whenever it gets messed up:
gconftool-2 --load panel_backup.xml
killall gnome-panel (kills and auto-respawns, possibly need to run gnome-panel & as well)[/FONT]

Works like a charm!

Cheers

---

### Post by AlexanderDGreat on 2010-06-27
@diogodpc - hey, this actually works.

I'm using a dual monitor, and sometimes a projector. Whenever something wrong happens I just do what you told.

Great thank you!

---

