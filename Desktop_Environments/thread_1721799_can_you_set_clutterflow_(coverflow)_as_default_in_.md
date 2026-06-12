---
title: "can you set clutterflow (coverflow) as default in Nautilus elementary?"
date: 2011-04-05
forum: Desktop Environments
---

### Post by N00b-un-2 on 2011-04-05
just wondering if it's possible.  All new Nautilus windows open without the coverflow view.  All you have to do is press f4 and it is activated, but I'd like to be able to activate it by default.  Looked in the gconf-editor and didn't find anything.  maybe in some kind of rc in the home folder? Any ideas?

---

### Post by Frogs Hair on 2011-04-05
I have been using Elementary Nautilus for a long time and I don't know a way with current settings options to make Clutterflow default.

It may be possible , but it would require a good working knowledge of the application and the ability to change how it works.

---

### Post by geazzy on 2011-05-02
> **N00b-un-2 said:**
> just wondering if it's possible.  All new Nautilus windows open without the coverflow view.  All you have to do is press f4 and it is activated, but I'd like to be able to activate it by default.  Looked in the gconf-editor and didn't find anything.  maybe in some kind of rc in the home folder? Any ideas?

I have problem same with this....
anybody can help?? :D

thanks

---

### Post by lilifiz on 2011-05-08
same issue here... and after doing some search, i found that it can't be done yet :-( .. hope someone will make it coz it's such an awesome feature to be considered as a default even in upcoming ubuntu releases in my opinion.

---

### Post by thongstele on 2011-05-18
> **lilifiz said:**
> same issue here... and after doing some search, i found that it can't be done yet :-( .. hope someone will make it coz it's such an awesome feature to be considered as a default even in upcoming ubuntu releases in my opinion.

Wish this ability can come true early...Coverflow is beautiful and more if it is default with Nautilus.

Cannot wait...

---

### Post by fatriff on 2011-05-18
C'mon now people, I just dropped everything I was doing just for this very issue.

I want it to default to clutterflow!!

Somebody please help us for the love of linux.

---

### Post by fatriff on 2011-05-18
**[COLOR="Red"][SIZE="3"]Semi Solution In My Next Post! Just needs tinkering to get clutter window to resize to user setting.[/SIZE][/COLOR]**

---

### Post by fatriff on 2011-05-18
Ok guys, The only way I am capable of thinking of how to do it. Took me all of 5 minutes once I figured out a way I could do it.

This works for all folders or single launchers.. Follow instructions below and then if you want there's an extra bit at the bottom of the post to just create single launchers (The set clutterview window size so it's always that size is being worked on and I will add it shortly)..

**Step 1**

Goto the repository and search for xdotool and install.

**Step 2**

Goto /home/yourname/.gnome2/nautilus-scripts

Right click in the folder and select create document>empty file.

In this file put the following..

[B]#!/bin/sh
filesall=""
while [ $# -gt 0 ]
do
files=`echo "$1" | sed 's/ /\?/g'`
filesall="$files $filesall"
shift
done
nautilus $filesall
sleep 1
xdotool key F4[/B]

Now Save As **clutterflow.sh**

Right click this file you just made and select Properties and then the Permissions tab and check the box.. Allow Executing file as Program..

Goto your Main Menu and then Preferences and then find the Application called Main Menu.

Once opened you will see your category tree.. There is one called Other, click it and on the right you will see the one called Open Folder

Select it and right click>properties or Click properties on the right hand side and you will see a box where you can edit the launcher.

Where is says command it currently says...

**nautilus --no-desktop %U**

Replace with this...

**sh /home/yourname/.gnome2/nautilus-scripts/clutterflow.sh**

Don't forget to replace **yourname** in the line above with whatever name you use on your machine!

Now press close and either click on a launcher you created or use the places menu or whatever you use..

**For single launchers** that only open 1 folder like Music or Videos etc.. just create a sh file called music.sh or videos.sh and use this instead.

[B]#!/bin/sh
nautilus /home/yourname/Music
sleep 1
xdotool key F4[/B]

Remember to change yourname to your machines and Music to whatever folder you want..

Then create the launcher and change the name to match your sh script..

**sh /home/yourname/.gnome2/nautilus-scripts/music.sh**

---

### Post by fatriff on 2011-05-18
**[COLOR="Red"][SIZE="4"]HELP!!![/SIZE][/COLOR]**

Also, when clutterflow opens, the display is always tiny.. I checked and it has a minimum size setting of 200x200 on launch..

With the xdotool we installed earlier, you can change the size of any window just by running a terminal command like this which I have been tinkering with in the sh file I made.

Adding this to the sh script resizes the nautilus window to 800 X 800 or any size you choose.

**xdotool search "nautilus" windowactivate windowsize %@ 800 800**

But I can't figure out how to select the clutterflow window within the nautilus window.. maybe somebody can?

But i'm having problems getting it to change the clutterflow window size as it's inside another window.. I just don't have the skills to do this.. If somebody would do this it would be great as the code can just be added to the sh file and that will be a complete solution to getting it to open at a default size the user chooses.

[http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)

---

### Post by fatriff on 2011-05-21
Anybody out there with any advice on how to get/set the default size of the display window of clutterview.. It's a 200x200 default I believe.. So where is this set?

Can anybody do this?

---

### Post by Uri_Herrera on 2011-06-13
In 11.04 the Clutterflow Icons are Corrupted what could it be?

---

### Post by jagrock on 2011-07-22
> **fatriff said:**
> Ok guys, The only way I am capable of thinking of how to do it. Took me all of 5 minutes once I figured out a way I could do it.


That is very good, but I'd would like to set the aperture size more higher when pressing F4, because the default set is to small... Is this possible?

I'm using ubuntu 11.04.

---

